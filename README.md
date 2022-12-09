# gsha
Get sha from recent git commits.</br>
Add this function to your ~/.bashrc
<pre>
gsha() {
    list=()
    while read -r sha    desc; do
       list+=(  "$sha" "$desc" )
    done  < <(git log --oneline -n${1:-20})
    dialog --output-fd 1        \
           --ok-label "Copy SHA" \
           --cancel-label "Exit"  \
           --menu "Select SHA to copy:" 0 0 0 "${list[@]}"
}
</pre>
Usage:
<pre>
sha="$(gsha)"
$ echo $sha
20799ef
</pre>

[![Twitter Follow](https://img.shields.io/twitter/follow/Vaniacer?style=social)](https://twitter.com/Vaniacer)
[![paypal](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://paypal.me/sshto?locale.x=en_US) <sup>Don't hold yourself, buy me a beer)</sup>

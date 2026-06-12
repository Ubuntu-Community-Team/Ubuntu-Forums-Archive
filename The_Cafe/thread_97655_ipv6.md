---
title: "ipv6"
date: 2005-12-01
forum: The Cafe
---

### Post by solarcontrol on 2005-12-01
Something I'd like to mention to devs: ipv6 should be off by default and  up to the user to toggle on.
This is because at this point some DSL providers dont support it (i.e. Earthlink) and ipv6 causes unusably long host resolution (Im talkin up to 2 minutes to load a web page).
It would run off any 1st time user - most of whom have no idea  how to disable ipv6 (or even what it is).

This should especially be the case for live cds since you cant disable it there even if you know how.

---

### Post by Kvark on 2005-12-01
It should auto detect. It can't be too hard to make it do something like "if(time_to_resolve > 10secs) {toggle_ipv6();}". Then it would switch to ipv4 if ipv6 is not supported and in the future when support for ipv4 is dropped it would just as easily switch back to ipv6.

---

### Post by arpunk on 2005-12-01
[QUOTE=Kvark]It should auto detect. It can't be too hard to make it do something like "if(time_to_resolve > 10secs) {toggle_ipv6();}". Then it would switch to ipv4 if ipv6 is not supported and in the future when support for ipv4 is dropped it would just as easily switch back to ipv6.[/QUOTE]
Yea, i agree with that, should it be more technical when detecting IPv6 (nice example thought :P) but it will improve surfing and internet usability by 50% when IPv6 is not used/enabled. New options in the *network settings* dialog would be pretty useful, probably gnome developers are working on that by now :P

---


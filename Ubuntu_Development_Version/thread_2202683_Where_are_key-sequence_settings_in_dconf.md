---
title: "Where are key-sequence settings in dconf?"
date: 2014-01-30
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2014-01-30
I was doing some testing for the new proposed 'gnome-tweak-tool' and I encountered an unrelated problem:

[https://bugs.launchpad.net/ubuntu-gnome/+bug/1266307/comments/6](https://bugs.launchpad.net/ubuntu-gnome/+bug/1266307/comments/6)

> 

Looks good here. In Ubuntu GNOME Trusty I tested the new build in the standard gnome shell, gnome classic, and flashback w/metacity sessions.

Then in Ubuntu I tested the new package in the standard Unity, flashback w/metacity, and flashback w/compiz sessions.

No problem at all but I suppose one could argue that 'gnome-tweak-tool' is not the optimal tool for tweaking Unity???

**I did encounter an unrelated problem while testing Unity - if the key sequence for killing X is changed then the logout button does not seem to respond properly.** There is no difference in which version of 'gnome-tweak-tool' is used to change that sequence though. I'll follow up on that ASAP.


So I've been poking around in dconf but can't find what I'm looking for :confused:

The plan is to install a fresh Ubuntu, then edit the key sequence for killing X w/o adding any packages to see if I can break the logout button :)

---

### Post by mc4man on 2014-01-30
The location of that 'option' has moved from org.gnome.libgnomekbd.keyboard options to - 
org.gnome.desktop.input-sources xkb-options
(- 'terminate:ctrl_alt_bksp'

While I haven't used in 14.04/unity, in 13.10 killing X in unity could produce some unexpected behavior when logging back in.
(nothing to do with breaking log out, more about running a root file browser in the session *after* killing X

So here I don't use 'kill x' though have returned ctrl+alt+delete to it's previous behavior of starting a log out instead of the opening system monitor nonsense.

---

### Post by kansasnoob on 2014-01-30
> **mc4man said:**
> The location of that 'option' has moved from org.gnome.libgnomekbd.keyboard options to - 
org.gnome.desktop.input-sources xkb-options
(- 'terminate:ctrl_alt_bksp'

While I haven't used in 14.04/unity, in 13.10 killing X in unity could produce some unexpected behavior when logging back in.
(nothing to do with breaking log out, more about running a root file browser in the session *after* killing X

So here I don't use 'kill x' though have returned ctrl+alt+delete to it's previous behavior of starting a log out instead of the opening system monitor nonsense.

Thanks, I'll poke around a bit and see what I can figure out :)

---


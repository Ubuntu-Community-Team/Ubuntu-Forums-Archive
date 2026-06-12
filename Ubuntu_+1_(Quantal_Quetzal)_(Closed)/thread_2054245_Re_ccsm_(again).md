---
title: "Re: ccsm (again)"
date: 2012-09-06
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mc4man on 2012-09-06
Atm it would be a very poor idea for users to do anything in ccsm > Preferences
The poor effects could range from unsetting most plugins if clicking on 'Reset to defaults' to considerably worse if switching profiles or Backends (why one would don't know but if an option exists...
[1047138]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1047138")

Edit this will reset the compiz plugins back to default supplied
```
dconf reset -f /org/compiz/
```

Another side effect of the current switch to gsettings is on new installs that use Classic (compiz) when logging in the first time the will be no plugins enabled, in that case they should be set thru ccsm as needed.
[1036752]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1036752")

---

### Post by ventrical on 2012-09-07
> **mc4man said:**
> Atm it would be a very poor idea for users to do anything in ccsm > Preferences
The poor effects could range from unsetting most plugins if clicking on 'Reset to defaults' to considerably worse if switching profiles or Backends (why one would don't know but if an option exists...
[1047138]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1047138")

Edit this will reset the compiz plugins back to default supplied
```
dconf reset -f /org/compiz/
```Another side effect of the current switch to gsettings is on new installs that use Classic (compiz) when logging in the first time the will be no plugins enabled, in that case they should be set thru ccsm as needed.
[1036752]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1036752")

Thanks for the heads up!

---


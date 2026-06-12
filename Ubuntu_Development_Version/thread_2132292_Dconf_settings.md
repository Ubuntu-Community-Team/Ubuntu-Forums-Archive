---
title: "Dconf settings ?"
date: 2013-04-04
forum: Ubuntu Development Version
---

### Post by dino99 on 2013-04-04
Was reading that blogpost : [http://www.mattfischer.com/blog/?p=431](http://www.mattfischer.com/blog/?p=431) and then checked my system.
What i've seen:
- the dconf-tool settings , for example : the chosen background, are not writen inside the user profile.
- worst, dconf use the wired default setting, as my "user" is not created by the configuration process.

So i wonder about how is your config settings about dconf : mainly /.config/dconf/ & /etc/dconf/profile/.
As profile, i only have "gdm", but not my login username.
But my system is an PP dist-upgrade, not a fresh install, so maybe a difference exist.

---

### Post by schragge on 2013-04-04
```
[COLOR=green]$[/color] lsb_release -idrc
[color=green]Distributor ID: Debian
Description:    Debian GNU/Linux 7.0 (wheezy)
Release:        7.0
Codename:       wheezy
$[/COLOR] ls ~/.config/dconf/
[color=green]user
$[/color] dconf dump /org/gnome/desktop/background/
[color=green][/]
color-shading-type='horizontal'
picture-options='zoom'
picture-uri='file:///usr/share/images/desktop-base/joy.xml'
primary-color='#0099cc'
secondary-color='#006699'[/color]
```

---

### Post by dino99 on 2013-04-05
hm, mine only have :  color-shading-type='horizontal'
even if dconf-tool shows all the other line entries

---


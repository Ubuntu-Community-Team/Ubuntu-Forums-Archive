---
title: "xubuntu 11.10 compiz emerald tutorial...working"
date: 2011-11-11
forum: Tutorials
---

### Post by Cresho on 2011-11-11
#sudo apt-get install compiz compiz-plugins-extra compiz-plugins-main compizconfig-settings-manager gnome-themes

[https://launchpad.net/~malteworld/+archive/compiz/+packages](https://launchpad.net/~malteworld/+archive/compiz/+packages)

install libemeraldengine and emerald.  both debs work on my 32bit system.  dont use the dev since you dont need it.

then

applications menu->settings->settings manager->session and startup->application autostart

make new "add" from bottom

1st

name:compiz
command: compiz --replace ccp



name:emerald
command: emerald --replace


under applications menu->settings->settings manager->session and startup->application, remove checkmark under "automatically save session on logout"
when you log out, be sure to remove "save sessions for future log ins" checkmark so
 it can boot up clean.

for a real clean boot, delete all files in your /usernmane/.cache/sessions so delete all files.  not necessery but it helps in some cases.

---


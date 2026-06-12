---
title: "GTK Inspector missing?"
date: 2016-03-21
forum: Ubuntu Development Version
---

### Post by vasa1 on 2016-03-21
I'm using a live USB of Lubuntu 16.04.

According to [https://wiki.gnome.org/Projects/GTK%2B/Inspector](https://wiki.gnome.org/Projects/GTK%2B/Inspector), one can run ```
gsettings set org.gtk.Settings.Debug enable-inspector-keybinding true
``` to activate GTKInspector but I get```
lubuntu@lubuntu:~$ gsettings set org.gtk.Settings.Debug enable-inspector-keybinding true
No such schema 'org.gtk.Settings.Debug'
lubuntu@lubuntu:~$ 
```

Is this because I'm using Lubuntu or does this fail on other Ubuntu flavors as well?

Looking at the comments to [this answer]("http://unix.stackexchange.com/a/242597"), it seems that this issue was present in Ubuntu GNOME 15.10 as well.

+++++++++++++++++

If I run ```
gsettings list-schemas | grep -i settings
```
all I get is:
```
org.gnome.settings-daemon.plugins.gdu-sd
org.gtk.Settings.FileChooser
org.blueman.gsmsettings
org.gtk.Settings.ColorChooser
lubuntu@lubuntu:~$
``` 
So I'm guessing that for whatever reason, GTKInspector won't be in Lubuntu 16.04 and possibly other flavors. But something is available if a gtk3 application is launched like this:
```
GTK_DEBUG=interactive application_name
```

But, according to this bug, ["No such schema 'org.gtk.Settings.Debug'" error upon trying to activate GTKInspector shortcuts]("https://bugs.launchpad.net/ubuntu-gnome/+bug/1523929"), users who want this need to install *libgtk-3-dev*.

---


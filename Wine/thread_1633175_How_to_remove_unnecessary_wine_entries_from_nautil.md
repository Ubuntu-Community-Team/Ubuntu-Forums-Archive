---
title: "How to remove unnecessary wine entries from nautilus openwith window"
date: 2010-11-28
forum: Wine
---

### Post by etdsbastar on 2010-11-28
Hello There,

I want to remove unnecessary entries from the nautilus open with window as shown in the attachment.

Please help.

---

### Post by Soulcage on 2010-11-29
I think the files you want are in ~/.local/share/applications the wine-extensions files.

---

### Post by etdsbastar on 2010-11-29
Thanks dear,

Your solution worked and i deleted all the wine entries from the ~/.local/share/applications folder, because wine has already been uninstalled from my system.

Thanks a lot again.

---

### Post by Soulcage on 2010-11-30
If you want to remove all the files that wine creates then run this whole command in a terminal.```
rm -rf $HOME/.wine && rm -f $HOME/.config/menus/applications-merged/wine* && rm -rf $HOME/.local/share/applications/wine && rm -f $HOME/.local/share/desktop-directories/wine* && rm -f $HOME/.local/share/icons/????_*.{xpm,png} && rm -f $HOME/.local/share/icons/*-x-wine-*.{xpm,png} && rm -f $HOME/.local/share/applications/wine-extension*
``` Copied most from [http://wiki.winehq.org/FAQ#head-8a17a13a8a4cda9e12e24a1ad4e1b1aaf043d581]("http://wiki.winehq.org/FAQ#head-8a17a13a8a4cda9e12e24a1ad4e1b1aaf043d581")

---


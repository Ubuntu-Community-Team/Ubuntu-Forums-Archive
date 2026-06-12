---
title: "(Fixed) Changing themes makes the desktop background disappear"
date: 2014-04-04
forum: Ubuntu Development Version
---

### Post by loukingjr on 2014-04-04
running Xubuntu 14.04 in VirtualBox and noticed switching themes causes the desktop wallpaper to disappear. I also can't use desktop settings to restore it until I restart Xubuntu.

edit: it also makes the panel disappear but if you click on where the icons are suppose to be, for instance the menu, it still functions.

---

### Post by slickymaster on 2014-04-04
I can confirm that. I'll file a bug for it in LP.

---

### Post by loukingjr on 2014-04-04
thanks

---

### Post by slickymaster on 2014-04-04
Update.

Not only there's already a bug on that, [Bug 1302101]("https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/1302101"), but also a upstream fix which hasn't yet landed, meaning that it will take some time until the fix lands in Trusty.

As a workaround, there's a patched xfdesktop available from [https://launchpad.net/~thad-fisch/+archive/test](https://launchpad.net/~thad-fisch/+archive/test)

---

### Post by loukingjr on 2014-04-04
thanks. I'll wait for the fix to show up in the Repos.

---


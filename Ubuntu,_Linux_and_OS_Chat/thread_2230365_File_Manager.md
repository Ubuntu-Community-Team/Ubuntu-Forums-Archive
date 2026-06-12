---
title: "File Manager ??"
date: 2014-06-18
forum: Ubuntu, Linux and OS Chat
---

### Post by ramakanta on 2014-06-18
What is the different between  nautilus , nemo and caja ?? why Linux mint uses caja in mate and nemo in cinnamon ??? why not use nautilus ???

---

### Post by tgalati4 on 2014-06-18
I use Linux Mint MATE and it uses caja which is a gnome2 nautilus clone.  The names have been changed to avoid conflict with the official nautilus version.  Try using each and you will see the differences.

> 
tgalati4@Mint14-Extensa ~ $ apt-cache depends caja
caja
  Depends: libatk1.0-0
  Depends: libc6
  Depends: libcairo2
  Depends: libcaja-extension
  Depends: libexempi3
  Depends: libexif12
  Depends: libgail18
  Depends: libgdk-pixbuf2.0-0
  Depends: libglib2.0-0
  Depends: libgtk2.0-0
  Depends: libice6
  Depends: libmateconf
  Depends: libmatedesktop
  Depends: libpango1.0-0
  Depends: libselinux1
  Depends: libsm6
  Depends: libunique-1.0-0
  Depends: libx11-6
  Depends: libxml2
  Depends: libxrender1
  Depends: shared-mime-info
    shared-mime-info:i386
  Depends: desktop-file-utils
  Depends: mate-vfs
  Depends: libglib2.0-data
  Depends: caja-common
  Suggests: ffmpegthumbnailer-caja
  Suggests: gstreamer0.10-tools
  Suggests: meld
  Suggests: engrampa
  Conflicts: caja:i386


---

### Post by LastDino on 2014-06-19
It's mostly dependent on user preferences. Nemo comes with more features, but is heavy and Nautilus and Caja are lighter file browsers. It usually doesn't even matter to most end users.

---

### Post by Bucky Ball on 2014-06-19
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by deadflowr on 2014-06-19
caja and nemo are both forks of nautilus.
caja is a fork of old nautilus, used in the gnome2 desktop.
nemo is a fork of a newer nautilus, used prior to 3.6(I *think*)

caja's fork has been explained in an earlier post, nemo's fork is because after nautilus version 3.4(again, I *think*), the nautilus developers started dropping beloved features like lead balloons. nemo is built to retain those lost features.

---

### Post by ramakanta on 2014-06-19
then what is the best one ??
in linux mint 17 if i have uninstall caja and load the nautilus,is any problem to system ???

---

### Post by LastDino on 2014-06-19
It will cause conflict, but you can manually change the default file manager from settings. I don't use MInt so I don't know ''step by step how to''. But, just an advice, stick with default Caja instead of replacing it with Nautilus.

---

### Post by tgalati4 on 2014-06-19
Don't uninstall caja.  See what the nautilus dependencies are for your system.  Nautilus may pull in a lot of unwanted libraries that could cause problems with your system.

```
apt-cache depends nautilus
apt-cache depends nautilus | grep Breaks
```

---


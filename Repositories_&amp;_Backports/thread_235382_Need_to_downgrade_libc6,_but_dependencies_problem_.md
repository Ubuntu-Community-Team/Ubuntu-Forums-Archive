---
title: "Need to downgrade libc6, but dependencies problem !!"
date: 2006-08-13
forum: Repositories &amp; Backports
---

### Post by mosaic on 2006-08-13
Hello,

I have upgraded libc6 to newer version from non-distribution package because I wanted to run AllTray.
But then I realised that it is not possible to install Evolution mail client or dix player, because it needs the older version of libc6!

I have tried to reinstall it (uninstall and install), but I got a lot of error messages saying that there are strong dependencies to probably all system packages and it is not possible to uninstall libc6.

I am lost at the moment, have no idea how to solve this situation.
Is it possible to downgrade this kind of essential package without system crash ? I need to get back the distribution version.

Could anybody help please ?

Thanks a lot.

mosaic

---

### Post by Dr. Nick on 2006-08-13
hopefully someone can be more specific, but i installed a debian version of libc6 and it totally trahsed it, it was fine untill reboot, then no apps would run.

If you look at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) you can probably find the libc6 that you need. then save the deb and try the various dpkg force installation methods which may help

---

### Post by mosaic on 2006-08-13
Hello Nick,

thanks for reply. But I have already tried to force install/ reinstall it, without success. it always says that newer version is already installed and the process aborts. somehow i need to downgrade the package without uninstallation.. I have found parameter --force-downgrade in dpkg man pages, but it is not recommended action untill I really know what I am doing.. and I am not sure what I would do :) so that's why I asked for help here.. 

thx

mosaic

---

### Post by Dr. Nick on 2006-08-13
What you can try is

Open synaptic, search libc6, click on the package and then go to the package menu on the toolbar and see if the "force version" option is avaible.

I have never used the --force-downgrade option. When I messed mine up it was by using a older version, so it installed the new (correct) version without issue

---


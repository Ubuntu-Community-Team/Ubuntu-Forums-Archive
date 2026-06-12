---
title: "results from today's update, upgrade, dist-upgrade"
date: 2013-04-11
forum: Ubuntu Development Version
---

### Post by pfeiffep on 2013-04-11
My daily normal practice is in the title. And information box popped up
> Data files for some packages could not be downloaded


The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.


flashplugin-installer


This is a permanent failure that leaves these packages unusable on your system.  You may need to fix your Internet connection, then remove and reinstall the packages to fix this problem. I did,however, leave the information box opened for the remainder of the process - possibly the warnings below were a result.


The process continued to other packages which seemingly invalidates the 'fix internet connection' - the remainder of the message is a bit ambiguous; I performed apt-get install flashplugin-installer which reported that I had the most recent. the process continued - during dist-upgrade I received this:
> Setting up modemmanager(0.6.0.0.really-0ubuntu5) ...
modemmanager start/running, process9227
Setting up software-center(5.6.0-0ubuntu2) ...
Updating software catalog...this maytake a moment.
INFO:softwarecenter.db.pkginfo_impl.aptcache:aptcache.open()




WARNING:softwarecenter.db.update:Thefile:'/usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser.desktop'could not be read correctly. The application associated with thisfile will not be included in the software catalog. Please considerraising a bug report for this issue with the maintainer of thatapplication


flashplugin-installer
WARNING:softwarecenter.db.update:Thefile: '/usr/share/app-install/desktop/workrave:workrave.desktop'could not be read correctly. The application associated with thisfile will not be included in the software catalog. Please considerraising a bug report for this issue with the maintainer of thatapplication




WARNING:softwarecenter.db.update:Thefile:'/usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser-layer.desktop'could not be read correctly. The application associated with thisfile will not be included in the software catalog. Please considerraising a bug report for this issue with the maintainer of thatapplication  

I spot checked the software center it opened and presented software packages.  My system appears 'normal' . Reissuing apt-get upgrade and dist-upgrade resulted in no warnings.

Anyone else have similar results?

---

### Post by grahammechanical on 2013-04-11
A few days ago I saw that message about sonicvisualizer. I saw it a few times. I did not get it today. I conclude that there is something wrong with the packaging of that application and it is not added to the software catalog.

Regards.

---


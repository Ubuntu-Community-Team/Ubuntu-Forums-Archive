---
title: "ubuntu won't recogniz raid scsi drives"
date: 2011-08-09
forum: Server Platforms
---

### Post by lister king of smeg on 2011-08-09
i have a old hp netserve i686 scsi raid server running novell netware that is needing to be decommissioned and re-purposed for file back ups. but when i popped in a ubuntu live cd to do a drive wipe ubuntu loaded but would not recognize that there were any hard-drives attached. thus i cannot do a reformat. also but non importantly the gui would not load i tried gnome and xfce. varients both. i also attempted to use system rescue live cd and neither would it see the harddrives or the gui load.

---

### Post by YesWeCan on 2011-08-09
Which type of Ubuntu live CD are you using?
It may be that the disks have Windows RAID metadata blocks on them and the installer is refusing to display them.
If you run these commands from live CD:
sudo apt-get install dmraid
sudo dmraid -s

any Windows RAID disks should be listed.

To delete the metadata blocks,
sudo dmraid -M -r /dev/sdx   (x=a,b,c...)


To reformat the disks in a linux RAID array you should use the alternate installer.

---

### Post by lister king of smeg on 2011-08-13
i tried xubuntu live cd and xubuntu alternate install disks how would i go about adding the package to the cd? also the sever is old enough that there is no usb port.

---

### Post by YesWeCan on 2011-08-13
> **lister king of smeg said:**
> i tried xubuntu live cd and xubuntu alternate install disks how would i go about adding the package to the cd? also the sever is old enough that there is no usb port.
I don't understand your question. When you have booted a live CD and then install a package it gets installed to your RAM. Obviously, this is volatile so if you reboot you have to install again.

---


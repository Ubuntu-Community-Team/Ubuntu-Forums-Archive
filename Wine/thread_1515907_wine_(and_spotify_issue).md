---
title: "wine (and spotify issue)"
date: 2010-06-23
forum: Wine
---

### Post by Lars_bylund on 2010-06-23
Hi, I have ubuntu installed (10.04) on one hd and windows xp on another. I downloaded Wine and got some programs running directly from the windows hd (photoshop 6, spotify aso) so I made a link to spotify (from the installation on the windows hd) and put it on the desktop, and it worked fine, until I re-started the computer! then the link 'broke'. why?

Must I reinstall the programs that are not working directly from the windows hd on the virtual 'c' drive in wine? It would be nice if I could run all of them of of the windows hd.

sometimes the windows hd are displayed on the ubuntu desktop on startup, sometimes not, however, I can always open it in 'places', if that mean anything.

---

### Post by nilarimogard on 2010-06-23
Because the NTFS partitions (on which Windows is installed) are not automatically mounted on startup, so after a restart the link is broken until you mount them (click on their icon in Nautilus). But you can set them to automatically mount on startup...

---

### Post by Lars_bylund on 2010-06-23
Thanks! but how do I mount it on startup? I tried to right click the hd>properties, but there were no mounting options... I tried to google it, but only found a guy who said:

> **hobo14 said:**
> I was changing some mount options for my external  hard disk, but instead of creating an entry for it in /etc/fstab I just  right-clicked on its icon, Properties > Volume > Settings, and  entered the options in the mount options box..............


as said, when i right klick on the hd, I only get properties.

the ubuntu help says:
'To add Disk Mounter to a panel, right-click on the panel, then choose
     Add to Panel.  Select Disk Mounter in the
     Add to the panel dialog, then click
     OK.'

Ok, but this only get me to the same properties!

please help!

Lars

---

### Post by TheStroj on 2010-06-23
I found an answer in 0.37s. 

[http://ubuntuforums.org/showthread.php?t=686042](http://ubuntuforums.org/showthread.php?t=686042)

---

### Post by nilarimogard on 2010-06-23
There's also a GUI for that: pysdm and even a [ntfs automount script]("http://www.webupd8.org/2010/04/ubuntu-script-to-automatically-mount.html")

---


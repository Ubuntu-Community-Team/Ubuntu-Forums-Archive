---
title: "Xubuntu 6.06/LTS Server with USB Hard Drive"
date: 2007-11-12
forum: Server Platforms
---

### Post by jamesr on 2007-11-12
Hi all,

I am having problems mounting a USB hard drive on my Archival server. The system is running Xubuntu 6.06 which has been regularly updated. I was hoping to keep the system running until the next LTS release. BUT Ii would like to add a USB hard drive so that the normal archival file area can be backed up regularly and then only once a month to CD or DVD.

The system is only a home server which is used as an Intranet server, running Apache.  Backup server for various Windows systems running Samba. Backup server for various Linux PCs. So it is relatively lightly loaded but I would prefer not to restart with 7.04 because of the support issues, and the current system is very stable and reliable.

I was able to solve the USB Hard Drive (on an independant system installing 7.04 and 7.10 solved the problem) so I seem to have several choices,

1) Upgrade to 7.04 or 7.10 by loading the upgrades from the internet. That should preserve all of my settings
2) Install 7.04 or 7.10 from CD and then add Apache, proFTP, access to my print server HUB, etc etc.
3)Hope that I can find a resolution to automounting of the USB Hard Drive.
4) add SCSI hard drives to the system but the server is long in the tooth and buying  suitable SCSI hard drives could be interesting and relatively costly.
5) Install the server CD and then add xubuntu-desktop.

Comments please.

---

### Post by jcbgrady on 2007-11-15
I am experiencing the same problem. The external USB drive is recognized but will not automount. My fstab is correct because when I run the mount -a command it mounts the drive as intended. It just will not do this automatically after a restart.

I am also wondering if a fresh install to Feisty will be worth it or if this problem will be present in that installation as well...

---


---
title: "[Debian 8]HDDs not seen after editing mount options to mount on startup, gnome-disks"
date: 2016-02-15
forum: Ubuntu/Debian BASED
---

### Post by feckinegit on 2016-02-15
I wanted want my two other hard drives (one HDD with windows 10, all partitions on HDDs are NTFS) to automount on system startup. In gnome-disks I edited the mount options to mount on startup the 2 drives (before doing this there was no issue with the HDD, I just had to manually mount them). Now my HDDs are not being recognized on the system at all and my windows 10 will not boot. Gparted, gnome-disks or kde partition manager will not see the HDDs. on boot I getting "SRST failed (errno=-16)" for the two HDDs. Fstab does not see the two HDDs. Ubuntu live cd or boot-repair does not see the HDDs. Hirens boot cd with mini XP does see them and lets me access all the files, I rebuilt MBR but still Linux does not see the HDDs. I have no issue with other USB HDDs which are NTFS just the two drives I set to mount at start up in gnome-disks. Is there any file I can edit to undo the mount on startup or what can I do to fix this.

---

### Post by feckinegit on 2016-02-16
I fixed the issue. Not the way I'd have liked to have fixed it, I would have liked to have been able to fix it inside Debian. For anyone else with similar issue I booted into mini XP in Hirens boot cd, in my computer I right clicked on the drive and choose reset NTFS permissions on the the HDDs. Everything working fine, no mount on startup but not the end of the world.

---


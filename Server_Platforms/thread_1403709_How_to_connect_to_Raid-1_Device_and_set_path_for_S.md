---
title: "How to connect to Raid-1 Device and set path for Samba"
date: 2010-02-10
forum: Server Platforms
---

### Post by Bauer17 on 2010-02-10
I currently have 3 drives installed to be used as a file server.  
1 holds the Ubuntu OS
The other is the file server drive with 1 additional for backup using raid1.

2 Questions:
1) How do I get to the drive or Raid device to put files on the drive using command line (the 2 drives are sda & sdc that are connected to the raid1 device)?

2) How do I set the path in Samba to connect to this RAID drive.

Thanks!

---

### Post by buntunoob on 2010-02-11
1. To get the Raid going its mdadm - [[COLOR=red]https://help.ubuntu.com/community/Installation/RAID1%2BLVM[/COLOR]]("https://help.ubuntu.com/community/Installation/RAID1%2BLVM") this guide looked good, but im not so sure about the fstab part( [[COLOR=red]http://mesanna.com/2009/02/02/how-to-mount-a-partition-automatically-in-ubuntu-linux/[/COLOR]]("http://mesanna.com/2009/02/02/how-to-mount-a-partition-automatically-in-ubuntu-linux/"))
 
2. For the samba part [[COLOR=red]http://ubuntuforums.org/showthread.php?t=202605[/COLOR]]("http://ubuntuforums.org/showthread.php?t=202605")

---


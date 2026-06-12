---
title: "What does this rkhunter log mean?"
date: 2012-02-06
forum: Security
---

### Post by zozza on 2012-02-06
I recently ran rkhunter.  All was OK except for:

Warning: The file properties have changed:
[21:32:42]          File: /usr/bin/last
[21:32:42]          Current inode: 4107521    Stored inode: 4104859
[21:32:42]          Current file modification time: 1327053783 (20-Jan-2012 10:03:03)
[21:32:42]          Stored file modification time : 1307648771 (09-Jun-2011 20:46:11)

 Warning: The file properties have changed:
[21:32:58]          File: /sbin/sulogin
[21:32:58]          Current inode: 491633    Stored inode: 491669
[21:32:58]          Current file modification time: 1327053783 (20-Jan-2012 10:03:03)
[21:32:58]          Stored file modification time : 1307648771 (09-Jun-2011 20:46:11)

I am wondering why this is an issue.  I cannot recall doing anything specifically on 20 January.  What does this mean?

I don't think these hidden files on pulse-shm data are problems:  [http://ubuntuforums.org/showthread.php?p=4908163](http://ubuntuforums.org/showthread.php?p=4908163)

 Warning: Suspicious file types found in /dev:
[21:35:02]          /dev/shm/pulse-shm-54487743: data
[21:35:03]          /dev/shm/pulse-shm-1701410113: data
[21:35:03]          /dev/shm/pulse-shm-2092259488: data
[21:35:03]          /dev/shm/pulse-shm-1005169831: data
[21:35:03]   Checking for hidden files and directories       [ Warning ]
[21:35:03] Warning: Hidden directory found: /etc/.java
[21:35:03] Warning: Hidden directory found: /dev/.udev
[21:35:03] Warning: Hidden directory found: /dev/.initramfs
[21:35:03] Warning: Hidden file found: /dev/.blkid.tab: ASCII text
[21:35:04] Warning: Hidden file found: /dev/.blkid.tab.old: ASCII text

Thanks!

---

### Post by Buckie_Bhoy on 2012-02-06
I had similar warnings around file properties have changed [posted about same time as you LOL].
 
I found an article via google which suggested it may have been to do with some upgrades/updates, and suggested running sudo rkhunter --propupd
 
I ran this then ran rkhunter again, and this time no issues with warnings regarding file properties

---

### Post by Buckie_Bhoy on 2012-02-06
Please see advice given by Dangertux in my thread regarding --propupd

---


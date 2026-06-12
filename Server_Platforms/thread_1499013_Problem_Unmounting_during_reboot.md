---
title: "Problem Unmounting during reboot"
date: 2010-06-01
forum: Server Platforms
---

### Post by terazen on 2010-06-01
I just built a 32bit lucid server and connected it to a pre-existing san lun and everything works fine.  It's got /dev/sdb as a 100gb ext3 drive mounted to /iscsi.  The problem is whenever I reboot the server it never even shuts down.  The system seems to hang after trying to unmount.

This is the last thing I see on the monitor (Sorry it's not cut and pasted.  I took a picture of it with my cell phone.)

Deconfiguring network interfaces
Deactivating swap
Unmounting weak filesystems
Unmounting local filesystems
connection1:0 ping timeout of 5 seconds expired
INFO: task flush-8:16:540 blocked for more than 120 seconds
"echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disable message
INFO: task umount:1450 blocked for more than 120 seconds
"echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disable message

I waited for a few hours to see if it was just super slow, but no luck.  Does anyone have any ideas?  I thought about formatting ext4, but wanted to check here to see if anyone has seen this before.

---

### Post by terazen on 2010-06-01
[https://bugs.launchpad.net/ubuntu/+source/open-iscsi/+bug/567143](https://bugs.launchpad.net/ubuntu/+source/open-iscsi/+bug/567143)

I added the mkdir line into my /etc/init.d/open-iscsi file and everything is working as expected again!  Now to get the ssh keys sorted out so I can move the backups over to the new server. :-)

---


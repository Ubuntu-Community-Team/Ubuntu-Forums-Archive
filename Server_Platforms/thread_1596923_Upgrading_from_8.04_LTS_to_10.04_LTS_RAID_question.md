---
title: "Upgrading from 8.04 LTS to 10.04 LTS RAID question"
date: 2010-10-14
forum: Server Platforms
---

### Post by sauce345 on 2010-10-14
Hello,

I currently have a Ubuntu 8.04 LTS box set up in Raid 5 with five 1 terabyte drives in it and 1 80 gigabyte system drive on it. The raid array and file system are not on the same drive.  I used mdam to set the software raid a while back and I want to upgrade to the latest LTS.

My question is do I just have to remount my /dev/md0 by sticking it in the /etc/fstab so as it will mount automatically on startup or is their anything special I need to do to the array in order for it to be recognized by the OS.  I assume this process will be very easy but just wanted to make sure I don't screw it since I have a lot of information stored on the array.

Thanks.

---

### Post by jbrown96 on 2010-10-14
It will either auto-detect or you can force a detect with the following:

From the mdadm manpage ```
mdadm --assemble --scan md-devices-and-options...
``` Note that your device names may change on a reinstall, but it shouldn't affect the array.

I recently re-installed Fedora, and I had literally no issues with my array. It was even named the same, /dev/md127. 

If you can, boot from a live CD, then you should be able to tell if the array will be auto-detected.

---

### Post by sauce345 on 2010-11-04
Sorry for the delayed response...finally got around to doing it and it worked just fine.  Now I have to just reconfigure all my samba and LAMP services the way I want and I will be to 100% operational.

Thanks for tips!!

---


---
title: "Kernel upgrade to 2.6.24-23-server broke RAID"
date: 2009-01-14
forum: Server Platforms
---

### Post by cooperised on 2009-01-14
Hi all,

I've got a server here at work (Hardy) with three hard drives, two of which are in a RAID 1 array using software RAID (mdadm etc).  After upgrading to 2.6.24-23-server kernel, RAID broke spectacularly - it appeared to be attempting to associate the wrong discs with the array.  Booting using the 2.6.24-22-server kernel fixes it, so for now that's what I'm doing.

Anyone else had similar problems?  I can boot to the new kernel and collect more specific information if it'll help, though I'll need to know what to grab.  I'd also like to file a bug report, but it'll only be any use if I can find out what's causing this.

Thanks!

---

### Post by freerkkalsbeek on 2009-01-14
I've had the same problem several times after upgrading kernels.

Last time I fixed it by creating a new mdadm.conf file with the script /usr/share/mdadm/mkconf

Recipe:
- Boot using the working kernel
- Check if array(s) are working correct (cat /proc/mdstat)
- Backup /etc/mdadm/mdadm.conf
- Create new config /usr/share/mdadm/mkconf
- Copy newly created conf to /etc/mdadm/mdadm.conf

Reboot.

Hope it works for you.

---

### Post by fjgaude on 2009-01-14
I've been using the same arrays for over two-years of kernel updates, moves to other machines, etc. Here's what has always worked for me: remove **mdadm** using apt-get, re-name or delete the **/etc/mdadm/mdadm.conf** file, reboot. Then re-install mdadm and run this command:

```
sudo mdadm --assemble --scan
```

A new mdadm.conf file is created automatically and everything works as before, correctly. Remember mdadm assembles arrays through the use of the special UUID that is placed on each drive of an array. Each disk has the same UUID and from header info can assemble correctly.

Let us know how you are doing.

---

### Post by leibniz1 on 2009-02-10
I recently had a similar experience when upgrading to that kernel version.

However, in my case, instead of just fudging the mdadm configuration or the menu.lst, the upgrade actually** removed the partitions on my hard drives!**

Yes, I was quite surprised.   I had two SATA drives (sdc and sdd) set up with RAID1 using mdadm.  Each drive had three partitions so I had md1 md2 and md3.

Upgraded the kernel, and this is all I saw when looking at the drives:
```

root@X2:/etc# fdisk -l /dev/sdd

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table
root@X2:/etc#

```

Since my partitions have disappeared, I assume that my VG and LVs that I had sitting on top of them are also gone for good.  :(

The whole reason for RAID is stability and redundancy.  If the kernel upgrade is going to simply remove my ['linux raid autodetect' type] partitions, then that defeats the purpose of using it in the first place,

I don't know if this is a specific kernel bug with this version (though I've read about the software raid bugs with this version) or just a freak happenstance, but what it has done is make me rethink using linux software RAID at all.   I'd rather go back to simple disk partitions and just rsync them on a daily basis with a cron script, than to always wonder if I'm going to lose everything when I upgrade my kernel.

Then again, I could simply never upgrade the kernel.  But that's not the solution either.

I would be very curious to know if anyone else has seen or experienced this.


Thanks
Bill

---

### Post by leibniz1 on 2009-02-18
Well, I have still not found out the root cause of why this happened.

I need to move ahead with a plan, so I guess I will play it safe, and recreate everything, and then just remove / readd mdadm when doing a kernel update. (backing up mdadm.conf of course)

If anyone has found a reason for these bugs and kernel update partition trashings, please post.

Thanks.
Bill

---


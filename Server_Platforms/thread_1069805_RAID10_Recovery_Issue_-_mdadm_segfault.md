---
title: "RAID10 Recovery Issue - mdadm segfault"
date: 2009-02-14
forum: Server Platforms
---

### Post by marc2112 on 2009-02-14
Hi folks,

I have a 4 disk software RAID10 that's not doing too well.  2 of 4 disks lost power and are flagged as "faulty removed".  Now that the power is restored, I feel like there should be a way to force the array back together but all the usual commands aren't working.

Here you can see the output of the commands I ran.  Any thoughts on how to recover?

[http://pastebin.com/m1dedbbac](http://pastebin.com/m1dedbbac)

Thanks!
---Marc

---

### Post by marc2112 on 2009-02-14
Added output of fdisk -l to pastebin: [http://pastebin.com/m39890121](http://pastebin.com/m39890121)

---

### Post by fjgaude on 2009-02-14
Hard to say what is going on with your raid10 array. Seems that sdd6 and sde6 have issues.

One thing you could try is using **mdadm** to fault and remove each partition, then zero their superblocks and then add the two partitions back into the array.

I guess you don't have backups for important data that's on these partitions, eh?

Read the **man** pages regarding my suggestion.

Let us know what you decide and the results, thanks.

---

### Post by marc2112 on 2009-02-15
Finally got this to work!  The mdadm command I had issued originally to force assemble which was producing a segfault works with the 2.6.8 version of mdadm (2.6.7 is shipped with xubuntu 8.10)

root@mclovin:~# /usr/src/mdadm-2.6.8/mdadm --assemble --force /dev/md0 /dev/sd[bcde]6
mdadm: forcing event count in /dev/sdd6(2) from 12547691 upto 12551546
mdadm: forcing event count in /dev/sde6(3) from 12547691 upto 12551546
mdadm: clearing FAULTY flag for device 2 in /dev/md0 for /dev/sdd6
mdadm: clearing FAULTY flag for device 3 in /dev/md0 for /dev/sde6
mdadm: /dev/md0 has been started with 4 drives.


---Marc

---

### Post by fjgaude on 2009-02-15
Interesting... anyway, happy you have the array up again.

---


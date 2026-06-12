---
title: "Booting Blocked by Degraded RAID"
date: 2011-11-01
forum: Server Platforms
---

### Post by wukey on 2011-11-01
Hi Guys

Re: Ubuntu Server 11.10 x64

I have 1x80GB HDD, which the system has been installed on, its the first disk. I also have 5x1TB HDDs that form a RAID5 software RAID.

The system stops at boot due to a "degraded RAID". I've been trying for hours to get the system to ignore the degraded RAID and just boot off the boot drive but it won't. While that array is degraded it won't go anywhere.

When you do try to tell it to boot degraded it complains that it only has 2/5 drives and stops anyway.

I have marks on my head from banging it against the wall. PLEASE HELP. :confused:

---

### Post by darkod on 2011-11-02
1. Sorry for the stupid question: Are you sure you have software raid? I was under the impression that with the OS on separate disk you could boot even with all disks of the raid gone. Of course there will be error messages but it should boot at least. This is not a motherboard BIOS raid, right?

2. Is the message that only 2 disks out of 5 are OK correct? Did 3 disks fail at once? RAID5 can only handle one failed disk which you should replace and let the array sync. If there are really 3 failed disks, the restore of your data is much more important than whether you can boot with the OS disk.

In worst case you can boot with the Desktop CD in live mode. You can even add disks and sync the array working from the live CD. But I'm not sure how it would work with more than 1 disk failed.

---

### Post by darkod on 2011-11-02
One thing that could prevent it booting with failed disks, is depending how you have grub set up. If it works with UUID you should be fine even if the disk /dev/sdX label changes.
But if grub works with /dev/sdX and the letter changes, grub is not looking at the right place for the kernel to boot it.
Also make sure in BIOS you are booting from the right disk.

---

### Post by daniel.pool on 2011-11-02
Hi,

On the off chance that you are having the same issue I had, Ubuntu was halting the boot as it was unable to mount the raid array defined in my fstab. For some reason I wasn't getting the standard error message which tells you this and allows you to press 'S' for skip or 'M' to enter a cli to fix. I just had a blank screen (having plugged a monitor into the server as it normally runs headless - I think this is because my server is built on old parts and has a built in nVidia card so I don't get a splash screen because of problems with the drivers ... don't ask why there is a splash, think its something to do with installing myth :(). I pressed 's' to skip mounting on the blank screen and was able to continue booting.

~Dan

---

### Post by mcarey on 2011-11-06
Hello all, 
  this might be the solution you are looking for:

[http://ubuntuforums.org/showpost.php?p=11388915&postcount=18](http://ubuntuforums.org/showpost.php?p=11388915&postcount=18)

  -Mark.

---


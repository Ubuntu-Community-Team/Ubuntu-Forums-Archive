---
title: "Backing Up &amp; Restoring Linux Partition"
date: 2005-05-04
forum: The Cafe
---

### Post by jodef on 2005-05-04
This question doesn't pertain to Ubuntu specifically :

I have a linux distro on a partition /dev/hda1 and I created an image using partimage, I want to restore and test that image so I restore to /dev/hda2. What adjustments would I now have to make to boot the version on /dev/hda2?

I adjusted lilo and pointed root to the correct /dev/hda2 but when booted and I do df -h it still shows /dev/hda1.

Anyone with any experience doing this or even alternative methods to backing up and restoring partitions?

---

### Post by nad on 2005-05-04
Did you modify /etc/fstab also? It seems that / is still pointed at /dev/hda1.

Partimage is a fine method of preservation. Your test is faulty. You need to duplicate conditions in order to perform this test. Switch hard drives and retest.

---

### Post by jodef on 2005-05-04
[QUOTE=nad]Did you modify /etc/fstab also? It seems that / is still pointed at /dev/hda1.

Partimage is a fine method of preservation. Your test is faulty. You need to duplicate conditions in order to perform this test. Switch hard drives and retest.[/QUOTE]
I didn't change /etc/fstab will try that.

I may not have been clear what I am really doing is creating a second install just as a back up, duplicating conditions not a necessity.

Thanks for you help.

---

### Post by jerome bettis on 2005-05-04
one thing about using something like partimage is that the partition you restore to can not be any smaller than the original one.  so if you need to do this, just make a tarball instead.

hopefully that helps you avoid learning the hard way (after you already deleted everything!) like i did!  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)

---

### Post by Xian on 2005-05-04
[QUOTE=jodef]What adjustments would I now have to make to boot the version on /dev/hda2?[/QUOTE]
The only thing you need to adjust is the bootloader config to reflect the added partition that contains the kernel, and the fstab files in both the old and new partition.

---

### Post by jodef on 2005-05-05
> Did you modify /etc/fstab also? It seems that / is still pointed at /dev/hda1. 
Thanks Nad that did the trick.
> one thing about using something like partimage is that the partition you restore to can not be any smaller than the original one. so if you need to do this, just make a tarball instead. Realised this only half way into the process but I had some extra free space on my drive so I created a large partition restored image and then resized it. O:) 
> The only thing you need to adjust is the bootloader config to reflect the added partition that contains the kernel, and the fstab files in both the old and new partition. Yes that resulted in a bootable image.

Thanks all for your assistance.

---


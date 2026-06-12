---
title: "Cant rezise extended partition"
date: 2017-11-26
forum: Ubuntu/Debian BASED
---

### Post by el3ctr0wqw on 2017-11-26
okay, so i searched everywhere about this problem which is  i cant add any space or rezise the extended partition of my kali linux os as you can see in the image ... i just tried a lot cant find any solution so please i would appreciate any help or explanation if any information is needed i will answer asap .. thanks

---

### Post by howefield on 2017-11-26
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by ajgreeny on 2017-11-26
That screenshot is showing that sda5 with then padlock icon is still probably mounted, so try right clicking on that and choosing unmount, and you may also need to right click on the swap partition, sda6 and choose swapoff before you can do anything to sda4, the extended partition.

Is this all being done from a live system?

I assume you realise that you can not do anything to your OS from an installed version of gparted on that OS as you can not unmount your running OS partitions and all partitions to be edited must be unmounted.

---

### Post by yancek on 2017-11-26
I expect you will have problems with this as you generally need contiguous space to expand to.  In your output, you show a 260GB ntfs partition between your Kali install and all the unallocated space.

---

### Post by el3ctr0wqw on 2017-11-26
> **ajgreeny said:**
> That screenshot is showing that sda5 with then  padlock icon is still probably mounted, so try right clicking on that  and choosing unmount, and you may also need to right click on the swap  partition, sda6 and choose swapoff before you can do anything to sda4,  the extended partition.

Is this all being done from a live system?

I assume you realise that you can not do anything to your OS from an  installed version of gparted on that OS as you can not unmount your  running OS partitions and all partitions to be edited must be  unmounted.





Yes , i tried gparted on live system (from usb) and i still couldnt get the resize/move option to appear

---

### Post by el3ctr0wqw on 2017-11-26
> **yancek said:**
> I expect you will have problems with this as you generally need contiguous space to expand to.  In your output, you show a 260GB ntfs partition between your Kali install and all the unallocated space.

so what do u suggest is there any possible solution?

---

### Post by Dennis N on 2017-11-26
Instead of expanding any partitions, you could just create a new partition in the 35 GB space and mount it in the Kali OS (which I assume is on sda5).

---

### Post by yancek on 2017-11-26
I'd agree with creating a new partition or new partitions.  You have 25GB of unallocated space at the beginning of the drive, another large ext4 partition and then 35GB of unallocated space.  We don't know what is on the second ext4 partition, you could probably combine them all but we don't know what you want.  Or you could simply create a new partition or new partitions from the 2 unallocated areas.  Not knowing what purpose the ext4 sda2 partition serves it is difficult to make any suggestion.

Are you using Kali to study computer forensics?  There is no other purpose to using it and it makes a terrible Desktop distribution as pointed out at their site.

---

### Post by el3ctr0wqw on 2017-11-28
allright guys thanks for helping, i got over this by moving the large files(basically virtualbox images) into a new created partition as Dennis suggested so yeah thanks again for your replies <3

---


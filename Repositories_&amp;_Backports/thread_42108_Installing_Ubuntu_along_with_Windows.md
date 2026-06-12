---
title: "Installing Ubuntu along with Windows"
date: 2005-06-16
forum: Repositories &amp; Backports
---

### Post by interaktiv on 2005-06-16
Hi

I have shipped two CDs from Ubuntu. One is installation disk, one is live CD. Documentation on installation disk says that it will destroy all existing data on my PC. (I don't want this :))) How may I install ubuntu and do not destroy windows?

I would like to select what OS will load on startup.
Thank you for replies,

regards,
interaktiv

---

### Post by defkewl on 2005-06-16
Data will be destroyed if you install Linux on partition where the data resides. First you have to spare a partition for your Linux to install. You can do this visually with Partition Magic from Windows. Format those partition as ext3 with PM. After that boot the Ubuntu instalation CD and install Ubuntu on those new partition you've just created. 

Good luck

---

### Post by interaktiv on 2005-06-16
[QUOTE=defkewl]After that boot the Ubuntu instalation CD and install Ubuntu on those new partition you've just created. 
[/QUOTE]

What about boot manager? Ubuntu will install some boot manager by itself?

Thank you for reply

---

### Post by interaktiv on 2005-06-16
[QUOTE=defkewl]First you have to spare a partition for your Linux to install. You can do this visually with Partition Magic from Windows.
[/QUOTE]

Do I need to create a partition for a swap? What size?

Thanks

---

### Post by defkewl on 2005-06-16
Yes, by default Ubuntu will install Grub for its Boot manager.

---

### Post by defkewl on 2005-06-16
Oops I forgot to tell you to install swap partition. :D Usually the size is 2 * Physical Memory size. Say if you have 512 RAM then your swap is recommended to have a size around 1GB. But this recommendation is not always right.

---

### Post by interaktiv on 2005-06-16
Swap partition filesystem is ex3, too?

---

### Post by davahmet on 2005-06-16
[QUOTE=interaktiv]Swap partition filesystem is ex3, too?[/QUOTE]
 No.  When you identify the partition as a swap, the installer will set the filesystem type as 'swap.'

---

### Post by defkewl on 2005-06-16
Nope. swap

---

### Post by interaktiv on 2005-06-17
Thank you
All works great.

---


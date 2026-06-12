---
title: "EasyBCD 1.6 Released!"
date: 2007-05-09
forum: The Cafe
---

### Post by Computer Guru on 2007-05-09
**A new version of EasyBCD, the popular Windows Vista dual-boot manager, has been released! It features improvments to the OS X dual-boot layer, and rewritten Linux/BSD support for greater compatibility. EasyBCD is a free (and small) must-have utility for any serious dual-booter.**

EasyBCD 1.6 has many bugfixes and new features - and it comes that much closer to making dual-booting a walk in the park. Some of the new features include a Diagnostics and Repair Center from where you can reset the Vista bootloader and accompanying BCD data & repair OS X partitions after a Windows install, rewritten Linux/BSD boot support that includes full LBA-detection and compatability, listing of drives by letter and partition (size, location, and format) to make figuring out which drive to use easier, improved memory usage, x64 driver disabling that works, and a new error handler class.

[EasyBCD 1.6 Released]("http://neosmart.net/blog/2007/easybcd-16-released/")
[Download EasyBCD 1.6]("http://neosmart.net/dl.php?id=1") | 721KB (Freeware)
[Screenshots]("http://neosmart.net/gallery/v/neosmart/EasyBCD/1_60/")

EasyBCD 1.6 was tested with Ubuntu Feisty every step of the way, and is guaranteed to work :)

---

### Post by Quillz on 2007-05-09
Do I install Feisty Fawn like usual, then go back into Vista and set up EasyBCD? Or do I have to use EasyBCD first and tell it the location of the future Feisty Fawn partition?

---

### Post by Computer Guru on 2007-05-09
You would install Feisty like usual, but ask it to install grub to the partition of Ubuntu instead of the drive.

Then boot into Vista, and add Ubuntu with EasyBCD.

Here's the detailed documentation: [http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

Cheers!

---

### Post by Quillz on 2007-05-09
> **Computer Guru said:**
> You would install Feisty like usual, but ask it to install grub to the partition of Ubuntu instead of the drive.

Then boot into Vista, and add Ubuntu with EasyBCD.

Here's the detailed documentation: [http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

Cheers!
Alright, thanks, I'll like into all this. At least I know it will work with 7.04.

---


---
title: "Daily build don't work for me"
date: 2012-06-03
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by novatillasku on 2012-06-03
I try every day with an USB and installer crashed.

I created with Startup Disk Creator in Maverick which ever work fine.

Just crashed when slideshow start.Today created a DVD and crash too ;-(

(quantal-desktop-i386.iso)

---

### Post by jerrylamos on 2012-06-03
Check my thread:

Quantal Startup Disk Creator made defective USB image

in this forum.  Sounds very similar to your experience, and the fix is the same, don't use quantal's startup disk creator.  Precise, Maverick, even Unetbootin work.

Jerry

---

### Post by sammiev on 2012-06-03
> **jerrylamos said:**
> Check my thread:

Quantal Startup Disk Creator made defective USB image

in this forum.  Sounds very similar to your experience, and the fix is the same, don't use quantal's startup disk creator.  Precise, Maverick, even Unetbootin work.

Jerry

I created my USB QQ boot using Precise and I crashed.

---

### Post by jerrylamos on 2012-06-03
> **sammiev said:**
> I created my USB QQ boot using Precise and I crashed.

What hardware are you using?  I've got Acer Aspire 1 netbook, Acer Aspire 5253 wide screen notebook, Compaq Presario tower Celeron 3.33 GHz.  All three installed from USB flash with varying amounts of pre-Alpha problems.

I also have an IBM Thinkpad T40 which with Intel Pentium M does not support generic-pae and quantal does not have a plain generic version that I've found.  cat /proc/cpuinfo lists the flags such as pae.  It's running precise lubuntu and slitaz linux, the latter for wireless support on the T40.

Jerry

---

### Post by wilee-nilee on 2012-06-03
Has worked with unetbootin for me several loads.

---

### Post by sammiev on 2012-06-03
> **jerrylamos said:**
> What hardware are you using?  I've got Acer Aspire 1 netbook, Acer Aspire 5253 wide screen notebook, Compaq Presario tower Celeron 3.33 GHz.  All three installed from USB flash with varying amounts of pre-Alpha problems.

I also have an IBM Thinkpad T40 which with Intel Pentium M does not support generic-pae and quantal does not have a plain generic version that I've found.  cat /proc/cpuinfo lists the flags such as pae.  It's running precise lubuntu and slitaz linux, the latter for wireless support on the T40.

Jerry

Toshiba L650 i5 Intel based. Will try it again tomorrow with the latest build but I will try a DVD. Used the Toshiba L500 and L650 for a few years now and never ran into this.

---

### Post by novatillasku on 2012-06-04
Thank's for your help, i try with Unetbootin and also in other computer, is possible my laptop is the problem.:)

---

### Post by pal1965 on 2012-06-04
try this:

[http://superuser.com/questions/265395/make-pendrive-bootable-via-command-line-ubuntu](http://superuser.com/questions/265395/make-pendrive-bootable-via-command-line-ubuntu)

---

### Post by jerrylamos on 2012-06-04
The primitive (!) linux commands still work.  Here's how as extracted from [http://ubuntuforums.org/showthread.php?t=1783752&highlight=Hybrid](http://ubuntuforums.org/showthread.php?t=1783752&highlight=Hybrid)
put the pen drive in a USB port
sudo apt-get install gparted
sudo gparted
search top right corner pull downs for your pen drive
likely have to umount it
delete all partitions
format to F32
don't do anything else to the pen drive
close gparted
make sure the pen drive is mounted,
df
to see what it is called in this example /dev/sdb
```

sudo dd if=quantal-desktop-i386.iso of=/dev/sdb oflag=direct bs=1048576
sync
```
That runs a lot faster than the bare dd command without the bs=1048576
The "sync" closes the pen drive to make sure the last dd was written.
Then try rebooting.

I usually prefer testing the quantal preferred method, but haven't gotten anywhere on writing a bug for the defective startup disk creator.

I'm also having fun with unetbootin because I can put an initial partition for the .iso of say 1 GB, add another ext2 partition labelled casper-rw in case when booting I add "persistent" to the linux line, another partition yet for storing some archive, ... used to be ubuntu could do the same thing but that function got deleted.

Pen drives are pretty big these days to waste the whole thing on a "starup disk" like the ubuntu application does.

Have fun, 

Jerry

---


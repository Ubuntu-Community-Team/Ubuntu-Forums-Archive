---
title: "Startup disk creator 4 GB + Partition support"
date: 2012-08-13
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Savio2010 on 2012-08-13
Add support to Startup disk creator to create 4 GB + Casper-RW Partitions.

An option in Startup Disk Creator to create casper-rw file or Casper-rw partion size above 4 GB in size.

Since now a days we find pen drives in big sizes.

What are your views?
I may link this thread to brainstorm later.....

---

### Post by sanderj on 2012-08-14
Yes, that would be very useful.

I don't know why the limit is at 4GB right now. Maybe it has to do that the stick is formatted with FAT (right?), which has a max file size?

Anyway: any solution that would make bigger sticks fully usable would be great.

---

### Post by pressureman on 2012-08-14
The max file size on FAT32 volumes is 2^32 - 1 bytes (4 GiB), and since the casper-rw is just a loopback filesystem, it is constrained by the file size limits of FAT32.

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent/](https://wiki.ubuntu.com/LiveUsbPendrivePersistent/) describes how to instead create an ext3/ext4 casper-rw *partition*, if you have a USB stick larger than 4GB.

---

### Post by Savio2010 on 2012-08-14
I had got this idea from TAILS. One of TOR Projects.

It has a build in 'Tails USB installer' which installs Tails to an empty USB drive and re-partitioning it creating an encrypted persistent partition.

See : [https://tails.boum.org/doc/first_steps/usb_installation/index.en.html](https://tails.boum.org/doc/first_steps/usb_installation/index.en.html)

---

### Post by ronacc on 2012-08-14
I do NOT want  the persistence file to default to ON . It should be an option that you have to enable not the other way around.

---

### Post by C.S.Cameron on 2012-08-14
Boot Live CD.
Plug in flash drive.
Start Partition Editor
Create 1 GB FAT32 partition, (on the left side of the bar). (size is optional)
Create a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw". (ext2 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, run "gksu nautilus"
Select disk / syslinux / text.cfg and add "persistent" as shown below:
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
Shutdown, remove CD, reboot.
You are persistent.

---

### Post by C.S.Cameron on 2012-08-14
> **ronacc said:**
> I do NOT want  the persistence file to default to ON . It should be an option that you have to enable not the other way around.

Follow the above but do not edit text.cfg.
When booting press F6 and type <space>persistent to get a persistent session.

---


---
title: "Slow hard drive response in 12.04"
date: 2012-03-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sg3524 on 2012-03-15
I recently acquired a Lenovo Z570 laptop to replace an  older Asus.

It uses a I7 2670QM four core processor and a 750G 5400 RPM hard drive.  I think everything on this system is getting throttled by the hard drive.  I loaded 12.04 onto it.

IT seems like anything that requires reads or writes from the hard drive is running much slower than my older Asus (also 5400 rpm drive).  Running hdparm -t /dev/sda nets 95.65 MB/per second.

This seems fairly respectable, but again, everytime I do anything disk intensive it takes much longer than it did on my previous laptop.

The only other difference I can think of would be that my old laptop was using ext3 and the new on is using ext4.  I don't think that is the problem.

Is there something new in 12.04 that might be causing this problem?

Additional information:
Drive is running AHCI mode and I confirmed that dmesg recognized it as such

Changing drive mode in BIOS did nothing.

Drive partitions are: etx4 at /, fat16 at /boot/efi, + 6GB swap.

This is really noticeable when I do local web development running MySQL, but is not limited to that.

Thanks for any help

---

### Post by 2F4U on 2012-03-15
Think about using the relatime or noatime filesystem options:

[http://en.wikipedia.org/wiki/Fstab](http://en.wikipedia.org/wiki/Fstab)

---

### Post by ubudog on 2012-03-15
*Thread moved to Ubuntu +1.*

---

### Post by sg3524 on 2012-03-15
> **2F4U said:**
> Think about using the relatime or noatime filesystem options:

[http://en.wikipedia.org/wiki/Fstab](http://en.wikipedia.org/wiki/Fstab)

That was a good read.  Thanks for passing it on.  Based on that article the kernel I am using will default to relatime.  I couldn't find a way to confirm this so added the option to fstab and rebooted.

Unfortunately no change.  I am going through some reconfiguration of MySQL to better optimize it.  Will report back, but any other suggestions are welcome and invited.

---

### Post by screaminj3sus on 2012-03-15
Ubuntu has used relatime by default since 8.04

---

### Post by dcstar on 2012-03-17
> **sg3524 said:**
> I recently acquired a Lenovo Z570 laptop to replace an  older Asus.

It uses a I7 2670QM four core processor and a 750G 5400 RPM hard drive.  I think everything on this system is getting throttled by the hard drive.  I loaded 12.04 onto it.

IT seems like anything that requires reads or writes from the hard drive is running much slower than my older Asus (also 5400 rpm drive).  Running hdparm -t /dev/sda nets 95.65 MB/per second.
..........
Thanks for any help

Newer hardware is no guarantee that it is going to be "faster" that what it replaces. All of these things are built to a minimum cost, and a bigger sized hard drive may well perform worse than a smaller one as the trade-off for the larger capacity.

Unless you install earlier version of Ubuntu on this new hardware and then do direct comparisons with the performance of 12.04, then your original premise of 12.04 being "slower" has no validity.

---


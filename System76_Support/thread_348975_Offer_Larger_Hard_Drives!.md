---
title: "Offer Larger Hard Drives!"
date: 2007-01-29
forum: System76 Support
---

### Post by zachtib on 2007-01-29
I'd like to buy an S76 laptop at some point, but one disappointment is that you don't offer very large hard drive options.  The largest I've seen on your site is 100GB.  Now that 5400rpm 160GB drives are available, and also 4200rpm 200GB drives, it would be nice if you offered them.  I don't want to buy a System76 laptop and have to buy another hard drive for it separately.

Is there a particular reason you only offer up to 100GB?

---

### Post by crichell on 2007-01-29
> Is there a particular reason you only offer up to 100GB?

We have reliable stock up to that size.  Above that stock reliability gets shaky.

---

### Post by iMav on 2007-03-05
I assume that swapping out a larger-capacity drive would be trivial?  (or does disassembly rival the old iBook's?)  :)

---

### Post by crichell on 2007-03-06
> I assume that swapping out a larger-capacity drive would be trivial? (or does disassembly rival the old iBook's?)

I haven't disassembled an iBook but ours are simple - a couple of screws on the bottom of the lappie.

---

### Post by Mateo on 2007-03-06
Similar question, but about the desktop.  My 2 year old computer has a 250gb hard drive, but the Ratel only has 250 as the max.  I'd want at least 300gb.  But what would really be nice is if you offered more than one hard drive.  Two 250gb would be good.

---

### Post by AusIV4 on 2007-03-07
I don't know what your comfort level with taking apart computers is, but on desktops adding a hard drive is about the easiest thing you can do to the inside of a computer, and a 250 GB hard drive will run you about $60 if you find the right deal. I'd find out what kind of connectors the mobo has and get an extra hard drive. 

The challenging part about adding another drive is understanding how to mount filesystems. I have a 40 GB root filesystem, and a 400 GB raid as my /home/ file system. Without using RAID or LVM, you can't have more than one disk contributing to your /home directory (unless you split different users up on different disks).

If System76 were going to offer multiple drives, they'd have to deal with how the drives should be mounted, and that gets complicated quickly.

---

### Post by maniacmusician on 2007-03-08
> **AusIV4 said:**
> I don't know what your comfort level with taking apart computers is, but on desktops adding a hard drive is about the easiest thing you can do to the inside of a computer, and a 250 GB hard drive will run you about $60 if you find the right deal. I'd find out what kind of connectors the mobo has and get an extra hard drive. 

The challenging part about adding another drive is understanding how to mount filesystems. I have a 40 GB root filesystem, and a 400 GB raid as my /home/ file system. Without using RAID or LVM, you can't have more than one disk contributing to your /home directory (unless you split different users up on different disks).

If System76 were going to offer multiple drives, they'd have to deal with how the drives should be mounted, and that gets complicated quickly.
You can't mount a partition to a mount point inside the /home/[user] director? I'd always thought that was possible.

---

### Post by AusIV4 on 2007-03-08
> **maniacmusician said:**
> You can't mount a partition to a mount point inside the /home/[user] director? I'd always thought that was possible.
Sure you can. What I meant  is there's no way to simply make your home directory larger. You can mount another file system anywhere you can make a directory. The point is, different users would need different configurations for multiple hard drives, which doesn't lend itself well to pre-configured systems. It's not quite as simple as windows where they just appear as the C:\ drive and the D:\ drive.

---

### Post by Mateo on 2007-03-09
> **AusIV4 said:**
> I don't know what your comfort level with taking apart computers is, but on desktops adding a hard drive is about the easiest thing you can do to the inside of a computer, and a 250 GB hard drive will run you about $60 if you find the right deal. I'd find out what kind of connectors the mobo has and get an extra hard drive. 

The challenging part about adding another drive is understanding how to mount filesystems. I have a 40 GB root filesystem, and a 400 GB raid as my /home/ file system. Without using RAID or LVM, you can't have more than one disk contributing to your /home directory (unless you split different users up on different disks).

If System76 were going to offer multiple drives, they'd have to deal with how the drives should be mounted, and that gets complicated quickly.

ok, then simply offering one 400gb drive would be fine for me.

---

### Post by beefcurry on 2007-03-12
You Storage is a big problem with me (have 3 Crates of burned DVD's lying around) and Its much more efficient if you have external harddrives (have 3). But having 1 System drive and 3 storage USB's does get innoying sometimes but the good thing is the 3 Externals are only used for storage and there is an On Off Button, meaning I can keep it off when not using it.

However I just needed more and more space so then I brought an Infrant ReadyNAS NV, its a 1TB NAS connected via Giga Bit lan , its just a Massive RAID external harddrive if you like. More more dynamic then having one massive drive.

---


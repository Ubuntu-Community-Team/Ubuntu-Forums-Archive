---
title: "Problem with Ubuntu Studio install (dual boot, CPU has UEFI, Windows 8.1)"
date: 2013-12-21
forum: Ubuntu Studio
---

### Post by Henry04 on 2013-12-21
**Situ:**

AMD64, HP Pavillion-500-046 desktop, does dual boot with Windows 8.1 (2TB internal hd), which has a UEFI booting scheme, & (presently) Linux Mint 16, Mate-Petra on a 90 GB portion of a 2 TB external usb 3 LaCie hd.

**What I tried to do**: 

As my internal hd was partitioned in approximately two equal partitions... the* second one was formatted to ext4 & had an install of Mint 16, that at first functioned, **until I messed up the '/etc/fstab' trying to get my external usb hd to mount..**.* (& I accessed it by having the rEFInd Boot Manager CD in my HP UEFI CD/DVD disk drive: [http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html) ).

I tried out the Ubuntu Studio live DVD... look very suitable to (some of) my actual needs, so I tried to install Ubuntu Studio on the internal Linux, ext4 partition (I couldn't get it to install on a little portable usb 3 Toshiba 500 GB hd, the installer kept complaining about my mount point being external to... (?), which was "/" on the device /dev/sdc in this case). 

Ok, so the installer choices I thought I was making, was something like on the previously afore mentioned Mint-Petra in the internal hd (keeping in mind, my Windows 8.1 was the first set of partitions): erasing Petra, installing Ubuntu Studio; *the installer did **NOT** say anything about removing Windows (!!)... but not only did the install wipe out Windows... cleared the whole disk... UEFI then, not available... got the "grub>" (or is it ">grub" (whatever, dang thing wouldn't mount/boot anything ]  :sad:.*

I managed to recover Windows 8 (& upgrade again to 8.1) & restored some of my Windows personal data... & now my internal hd is back to all NTFS.

Of course, this leaves me MORE than a little apprehensive about what this installer will do, if I try another route, which I think I am (hoping) to be more prepared, physically in terms of space, to try another install;** NOW on my EXTERNAL usb...** (with the other/s for additional storage... that is, has been, all too often for me, an "ownership" issue... *In other words, need to have it mount, & be read & write-able.. a serious.s problem I have been having: which raises a SERIOUS question (for me, least wise): Why the heck are Linux formatted disks so much more difficult to mount & utilize (from Linux) than WINDOWS (i.e., NTFS formatted)?????*

Any help advice in these regards *will* be appreciated.

Thanks in advance.

Henry04

P.s., I tried booting the Ubuntu Studio live DVD with 'secure boot' enabled... i.e., through UEFI... it would get as far as the opening menu, but try Ubuntu Studio live, the CPU would hang at a blank window... didn't try to install... so I can not report about that... but my install that I try to discuss above, was with 'secure boot' disabled, & 'legacy' enabled (as well as 'fast boot' disabled').

P.p.s., I installed grub 2 on my current Linux Mint OS... on the usb hd Mint resides on, & it works, to access Mint (at least, I have not tried to boot Windows from grub, but grub apparently recognizes it).

---


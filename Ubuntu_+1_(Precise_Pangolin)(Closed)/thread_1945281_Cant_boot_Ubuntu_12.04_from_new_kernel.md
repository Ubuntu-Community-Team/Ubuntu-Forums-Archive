---
title: "Cant boot Ubuntu 12.04 from new kernel"
date: 2012-03-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by johnnyde94 on 2012-03-22
I have been having problem for a while now trying to get Ubuntu to boot. I have a dell C521 and have disk set up as GPT(because MRB is so old) with newest kernel. I have tryed using boot repair with no luck. If i use parted magic CD and and go to super grub2 disk i can get it booted. here is the URL of parted magic "DX"

[http://paste.ubuntu.com/895931/](http://paste.ubuntu.com/895931/) 

Thanks in advance,):P:p
John

---

### Post by oldfred on 2012-03-22
I cannot tell for sure but it looks like your bios_grub which is unformated space for grub's core.img only is mixed up with a ext4 /boot partition both sda1. Not sure how that is done.

The bios_grub has to be unformated space and only needs to be 1MB. Most desktops do not need a separate /boot and it just complicates things. Only those configured more like a server with RAID or LVM, or very old systems with BIOS limits that only boot from the first 137GB may need a separate /boot.

Change format of sda1 to no format. Leave it as your bios_grub. Only install grub to the MBR of sda not to any partitions. Grub has not fully installed as you do not show a grub.cfg nor core.img which it has a copy of in your partition.

If you can boot into your system after correcting the sda1 partition you may be able to just reinstall grub. You can skip the chroot part of the instructions
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

sudo dpkg-reconfigure grub-pc

---

### Post by cariboo on 2012-03-22
When you say it won't boot, what do you mean, does it just sit at the grub menu? Does it get past the grub menu and stop at the Ubuntu logo? Does it boot to the login screen, but the screen is black?

I had a problem with the previous kernel update, where grub claimed a partition didn't exist. After using the same hard drive order in the BIos since the toolchain was uploaded, I just changed which disk was first, and the system booted the way it should. I suspect this had nothing to do with the kernel update, but it's something to look at.

---

### Post by saksmlz on 2012-03-23
I have the same problems with 3.2.0-19 and 3.2.0-20. 3.2.0-18 - boots fine.
It doesn't boot - means that it freezes and does nothing after pressing "Return" in the grub2 menu. Screen is black, cursor is blinking but nothing more. No HDD activity. I was waiting 10 minutes or more - nothing.

---

### Post by oldfred on 2012-03-23
@saksmlz - welcome to the forums, but
Please start your own thread, unless detail of issues is identical (rare on boot issues).
Yours  may be video related.
How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by johnnyde94 on 2012-03-25
Thanks for all the help but, I could not get it to boot right. I just decided to revert back to MRB and I was able to boot just fine. Hopefully grub2 will be fixed to make it not as hard to boot into a GPT

---

### Post by oldfred on 2012-03-25
Sorry you could not get it to work. 

I have three drives, one rotating, one SSD & one flash all formated with gpt with a bios_grub partition and all three install and boot without issue with BIOS. Most are having issues with UEFI which is not so straightforward.

---


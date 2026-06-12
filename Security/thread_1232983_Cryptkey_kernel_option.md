---
title: "Cryptkey kernel option"
date: 2009-08-06
forum: Security
---

### Post by MrBabyface on 2009-08-06
Hello, 
I installed jaunty with all partition encrypted (except boot of course) and following this :
[http://wiki.archlinux.org/index.php/LUKS#Storing_the_key_between_MBR_and_1st_partition](http://wiki.archlinux.org/index.php/LUKS#Storing_the_key_between_MBR_and_1st_partition)
I found out that if added to kernel option, root partition can be unlock with a key stored on a block-device sectors with the cryptkey option (cryptkey=/dev/sd[a-z]:OFFSET:SIZE) but it doesn't seam to work for me.
It keeps asking for passphrase for root partition at boot. Do I have to build a custom kernel that support this option ? 
Is this an initrd issue or a kernel issue ?
By the way I also add a "test" key to root partition from internal drive to be sure it's not usb related and I get the same none working cryptkey kernel option.
Tried also with initrd with no root partition in crypttab to be sure it doesn't ask for passphrase but then it doesn't even try unlock root partition on boot.

---

### Post by Johnny B on 2009-08-06
aren't you using a key that requires a passphrase?
[http://wiki.archlinux.org/index.php/LUKS#Keyfile_.28visible_on_external_USB_stick.29]("http://wiki.archlinux.org/index.php/LUKS#Keyfile_.28visible_on_external_USB_stick.29")

im probably not able to answer your question, but here look at this:

[ftp://ftp.ccc.de/congress/22C3/lectures/video/mp4-avc/320x240/22C3-1112-en-modern_disk_encryption.m4v]("ftp://ftp.ccc.de/congress/22C3/lectures/video/mp4-avc/320x240/22C3-1112-en-modern_disk_encryption.m4v")

[http://www.linux.com/archive/feature/52820]("http://www.linux.com/archive/feature/52820")

---


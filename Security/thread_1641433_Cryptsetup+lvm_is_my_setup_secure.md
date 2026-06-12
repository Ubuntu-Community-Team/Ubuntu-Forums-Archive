---
title: "Cryptsetup+lvm: is my setup secure?"
date: 2010-12-09
forum: Security
---

### Post by vangop on 2010-12-09
Hi!
I'm new to cryptsetup but want to have some parts of the system encrypted.
There's a great explanation [here]("http://ubuntuforums.org/showthread.php?p=7576717") on how to encrypt the whole disk.
My intention is to have:
1. both encrypted and unencrypted volumes
2. have lvm manage them, so that I could easily change the sizes when needed.

I created a primary partA, and logical partB.
PartA is setup for LVM, partB is for encryption.
Then I created a volume group vg1 and added partA to it. Then created a log. vol. lvroot with ext4 and mounted it as /

Then extended the vg1 with partB (after setting it up for encryption), and created the following volumes lvhome (/home), lvdata (/data) and lvswap (swap).

My assumptions are: ununcrypted root with encrypted /home, swap and /data (80% of drive). I am able to change the sizes since they all are managed in lvm when needed. I assume I can easily take from /data and add to /home (since they are under same encrypted drive) and a bit harder take from /data and add to root, since I have to reduce the enc device and then add the free space to unencrypted one.

Please tell me that that's gonna work, and my assumptions are correct. 
Please tell me that I have secured the system, since I don't know where cryptsetup stores the passphraze/keys, and I'm exposing the / ununcrypted (and it might just store them there??)

EDIT: LVM cannot be used to boot from, so I created a primary /boot partition outside of lvm.

Thanks a lot!

---

### Post by vangop on 2010-12-09
Heck, this setup is not working, while installing the system I get update-grub failed error. Even if I try to boot from rescue cd and fix it as [described]("http://ubuntuforums.org/showthread.php?t=1581099") it won't work, I get grub prompt at boot..

---


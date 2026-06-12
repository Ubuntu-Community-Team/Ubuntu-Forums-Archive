---
title: "lvm mirroring and dmcrypt managament"
date: 2008-04-15
forum: Server Platforms
---

### Post by finite9 on 2008-04-15
Im going to buy 2 new external triple interface discs but will initially use them with 1394a interface.

I love LVM and will set them up as a mirrored volume group for redundancy, but I also want to use dmcrypt for a small portion of the disc.  Can I do this??

How do I initially setup up LVM to use the second disc as a mirror?

I currently have an external disc that is lvm'ed and dmcrypt'ed with no mirroring, but it is one big 320GB partition.  If I want one partition that is dmcrypted on the new discs with LVM on top, mirrored, can I then create a second larger partition on the same disc that is LVM without dmcrypt?

What is the best way to do dmcrypt and LVM from a disc management perspective...should I dmcrypt the disc and setup lvm on top or lvm the disc then do dmcrypt?  Which way will provide me with the most flexible disc management/volume group management capabilities?

Im not bothered about having to enter dmcrypt passphrases as its a server that i rarely turn off.

---

### Post by finite9 on 2008-04-15
By the way, what is the point of software RAID when you have LVM??  I saw a post whilst typing this about someone using LVM with RAID-5, and it seems pointless to me to implement both as they both do the same thing.

---

### Post by finite9 on 2008-04-18
answer to my own question, so others know...

you can implement mirroring in lvm, but it's more work to do it this way.  It is easier to implement RAID-1 on the two discs with mdadm, then put an lv on top of the software raid array.  better from a disc management perspective this way.

As for multiple partitions, it shouldn't be an issue...

create a 150GB raid-1 partition across the two discs then put an lv on top of it.  This leaves 350GB left that I can partition again as RAID-1 then put dmcrpyt on top of that, and lastly put lvm on top of dmcrypt.  Although this way, I will probably kill my CPU what with having to go through dmcrypt and then raid.  CPU is already a significant issue just having dmcrypt on a disc, but I am using the version in Gutsys repo, and it might be more efficient in Hardy, but I have not yet tried.

Might be harder to add a pv to an lv at a later stage if using dmcrypt under lvm as I do not know if you can grow a dmcrypt partition.

---


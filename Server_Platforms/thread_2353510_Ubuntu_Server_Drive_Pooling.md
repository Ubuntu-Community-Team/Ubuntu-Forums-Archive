---
title: "Ubuntu Server Drive Pooling"
date: 2017-02-22
forum: Server Platforms
---

### Post by voyto on 2017-02-22
Hi all. Today I'd did some tweaks on my windows home server and somehow broken it. It now refuses to boot. 

I've been waiting for an excuse for a whole now to make the switch to Ubuntu server. 

My question however is, on Windows I used some software called drivepool which allowed me to mix together a mishmash of hard drives into one virtual drive, sort of like a raid without matching disks. Can I do the same using Ubuntu? 

Thanks!

---

### Post by howefield on 2017-02-22
Thread moved to the "*Server Platforms*" forum, probably a better fit for responses.

---

### Post by ajgreeny on 2017-02-22
Using LVM partitioning sounds as if it will do what you want according to the thread at [http://askubuntu.com/questions/861444/how-to-use-lvm-to-make-two-hard-drives-act-as-one](http://askubuntu.com/questions/861444/how-to-use-lvm-to-make-two-hard-drives-act-as-one)

My knowledge of LVM is zero so I can not personally help further, but this may give you a start from which you can search for more info.

Good luck!

---

### Post by voyto on 2017-02-22
Thank you! Installed this evening and LVM was exactly what I was looking for! I assume I can add more disks to the volume without data loss on the existing members of the volume?

---

### Post by The Cog on 2017-02-22
Yes. You need to add the new physical volumes to the volume group, then increase the size of the logical volume, then use resize2fs to resize the ext filesystem that lives on the logical volume.

Maybe just doing some stirring, but unless you are using encryption, using btrfs as a filesystem might be simpler than the multiple layers of LVM. Btrfs allows adding and deleting partitions to the filesystem on the fly too. I don't think btrfs does encryption.

---

### Post by rubylaser on 2017-02-23
With a spanned LVM volume on top of a bunch of disks without parity (like mdadm), you will lose all of your data in the in the event of a failure. I find [MergerFS]("https://github.com/trapexit/mergerfs")  to be perfect for what you are describing.  Each disk is independent, and the failure of one does not cause a loss over the entire pool.  Also, you can couple it with SnapRAID if you want data protection (parity).  I have found this to be a perfect fit for my home media server.  Here are a few tutorials I have written on these topics if you are interested.

[http://zackreed.me/mergerfs-another-good-option-to-pool-your-snapraid-disks/](http://zackreed.me/mergerfs-another-good-option-to-pool-your-snapraid-disks/)
[http://zackreed.me/setting-up-snapraid-on-ubuntu/](http://zackreed.me/setting-up-snapraid-on-ubuntu/)

---

### Post by dasjestyr on 2017-11-26
But what about redundancy/parity? LVM groups the disks, but does it provide any options for replication? If a drive goes bad, I need to a) know that the data is still there and b) be able to pull that disk and replace it without having to move data around first. I've been using StableBit DrivePool on windows for a while now and it's perfect. However, I did something similar where I gump'd up the windows install and need to reinstall and have been looking for an excuse to switch it to linux, so I'm in the same situation.

---


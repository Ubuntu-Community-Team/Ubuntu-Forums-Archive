---
title: "EXT4 vs NFTS (on the health of HDD)"
date: 2018-06-12
forum: Ubuntu, Linux and OS Chat
---

### Post by ardouronerous on 2018-06-12
I was wondering what are the benefits of EXT4 over NFTS on the health and longevity of HDDs, does EXT4 minimize bad sectors?

Two benefits I know is that EXT4 doesn't need to be defragged and EXT4 doesn't suffer significant system slowdowns because it doesn't fragment the drive like NFTS does, but what does that mean for the overall health of the HDD?

---

### Post by Morbius1 on 2018-06-12
You are about to get a barrage of answers to your question but I would just like to point out one thing: 

An NTFS partition in Linux performs far differently than an NTFS partition in Windows especially if that Windows is Win10. For one thing Linux creates a "view" of the partition using fuse that gives it the appearance of having Linux ownership and permissions bits when in fact it has none. As a result it is slower in Linux than Windows.

So which is better in the abstract is different from which is better in Linux.

I can't see a justification for using NTFS in an all Linux system and if it's a dual boot with Windows you don't have much choice.

---

### Post by ajgreeny on 2018-06-12
One other thing you must bear in mind is that any problems in the NTFS filesystem will not be repairable in Ubuntu but will demand a Windows system for the repair.

Therefore if you do not also have an available Windows OS to use for that repair I recommend you steer clear of NTFS.

---

### Post by ardouronerous on 2018-06-13
Thanks for the information on NFTS within Linux.
Generally, I do not dual-boot, I use Virtualbox instead because dual-booting is a hassle to do.

Based of what I read, since NFTS needs to defragged on a regular basis, the process of defragmenting uses a lot of read and write cycles that causes wear and tear on the drive, but since EXT4 doesn't need to be defragged unlike NFTS, EXT4 doesn't suffer from the same wear and tear caused by read and write cycles that NFTS does, making EXT4 less prone to bad sectors.

How true is this?

---

### Post by Morbius1 on 2018-06-13
If this is an all Linux box it is academic. Linux doesn't have an NTFS de-fragmenting tool.

For NTFS on Windows it depends on how high up on the food chain your are. Win10 really tries to be smart about this and attempts to do what EXT4 does when it saves files but ....

De-fragmenting in Win10 is automatic but on an SSD rarely happens because of the excessive r/w required to accomplish the task.

Not sure if bad sectors are linked to excessive defragmenting.

---

### Post by mastablasta on 2018-06-14
> **ardouronerous said:**
> 

Based of what I read, since NFTS needs to defragged on a regular basis, the process of defragmenting uses a lot of read and write cycles that causes wear and tear on the drive,

it depends on what you do on the drive. if you just store data then there is hardly any fragmentation on that partition. the most fragmentation is done on system drive but even there i didn't have that much after 10 years of use. yes it was after 10 years when i had to defragment the drive (WinXP) to prepare it for imaging an moving the whole thing to another drive and expanding it.

also the ext4 is not really the end of development. it was made as a stopgap measure. currently file systems such as ZFS (ZFS4linux) and BTRFS or similar (i believe Redhat will make their own)are made, explored and installed for places where robust data, data safety and file system stability is needed.

in terms of longevity again it depends what will you do on disk? there is a large data center that published disk wear survey every year or so. you can see how their disks fail within a year or two. but yours will likely last at least 5 if not 10 years or more. depends on the batch i guess.

---


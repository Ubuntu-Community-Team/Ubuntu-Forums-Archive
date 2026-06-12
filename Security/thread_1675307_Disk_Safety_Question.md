---
title: "Disk Safety Question"
date: 2011-01-25
forum: Security
---

### Post by OxentroT on 2011-01-25
I am going to be saving a mass amount of data on an external disk for a project and was wondering if there are any sort of precautions I can take to be sure that the disk or files do not become corrupted in any way.

Thank You!

---

### Post by howefield on 2011-01-25
Depends on how serious you are.

If the data is important, you'll have more than one back up. Build in some redundancy irrespective of how healthy you believe your disk is. There is always a chance that your data will corrupt for one reason or another.

---

### Post by HermanAB on 2011-01-25
Howdy,

For protection against corruption (improved integrity) use a file system with a journal, for example Ext3, Ext4, XFS, JFS or ReiserFS.  That is, pretty much anything except FAT or Ext2.

To ensure integrity during the copy process, use rsync instead of cp.  Rsync uses cryptographic checksums to verify each block copied.

---

### Post by psusi on 2011-01-25
Keep a backup copy on another disk.

---

### Post by OxentroT on 2011-01-27
Thank All of you for your input! I am leaning towards multiple storage devices *just-in-case* as it seems I have recurring nightmares of my old HDD expiring out of nowhere and I lost 40GB or so of music.

As you have mentioned:
HermanAB> For protection against corruption (improved integrity) use a file system with a journal, for example Ext3, Ext4, XFS, JFS or ReiserFS. That is, pretty much anything except FAT or Ext2.

To ensure integrity during the copy process, use rsync instead of cp. Rsync uses cryptographic checksums to verify each block copied.

I am interested in learning in detail about the different file systems and their pros/cons between each one and was curious if someone could recommend me any good books on that subject.

Thank You!

---

### Post by Boondoklife on 2011-01-27
You may want to also look into setting up or getting a small NAS in Raid1. This will make sure the two disks are duplicates and if one fails you don't loose any data.

If it is really critical data an rsync to an offsite server is another good idea in addition to the NAS.

---

### Post by OxentroT on 2011-02-01
Thank You All for your suggestions! I was asking from the perspective of one who isn't currently in the position to buy multiple disks (let alone remote storage).  Nevertheless, I am going to take this advice but I am going to have to save up a little bit for multiple disks before I forego this project. 

Thank You again. 

:guitar:
Rock On!

---

### Post by The Cog on 2011-02-01
Just one comment: Using RAID doesn't protect against mistakes that delete your precious files - both copies get deleted real quick. I would suggest manually maintaining two separate copies on different disks, and don't plug them both in at the same time.

---


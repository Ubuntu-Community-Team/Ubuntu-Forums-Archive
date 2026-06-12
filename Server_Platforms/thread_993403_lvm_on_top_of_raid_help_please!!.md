---
title: "lvm on top of raid help please!!"
date: 2008-11-25
forum: Server Platforms
---

### Post by monkeyanengineer on 2008-11-25
This is one that i have not been able to find any documentation on.

Problem: my 3.18tb lvm volume will not mount

My setup: i have ununtu 7.10 server 64-bit with webmin installed. this is where it gets fun. i have 5 disks.  3 are 500gb ide drives in a software raid-0 /dev/md2.  two more are 1tb sata disksin a second raid-0 array /dev/md1.  i know i know raid-0 is horrible but i was stupid.  these two raid arrays were being used as lvm drive.  my electicity wint out and when it came back on that is when the fun started.  the lvm would not mount.  after some investigation i have discovered that one of the 1tb drives is not working properly.  /dev/md1 was showing as inactive on webmin.  i enabled it manually and did a pvdisplay.  no errors came up.  i thought that all was well, however when i tried to mount the lvm it failed.  it said bad superblock.  however when i did a vgscan i noticed that my there were errors in my physical volumes.  i looked at my raids again and now /dev/md1 was showing as not active. for some reason when i tried to mount the lvm it moved the location of one of the 1tb drives from /dev/sdb1 to /dev/.static/sdb1,

Finally the question: why did my dev point move when i tried to mount the lvm? please let me know any information that i left out.

Thanks in advance!!

---

### Post by Philio on 2008-11-25
Hopefully you don't have any valuable data stored on your disk, RAID 0 is not exactly a good option for important data!

The bad superblock error when mounting means that the ext3 filesystem on the lvm partition is corrupt, it might be possible to repair and recover the partition, however considering your raid is not working properly it sounds like this may not be the source of the problem.

Are you sure both the drives are working ok? If the power cut has managed to damage one of the drives this would explain why the RAID is not working correctly, the LVM volume(s) obviously require the RAID to be up and running and in turn the filesystem requires the LVM partition/groups to be working to enable it to be mounted. You need to look at the separate components in this order really.

If you manage to get it working again consider moving off RAID 0 ASAP if you have any important data on your drives!

---

### Post by monkeyanengineer on 2008-11-26
i am just going to concede defeat and wipe my raid arrays. now to raid-5....lesson learned

---


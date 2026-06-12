---
title: "Resizing Encrypted Luks partition from 12.04 ( No LVM )"
date: 2012-10-11
forum: Security
---

### Post by microchip13 on 2012-10-11
I setup whole disk encryption with the alternative installer on 12.04, and it seems to have gone with using an encrypted partition rather than an LVM.

If I follow the guide at:
help.ubuntu.com/community/ResizeEncryptedPartitions

None of the VG commands do anything. All I'm left with after I initialize the disk is a device /dev/mapper/sda2_crypt. I can mount that and happily see my filesystem (though oddly, fdisk doesn't report anything on it). 

I have 3 partitions - sda1 which is boot, sda2 which is my luks partition, and then sda3 which is a partition I had intended to use for windows, and am deciding to just merge it with my linux partition.


I feel I have to enlarge the sda2 partition, then enlarge the crypt of it? That's where I get lost.

Help Please?!

---

### Post by BrandonIngalls on 2012-10-15
If you have a external hdd or flash drive that can hold the files on your luks partition, I would recommend creating a tarball of that filesystem with something like this from a Ubuntu liveCD(as root)...
```
cd /media/encryptedfs/
tar -cvzpf /media/ExternalHdd/fs.tar.gz *
blkid > /media/ExternalHdd/fsuuids.txt
```

Then you could delete the partition and create a new one that fills up the space and once you do that you re-create the luks partition using the name uuid and then re-create the filesystem using its uuid and name.
Then it is as simple as
```
tar -xvzpf /media/ExternalHdd/fs.tar.gz -C /media/encryptedfs/
```

---


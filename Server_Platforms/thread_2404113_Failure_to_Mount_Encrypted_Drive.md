---
title: "Failure to Mount Encrypted Drive"
date: 2018-10-20
forum: Server Platforms
---

### Post by linus_leung on 2018-10-20
I wanna mount encrypted drive in Ubuntu server 16.04, but found error as follows. Could anyone suggest solutions?

sudo cryptsetup luksFormat /dev/sdb
sudo cryptsetup luksOpen /dev/sdb my_encrypted_volume

sudo mount /dev/mapper/my_encrypted_volume /test
mount: wrong fs type, bad option, bad superblock on /dev/mapper/my_encrypted_volume,
       missing codepage or helper program, or other error


       In some cases useful info is found in syslog - try
       dmesg | tail or so.

---

### Post by TheFu on 2018-10-20
You need to create a file system on /dev/mapper/my_encrypted_volume after it is open, but before mounted.

mkfs is the tool. There are others.

---

### Post by darkod on 2018-10-20
To add to what TheFu said, I wouldn't be using the whole drive like you are. Create a partition on it, don't use the drive designator /dev/sdb as a device to encrypt.

---

### Post by TheFu on 2018-10-20
Good catch, darkod!  

While many places use storage without partitioning, I would rather have partitioning to ensure someone doesn't get confused with storage they can't read and just wipe it completely by accident.  Having a partition table would provide an extra opportunity to catch that sort of mistake.

---


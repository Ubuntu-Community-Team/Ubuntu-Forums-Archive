---
title: "iscsitarget problem on ubuntu natty???"
date: 2011-06-30
forum: Server Platforms
---

### Post by jk.cheng on 2011-06-30
i have install the iscsitarget on my new install ubuntu 11.04 server

```
sudo apt-get install iscsitarget
```

i also have enable the default daemon load

```
sudo vi /etc/default/iscsitarget
ISCSITARGET_ENABLE=true
```

i check the hdd to share with fdisk

```
fdisk -l /dev/sdb
```

result /dev/sdb:21.5GB with /dev/sda1 as partition

however, when i start adding my hdd to scsi it shown no file/directory found..

```
sudo ietadm --op new --tid=1 --lun=0 --params Path=/dev/sdb
No such file or directory
```

same when i add it on the partition side

```
sudo ietadm --op new --tid=1 --lun=0 --params Path=/dev/sdb
No such file or directory
```

i wonder what is the problem here???

---

### Post by rubylaser on 2011-06-30
This is old, but still works fine.
[http://www.howtoforge.com/using-iscsi-on-ubuntu-9.04-initiator-and-target](http://www.howtoforge.com/using-iscsi-on-ubuntu-9.04-initiator-and-target)

The only thing that has changed is the ietd.conf location.  Off the top of my head, I think it's at /etc/ietd/ietd.conf now.

---

### Post by jk.cheng on 2011-06-30
thanks for the reply... i already looking into this tutorial... on my side loading LUN form image, LVM and RAID5 seem ok... only the above error occurred when i trying to load the LUN direct from physical drive...

---

### Post by rubylaser on 2011-06-30
Have you tried to run the iscsitarget from the partition on the disk rather than the raw disk? (You mentioned having a partition on the drive earlier).

```
sudo ietadm --op new --tid=1 --lun=0 --params Path=/dev/sdb1
```

---


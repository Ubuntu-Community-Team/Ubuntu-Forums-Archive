---
title: "LVM on RAID problem."
date: 2010-08-31
forum: Server Platforms
---

### Post by vpablos on 2010-08-31
Hi there,

I've a server that has been running from Hardy Heron (now it was running Lucid Lynx) with 3 raid partitions (mdadm) and using lvm in the third partition to support partitions for /usr, /var, /srv, /home, etc.

Past friday something went wrong and after I ordered an 
array rebuilt (second hard disk went down and I reboot the machine
first). After the rebuilt finishes I reboot the machine to see 
if it was capable to detect and use raid again and now it is unusable.

Problem is not that it is non-bootable (I do not care about that), 
but that there is some information on the third partition that is not accesible (I can not see any LVM partition) and we can not recover from backups.

I've tried ubuntu Lucid Lynx installation desktop CD and alternate CD by installing the following packages 
lvm2 dmsetup mdadm 
but I have only been able to see the Linux raid autodetect partition.

Can you help me to recover my data?
Thanks.

Victor

Some links I've read:

[http://aplawrence.com/Linux/rebuildraid.html](http://aplawrence.com/Linux/rebuildraid.html)
[https://help.ubuntu.com/community/Installation/RAID1%2BLVM](https://help.ubuntu.com/community/Installation/RAID1%2BLVM)
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID)

---

### Post by sh1ny on 2010-08-31
Did you manage to bring the raid up again at all ? You won't see lvm partitions until the raid is up and functioning.

Don't do backups on local disks also :(

---


---
title: "I'm dumb, need baby help to create a local datastore with vmware"
date: 2009-06-30
forum: Virtualisation
---

### Post by sdowney717 on 2009-06-30
ok, I can run vmware web interface
I am logged in, I can run VM's.

I can not create any local datastores. I assume a "local datastore" is just a place to put virtual machines like on a second hard drive.
I have tried, it just always says file not found.
I have also tried to do this on my primary drive and cant do it.

my second drive is sdb1
I would like to put a virtual machine over there
Can any of you tell me the proper path and every file needed in the other directory?

```
scott@scott-desktop:/bin$ ./df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             70153596  62008568   4581412  94% /
tmpfs                   513352         0    513352   0% /lib/init/rw
varrun                  513352       416    512936   1% /var/run
varlock                 513352         0    513352   0% /var/lock
udev                    513352       176    513176   1% /dev
tmpfs                   513352       980    512372   1% /dev/shm
lrm                     513352      2192    511160   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sda1            122575918  97597382  24978536  80% /media/disk
/dev/sr0                145860    145860         0 100% /media/cdrom0
/dev/sdb1             57707836  47932160   6844220  88% /media/disk-2
/dev/sr1                  1664      1664         0 100% /media/cdrom1
/dev/sdc                 18016       319     17697   2% /media/PHONE

```

---

### Post by Cheesemill on 2009-06-30
The directory that you enter into VMware has to already exist.
Just use /media/disk-2 if that's where your second drive is mounted.

---

### Post by sdowney717 on 2009-06-30
thanks, I got it
in the field I type

this line worked
/media/disk-2/test

this does not
/media/disk-2/test/test.vmx

---


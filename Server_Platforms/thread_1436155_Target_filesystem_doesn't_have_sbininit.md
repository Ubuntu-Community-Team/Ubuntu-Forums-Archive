---
title: "Target filesystem doesn't have /sbin/init"
date: 2010-03-22
forum: Server Platforms
---

### Post by SmartP on 2010-03-22
My UBUNTU 8.04 server does not boot anymore : here is the error message :
> Target filesystem doesn't have /sbin/init

Previous messages on the boot were :

> kinit: name_to_dev_t(/dev/disk/by-uuid/0a301...a88) = md1(9.1)
kinit: trying to resume from /dev/disk/by-uuid/0a301...a88)
kinit : No resume image, doing normal boot...
Target filesystem doesn't have /sbin/init

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)


My system :
 - Ubuntu 8.04 server
 - 4HDD : RAID 5

Once BusyBox is started, here is the situtatino :
 - in /root : I found ALL my files from the current system
 - /root/sbin/init does not exists

I search the web for solution but in vain. I am not able to repari or I don't know how to.

PLEASE HELP ....

---

### Post by cdenley on 2010-03-22
On hardy, you should have either runit-run, sysvinit, or upstart which provides /sbin/init. I would try chroot'ing your install from a livecd, determine which you are using
```

dpkg-query -S /sbin/init

```
then attempt to reinstall it. Of course, if critical files disappear on you like that, you might want to investigate what may have caused it (bad disk sector, system compromise).

---

### Post by BULLIT22 on 2010-03-22
Just for some Info, I installed Ubuntu server and 3 days later had the same problem. could not boot due to the same error you have. Turns out mine was a failing hard drive. not sure if this is your problem, but at least its a place to look. Thanks.

---

### Post by SmartP on 2010-03-22
Thank you for this quick reply : I am quite new on linux and ubuntu. so my question might be trivial : excuse me for that :

1) How to : chroot'ing your install from a livecd, knowing that when I start from the live CD : the RAID is not built as it is a software RAID => I don't see any files from the resident system

2) "dpkg-query -S /sbin/init" does is not launch on BusyBox

Yes you are right : Once the datase backed up : I will have to reinstall all

---

### Post by SmartP on 2010-03-22
> **BULLIT22 said:**
> Just for some Info, I installed Ubuntu server and 3 days later had the same problem. could not boot due to the same error you have. Turns out mine was a failing hard drive. not sure if this is your problem, but at least its a place to look. Thanks.

Doesn't seems to be the issue as system is on RAID 5 and all RAId is operitional and all files are accessibles exepct init !
Thnks for the tip anyway.

---

### Post by cdenley on 2010-03-22
> **SmartP said:**
> Thank you for this quick reply : I am quite new on linux and ubuntu. so my question might be trivial : excuse me for that :

1) How to : chroot'ing your install from a livecd, knowing that when I start from the live CD : the RAID is not built as it is a software RAID => I don't see any files from the resident system

2) "dpkg-query -S /sbin/init" does is not launch on BusyBox

Yes you are right : Once the datase backed up : I will have to reinstall all

1. I'm not sure how to initialize a software raid array on a LiveCD, but it should be possible. You did not specify that it was a software raid array. I assumed it was hardware.

2. I don't think so. You need to chroot your install from a livecd, then run that command.

---

### Post by SmartP on 2010-03-23
Conclusion :
I could not repair the system. anyway when such a problem happens, it is better to have a fresh start. But I could backup the datas adding a sata drive on the computer : simple but efficient !

Thxs for your help

---


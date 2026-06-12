---
title: "Ubuntu Server 12.04 + Software Raid boot problem"
date: 2012-07-24
forum: Server Platforms
---

### Post by pdnv on 2012-07-24
Hi!

My config is the following: Lenovo M58 with two WD320 HDDs.
I've installed 64 bit Ubuntu Server 12.04 with software raid (RAID1).

My problem is that sometimes the server stops the booting procedure after grub and it takes me to the initramfs console. If I press CTRL-D the boot process continues and everything is OK.

I found the following differences in dmesg:

When it's OK - It's OK for all MD devices (md0-md10):

[    1.799536] md: bind<sda12>
    [    1.802215] bio: create slab <bio-1> at 1
    [    1.802319] md/raid1:md10: active with 2 out of 2 mirrors
    [    1.802339] md10: detected capacity change from 0 to 111970336768
    [    1.807616] md: bind<sda1>
    [    1.809052] md/raid1:md0: active with 2 out of 2 mirrors
    [    1.809070] md0: detected capacity change from 0 to 9998098432
    [    1.812797] md: bind<sda7>
    [    1.814201] md/raid1:md5: active with 2 out of 2 mirrors
    [    1.814221] md5: detected capacity change from 0 to 9998098432
    [    1.823587] md: bind<sda8>

ERROR - It says this** unknown partition table** thing for all MD devices (md0-10) :

[    1.956170] md: bind<sda5>
    [    1.957628] bio: create slab <bio-1> at 1
    [    1.957719] md/raid1:md3: active with 2 out of 2 mirrors
    [    1.957776] md3: detected capacity change from 0 to 9998098432
    [    1.975224]  **md3: unknown partition table**
    [    1.984179] md: bind<sda1>
    [    1.985810] md/raid1:md0: active with 2 out of 2 mirrors
    [    1.985871] md0: detected capacity change from 0 to 9998098432
    [    2.053296]  **md0: unknown partition table**
    [    2.060182] md: bind<sda12>
    [    2.061861] md/raid1:md10: active with 2 out of 2 mirrors
    [    2.061922] md10: detected capacity change from 0 to 111970336768
    [    2.137478]  **md10: unknown partition table**
    
If I reboot the server, 2 of 10 times the boot procedure stops... 

Is this an mdadm os a kernel bug? Or what should be this problem?

---

### Post by rubylaser on 2012-07-25
> **pdnv said:**
> Hi!

My config is the following: Lenovo M58 with two WD320 HDDs.
I've installed 64 bit Ubuntu Server 12.04 with software raid (RAID1).

My problem is that sometimes the server stops the booting procedure after grub and it takes me to the initramfs console. If I press CTRL-D the boot process continues and everything is OK.

I found the following differences in dmesg:

When it's OK - It's OK for all MD devices (md0-md10):

[    1.799536] md: bind<sda12>
    [    1.802215] bio: create slab <bio-1> at 1
    [    1.802319] md/raid1:md10: active with 2 out of 2 mirrors
    [    1.802339] md10: detected capacity change from 0 to 111970336768
    [    1.807616] md: bind<sda1>
    [    1.809052] md/raid1:md0: active with 2 out of 2 mirrors
    [    1.809070] md0: detected capacity change from 0 to 9998098432
    [    1.812797] md: bind<sda7>
    [    1.814201] md/raid1:md5: active with 2 out of 2 mirrors
    [    1.814221] md5: detected capacity change from 0 to 9998098432
    [    1.823587] md: bind<sda8>

ERROR - It says this** unknown partition table** thing for all MD devices (md0-10) :

[    1.956170] md: bind<sda5>
    [    1.957628] bio: create slab <bio-1> at 1
    [    1.957719] md/raid1:md3: active with 2 out of 2 mirrors
    [    1.957776] md3: detected capacity change from 0 to 9998098432
    [    1.975224]  **md3: unknown partition table**
    [    1.984179] md: bind<sda1>
    [    1.985810] md/raid1:md0: active with 2 out of 2 mirrors
    [    1.985871] md0: detected capacity change from 0 to 9998098432
    [    2.053296]  **md0: unknown partition table**
    [    2.060182] md: bind<sda12>
    [    2.061861] md/raid1:md10: active with 2 out of 2 mirrors
    [    2.061922] md10: detected capacity change from 0 to 111970336768
    [    2.137478]  **md10: unknown partition table**
    
If I reboot the server, 2 of 10 times the boot procedure stops... 

Is this an mdadm os a kernel bug? Or what should be this problem?

Unless, you added a partition to each of your arrays with LVM when you did your install, the lack of partitions is probably not the issue (it would be an issue all the time, not sometimes).  Most directions that demonstrate installing on mdadm with RAID1 and swap on RAID1 do not setup partitions.  You can check that by looking at these.
```
fdisk -l
```
```
df -h
```
or
```
mount
```

Can you provide the whole output of dmesg instead of only the portion you've provided?

---


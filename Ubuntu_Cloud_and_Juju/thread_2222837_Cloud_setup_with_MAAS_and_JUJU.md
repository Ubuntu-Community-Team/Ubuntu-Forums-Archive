---
title: "Cloud setup with MAAS and JUJU"
date: 2014-05-08
forum: Ubuntu Cloud and Juju
---

### Post by revanth2 on 2014-05-08
HI,

I am doing POC for cloud setup with MAAS and JUJU so I can install later open stack icehouse.
I am doing this in vmware workstation , MAAS controller is unable to control power type for the nodes , could someone please tell me which option i need to select.

I have to start the nodes manually , not sure this is right way to do. After MAAS set up I will test with juju and finally I will install open stack icehouse .

Is there any other way to do easily or this is the way to do it.??

If POC is success I will install in physical servers.

Please guide me.

Thanks a lot.

Cheers,
Revanth

---

### Post by revanth2 on 2014-05-17
I am getting below error

nova-volume/0:
        agent-state: error
        agent-state-info: 'hook failed: "install"'


 I have checked the logs it is showing "nova-volume ERROR: /dev/xvdb is not a valid block device"

But when I checked there is block device there is nova xvdb

sudo fdisk -l


Disk /dev/sda: 42.9 GB, 42949672960 bytes
255 heads, 63 sectors/track, 5221 cylinders, total 83886080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007a39c


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    82837503    41417728   83  Linux
/dev/sda2        82839550    83884031      522241    5  Extended
/dev/sda5        82839552    83884031      522240   82  Linux swap / Solaris


Kindly tell me where I am missing I am in deep trouble please help me

---


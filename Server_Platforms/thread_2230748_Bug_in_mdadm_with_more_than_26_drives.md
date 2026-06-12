---
title: "Bug in mdadm with more than 26 drives?"
date: 2014-06-20
forum: Server Platforms
---

### Post by kmcclure on 2014-06-20
What is causing all drives between /dev/sdc to /dev/sdz to loose their raid metadata on reboot?  

I've been looking for an answer to my issue, but haven't had any luck yet.  My company has always used hardware raid for our storage servers.  Now management is asking me to set up large system using software raid.  I have a server with two boot drives and 36 4TB data drives.  I made two 18-drive raid6 volumes using the following commands:

mdadm --create --verbose /dev/md/3 --metadata 1.2 --level=6 --layout=left-symmetric --chunk=256 --raid-devices=18 /dev/sdc /dev/sdd /dev/sde /dev/sdf /dev/sdg /dev/sdh /dev/sdi /dev/sdj /dev/sdk /dev/sdl /dev/sdm /dev/sdn /dev/sdo /dev/sdp /dev/sdq /dev/sdr /dev/sds /dev/sdt

mdadm --create --verbose /dev/md/4 --metadata 1.2 --level=6 --layout=left-symmetric --chunk=256 --raid-devices=18 /dev/sdu  /dev/sdv /dev/sdw /dev/sdx /dev/sdy /dev/sdz /dev/sdaa  /dev/sdab /dev/sdac /dev/sdad /dev/sdae /dev/sdaf /dev/sdag /dev/sdah /dev/sdai /dev/sdaj /dev/sdak /dev/sdal


They initialized normally.  Then I partitioned md3 and md4 with gdisk, creating a single partition on each volume.  I formatted them with the following commands:

mkfs -t ext4 -v -b 4096 -E stride=64,stripe-width=1024 /dev/md3p1
mkfs -t ext4 -v -b 4096 -E stride=64,stripe-width=1024 /dev/md4p1

I mounted the volumes and /storage/md3 and /storage/md4 and put some test data on them and all was well.  Everything went well to this point.  I saved the raid info with this command:

mdadm --detail --scan >> /etc/mdadm/mdadm.conf


After reboot, neither md3 or md4 came up.  mdadm --query --detail /dev/md4 showed:
mdadm: md device /dev/md4 does not appear to be active.

/dev/md3 is completely gone after the reboot, no entries in /dev, no mdadm commands return any information.
/etc/mdadm/mdadm.conf showed the following:
# This file was auto-generated on Tue, 17 Jun 2014 19:08:14 +0200
# by mkconf $Id$
ARRAY /dev/md/1 metadata=1.2 name=storage74:1 UUID=1bdb821b:4d2c1826:5f4a01cd:dd26e1df
ARRAY /dev/md/0 metadata=1.2 name=storage74:0 UUID=432bbb98:6c010f30:d3b0fc11:96af1f97
ARRAY /dev/md/3 metadata=1.2 name=storage74:3 UUID=2727aaeb:6a15d5a9:98347282:eda1eacc
ARRAY /dev/md/4 metadata=1.2 name=storage74:4 UUID=bc5b34c3:fec59821:b2e70f3f:6ff4fc53



cat /proc/mdstat showed the following:
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md4 : inactive sdac[8](S) sdai[14](S) sdab[7](S) sdaj[15](S) sdah[13](S) sdal[17](S) sdak[16](S) sdaa[6](S) sdag[12](S) sdaf[11](S) sdad[9](S) sdae[10](S)
      46882650144 blocks super 1.2

md0 : active raid1 sdb1[1] sda1[0]
      224476992 blocks super 1.2 [2/2] [UU]

md1 : active raid1 sdb2[1] sda2[0]
      15616896 blocks super 1.2 [2/2] [UU]

unused devices: <none>  




All drives from /dev/sdc to /dev/sdz showd the following information:
mdadm -E /dev/sdm
/dev/sdm:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)


All drives from /dev/sdaa to /dev/sdal showed this information:
mdadm -E /dev/sdaj
/dev/sdaj:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : bc5b34c3:fec59821:b2e70f3f:6ff4fc53
           Name : storage74:4  (local to host storage74)
  Creation Time : Thu Jun 19 22:22:54 2014
     Raid Level : raid6
   Raid Devices : 18

 Avail Dev Size : 7813775024 (3725.90 GiB 4000.65 GB)
     Array Size : 62510194688 (59614.37 GiB 64010.44 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 2d432360:7a6c197d:dfd99696:24400e3c

    Update Time : Fri Jun 20 22:58:56 2014
       Checksum : c5cf9145 - correct
         Events : 19

         Layout : left-symmetric
     Chunk Size : 256K

   Device Role : Active device 15
   Array State : AAAAAAAAAAAAAAAAAA ('A' == active, '.' == missing)



What is causing all drives between /dev/sdc to /dev/sdz to loose their raid metadata on reboot?  At one point, I had a three-drive raid5 on /dev/sdaj, /dev/sdak, and /dev/sdal, and it survived reboots with the exact same setup, where the volume on /dev/sdc through /dev/sdt did not.  Any ideas will be helpful.

---

### Post by Gyokuro on 2014-06-22
Hi

Maybe I have overlooked something but I can not find which Ubuntu release are you using and whether you are using GPT partitions which is a must with such an amount of space. Another problem is that for 48TB I would choose XFS due to it's much better tested with large disk space as one of the old rules is to use ext4 => 16TB (I was unable to find out the current supported file system size in Ubuntu - RHEL supports with release 6 16TB ext3/4 - 100TB XFS, RHEL7 50TB ext4 - 500TB XFS). I have glanced over your commands and maybe you forgot to enter your disk settings in /etc/mdadm/mdadm.conf so that your system knows how to assemble the RAID after a reboot and the next step is to update initramfs via: sudo update-initramfs -u 

- HTH

---

### Post by davismarkc on 2014-06-24
+1 on the "sudo update-initramfs -u"   If you don't do that then mdadm during boot uses the old mdadm.conf and that can give you unpredictable results.

By the way, I would love to see "cat /proc/mdstat" output.  Maybe there is a "/dev/md127" hiding in there.

---

### Post by rubylaser on 2014-06-24
The original poster did include cat /proc/mdstat. Here is what he had.
```

cat /proc/mdstat showed the following:
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md4 : inactive sdac[8](S) sdai[14](S) sdab[7](S) sdaj[15](S) sdah[13](S) sdal[17](S) sdak[16](S) sdaa[6](S) sdag[12](S) sdaf[11](S) sdad[9](S) sdae[10](S)
46882650144 blocks super 1.2


md0 : active raid1 sdb1[1] sda1[0]
224476992 blocks super 1.2 [2/2] [UU]


md1 : active raid1 sdb2[1] sda2[0]
15616896 blocks super 1.2 [2/2] [UU]


unused devices: <none> 

```

I would definitely update your initramfs first.  Also, you can remove the name portion in each device line of your /etc/mdadm/mdadm.conf file.  It's not required for proper assembly and occasionally causes problems without providing any real benefit. It would look like this...
```

# This file was auto-generated on Tue, 17 Jun 2014 19:08:14 +0200
# by mkconf $Id$
ARRAY /dev/md/1 metadata=1.2 UUID=1bdb821b:4d2c1826:5f4a01cd:dd26e1df
ARRAY /dev/md/0 metadata=1.2 UUID=432bbb98:6c010f30:d3b0fc11:96af1f97
ARRAY /dev/md/3 metadata=1.2 UUID=2727aaeb:6a15d5a9:98347282:eda1eacc
ARRAY /dev/md/4 metadata=1.2 UUID=bc5b34c3:fec59821:b2e70f3f:6ff4fc53

```

Also, there is no reason to put partitions on top of a mdadm device.  You typically would just use the raw block device for your filesystem. Another note is that ext4 can work fine with filesystems >16TB, but you need to pass the -O 64bit option when you create the filesystem like this.

```

mkfs.ext4 -O 64bit /dev/md0

```

That being said, I would consider using XFS on this array instead, or even consider using ZFS on Linux as discussed below to take advantage of triple parity on your array.
[COLOR=#000000]
[/COLOR]As a final note, with more than (14) 4TB disks in any array, I would really start considering breaking it down into smaller RAID6's.  Ideally, at 18 large disks, you would be using triple parity (RAID7) or in ZFS speak RAIDz3. Unfortunately, at this time, mdadm does not support triple parity.  This is just food for thought, and with a solid backup strategy, any double URE error risk is mitigated.

P.S. I'd love to see some pictures.  I really enjoy larger storage projects :p

---

### Post by lukeiamyourfather on 2014-06-25
I would definitely recommend ZFS with that many drives and either break it up into multiple VDEV or use triple parity RAID (multiple VDEV would still be in the same namespace). ZFS is just safer and easier to manage with that many drives. Especially if you configure vdev_id.conf in a meaningful way. For what it's worth I'm running ZFS on Linux on several machines with 36 drives each.

[http://zfsonlinux.org/faq.html#HowDoISetupVdevIdConf](http://zfsonlinux.org/faq.html#HowDoISetupVdevIdConf)

---

### Post by kmcclure on 2014-06-25
Thanks for all of the replies.  I resolved the issue by putting the raid on the partitions instead of directly on the drives.   I changed my commands to create the volumes as follows

mdadm --create --verbose /dev/md/2 --metadata 1.2 --level=6 --layout=left-symmetric --chunk=256 --raid-devices=18 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1 /dev/sdi1 /dev/sdj1 /dev/sdk1 /dev/sdl1 /dev/sdm1 /dev/sdn1 /dev/sdo1 /dev/sdp1 /dev/sdq1 /dev/sdr1 /dev/sds1 /dev/sdt1

mdadm --create --verbose /dev/md/3 --metadata 1.2 --level=6 --layout=left-symmetric --chunk=256 --raid-devices=18 /dev/sdu1  /dev/sdv1 /dev/sdw1 /dev/sdx1 /dev/sdy1 /dev/sdz1 /dev/sdaa1 /dev/sdab1 /dev/sdac1 /dev/sdad1 /dev/sdae1 /dev/sdaf1 /dev/sdag1 /dev/sdah1 /dev/sdai1 /dev/sdaj1 /dev/sdak1 /dev/sdal1

This machine is a basic supermicro 4U chassis with 36 3.5" bays loaded with 4TB enterprise drives.  So it has 56TB of formatted disk space on each of it's two volumes.  We have multiple machines running ubuntu 12.04 (including this one) that have anywhere from 35TB to 60TB volumes.  All have EXT4 with no issues and Ubuntu by default uses the -O 64 bit option (at least I never had to specify it to work).  This is just the first one with software raid.

Questions:
1.  Even though I ran the mdadm --detail --scan >> /etc/mdadm/mdadm.conf command, which updates the existing mdadm.conf file, do I still need to run update-initramfs -u ?  So far, the system has been through multiple reboots and power-offs and hasn't had any issues with the disappearing volumes since I put the md volume on the partitions.

2.  Typically when running the mdadm --create command to make a raid volume, am I understanding that it will usually be something like this (no partition use):

mdadm --create --verbose /dev/md/3 --metadata 1.2 --level=6  --layout=left-symmetric --chunk=256 --raid-devices=18 /dev/sdc /dev/sdd  /dev/sde /dev/sdf /dev/sdg /dev/sdh /dev/sdi /dev/sdj /dev/sdk /dev/sdl  /dev/sdm /dev/sdn /dev/sdo /dev/sdp /dev/sdq /dev/sdr /dev/sds /dev/sdt

and not this (using partitions):

mdadm --create --verbose /dev/md/3 --metadata 1.2 --level=6 --layout=left-symmetric --chunk=256 --raid-devices=18 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1 /dev/sdi1 /dev/sdj1 /dev/sdk1 /dev/sdl1 /dev/sdm1 /dev/sdn1 /dev/sdo1 /dev/sdp1 /dev/sdq1 /dev/sdr1 /dev/sds1 /dev/sdt1

Thanks!

---

### Post by rubylaser on 2014-06-25
> **kmcclure said:**
> Thanks for all of the replies.  I resolved the issue by putting the raid on the partitions instead of directly on the drives.   I changed my commands to create the volumes as follows

mdadm --create --verbose /dev/md/2 --metadata 1.2 --level=6 --layout=left-symmetric --chunk=256 --raid-devices=18 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1 /dev/sdi1 /dev/sdj1 /dev/sdk1 /dev/sdl1 /dev/sdm1 /dev/sdn1 /dev/sdo1 /dev/sdp1 /dev/sdq1 /dev/sdr1 /dev/sds1 /dev/sdt1

mdadm --create --verbose /dev/md/3 --metadata 1.2 --level=6 --layout=left-symmetric --chunk=256 --raid-devices=18 /dev/sdu1  /dev/sdv1 /dev/sdw1 /dev/sdx1 /dev/sdy1 /dev/sdz1 /dev/sdaa1 /dev/sdab1 /dev/sdac1 /dev/sdad1 /dev/sdae1 /dev/sdaf1 /dev/sdag1 /dev/sdah1 /dev/sdai1 /dev/sdaj1 /dev/sdak1 /dev/sdal1

This machine is a basic supermicro 4U chassis with 36 3.5" bays loaded with 4TB enterprise drives.  So it has 56TB of formatted disk space on each of it's two volumes.  We have multiple machines running ubuntu 12.04 (including this one) that have anywhere from 35TB to 60TB volumes.  All have EXT4 with no issues and Ubuntu by default uses the -O 64 bit option (at least I never had to specify it to work).  This is just the first one with software raid.

Questions:
1.  Even though I ran the mdadm --detail --scan >> /etc/mdadm/mdadm.conf command, which updates the existing mdadm.conf file, do I still need to run update-initramfs -u ?  So far, the system has been through multiple reboots and power-offs and hasn't had any issues with the disappearing volumes since I put the md volume on the partitions.

2.  Typically when running the mdadm --create command to make a raid volume, am I understanding that it will usually be something like this (no partition use):

mdadm --create --verbose /dev/md/3 --metadata 1.2 --level=6  --layout=left-symmetric --chunk=256 --raid-devices=18 /dev/sdc /dev/sdd  /dev/sde /dev/sdf /dev/sdg /dev/sdh /dev/sdi /dev/sdj /dev/sdk /dev/sdl  /dev/sdm /dev/sdn /dev/sdo /dev/sdp /dev/sdq /dev/sdr /dev/sds /dev/sdt

and not this (using partitions):

mdadm --create --verbose /dev/md/3 --metadata 1.2 --level=6 --layout=left-symmetric --chunk=256 --raid-devices=18 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1 /dev/sdi1 /dev/sdj1 /dev/sdk1 /dev/sdl1 /dev/sdm1 /dev/sdn1 /dev/sdo1 /dev/sdp1 /dev/sdq1 /dev/sdr1 /dev/sds1 /dev/sdt1

Thanks!

Putting mdadm on disks with partitions or the raw disks are both okay.  I usually put mdadm on the disk partitions.  I would make the array like this to make your create statement shorter.
```

mdadm --create --verbose /dev/md3 --level=6 --raid-devices=18 --chunk=256 /dev/sd[cdefghighijklmnopqrst]1

```
You don't need a parition on top of the mdadm device though.  Also, it's always a good idea to run update-initramfs -u after you create your new mdadm.conf file.  Running it won't hurt your working setup.

Finally, ext4 works fine with larger volumes, but it's always good to pass the -O 64bit option, because on older versions of 12.04 or Ubuntu, the version of e2fsprogs does not create 64 bit filesystems by default.  This way you will *know* that the filesystem is 64 bit :)

---

### Post by kmcclure on 2014-06-26
Thanks for the Clarification!

---

### Post by Tadaen_Sylvermane on 2014-06-27
> [COLOR=#000000]P.S. I'd love to see some pictures. I really enjoy larger storage projects [/COLOR]:razz:

First thing I thought of to. It's like nerd porn. Servers / Mass storage / Datacenters... can't get enough.

---

### Post by lukeiamyourfather on 2014-06-30
> **Tadaen_Sylvermane said:**
> First thing I thought of to. It's like nerd porn. Servers / Mass storage / Datacenters... can't get enough.

It sounds like I'm using similar hardware to the original poster so maybe this will appease you.

[https://plus.google.com/photos/107506047335554701913/albums/5987426031524373521](https://plus.google.com/photos/107506047335554701913/albums/5987426031524373521)

---


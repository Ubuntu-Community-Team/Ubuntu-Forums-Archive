---
title: "HA iSCSI Questions"
date: 2009-06-16
forum: Server Platforms
---

### Post by Gibby82 on 2009-06-16
Greetings. I'm currently working on putting together a Win2003/iSCSI setup and need some assistance with the iSCSI portion. 

In this article: [https://help.ubuntu.com/community/HighlyAvailableiSCSITarget](https://help.ubuntu.com/community/HighlyAvailableiSCSITarget)

..it mentions DRBD, but uses it in a virtual environment. I'd like to do this, but with two physical servers:

--iSCSI storage server--
Dual Xeon 2.8 (single core w/HT)
2GB memory (can be increased)
2 Gb NIC's on each server (Intel)
Adaptec 2820sa connected to 4 WD2500YS drives, in RAID 5. 
100M Boot
4096 Swap
100GB /
600GB /Storage
--------------------


There would be two Win2003 servers that are load balanced/clustered, with 1Gb links to a Gb switch, then one of the 1Gb links on the iSCSI servers would connect to the same switch. The other two would be crossed over for DRBD.

My questions are:

1. Would this work?

2. Is there some documentation on DRBD between two physical servers?

---

### Post by Gibby82 on 2009-06-17
Anyone?

---

### Post by huy_vu on 2009-12-02
I used the instructions described in 
[https://help.ubuntu.com/community/HighlyAvailableiSCSITarget](https://help.ubuntu.com/community/HighlyAvailableiSCSITarget)
as a guide and used  2xHP DL-360s, each with 2x72Gig scsi drives.

IP address scheme:
node1: 192.168.10.16 (SAN)
node1: 10.38.181.16 (heartbeat)
node2: 192.168.10.18 (SAN)
node2: 10.38.181.18 (heartbeat)
 
Here is what I did:
1. For each server, I RAIDed the 2 drives to produce a 144 Gig RAID drive
2. I installed Ubuntu 9.04 on each server on a 40GB partition and 2 GB swap space.
    The remaining 100GB was set aside for the iscsi target
3. I did not do the NIC bonding as per instructions
4. I did not use the 3 partitions for DRBD as described in the instructions;
    opting for just one partition to back the DRBD. Here 's what fdisk -l shows:

vuh@vuh-iscsi1:/etc/heartbeat$ sudo fdisk -l

Disk /dev/cciss/c0d0: 145.6 GB, 145667358720 bytes
255 heads, 63 sectors/track, 17709 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002790a

           Device Boot      Start         End      Blocks   Id  System
/dev/cciss/c0d0p1   *           1        4863    39062016   83  Linux
/dev/cciss/c0d0p2            4864       17709   103185495    5  Extended
/dev/cciss/c0d0p5            4864        5106     1951866   82  Linux swap / Solaris
/dev/cciss/c0d0p6            5107       17709   101233566   83  Linux

Partition c0d0p6 is going to be the backing partition for DRBD.

5. I got drbd to work and got the drbd device /dev/drbd0. See attached drbd.conf.
6. Then I got iscsi target to serve it up. See attached ietd.conf. I did not put a file
     system on it before serving it up as per instructions. I just served it as a raw
     block device.
7. I got heartbeat to work also. See attached ha.cf and haresourses
8. I installed open-iscsi on another machine (a laptop running ubuntu 9.04) and
    connected to the iscsi target. I installed lsscsi and found it  useful. It lists the
    iscsi devices the host has. Here is the output on my laptop running open-iscsi.

[0:0:0:0]    disk    ATA      FUJITSU MHV2040A 0000  /dev/sda
[1:0:0:0]    cd/dvd  TSSTcorp DVD+-RW TS-L532B DE04  /dev/sr0
[4:0:0:0]    disk    IET      VIRTUAL-DISK     0     /dev/sdb
[5:0:0:0]    disk    IET      VIRTUAL-DISK     0     /dev/sdd

The last scsi device (/dev/sdd) is the target from my DRBD servers.

9. Made a partition on /dev/sdd and put a jfs file system on it and mounted it
    as /mnt/iscsi
10. I tested the failover by playing an mp3 file in /mnt/iscsi while failing over the
      DRBD servers. This went well.

Here is the bad part. Instead of playing the mp3 file I started a large file copy. While the
cp command was running, I did a failover of the DRBD servers, the whole iscsi initiator computer (the laptop) just froze solid. I suspect this has to do with the iscsi client and nothing to do with the iscsi target or DRBD. More testing will tell the whole story.

---

### Post by optimuslobo on 2013-01-14
I have been trying to follow this guide but no luck so far with the failover part, I got the iscsi and replication working but if i shut down node1 then node2 doesn't get into action, as far I understand thats the way is supposes to work, node1 goes down then node2 goes up and the iscsi service keep running right?

---


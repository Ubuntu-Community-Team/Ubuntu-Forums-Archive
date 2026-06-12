---
title: "Extremely Slow Network Write RAID 6 mdadm"
date: 2014-10-22
forum: Server Platforms
---

### Post by neorush on 2014-10-22
I am running mdadm raid 6 and while speed was not paramount as we are after raw storage volume, the write numbers are painfully slow.  In the neighborhood of 800kb/s on a gigabyte lan connection.  The crazy thing is that locally writing to the drive is quite fast:
```

~$ sudo dd if=/dev/zero of=/media/raid6/test bs=1G count=10;
10+0 records in
10+0 records out
10737418240 bytes (11 GB) copied, 25.3465 s, 424 MB/s
OR
~$ sudo dd if=/dev/zero of=/media/raid6/test bs=1M count=1000;
1000+0 records in
1000+0 records out
1048576000 bytes (1.0 GB) copied, 2.16628 s, 484 MB/s

```
It is ONLY over the network that is slows to a crawl.  Tested over Samba and SFTP so it is not one protocol.
mdadm info:
```

sudo mdadm --detail /dev/md127 
/dev/md127:
        Version : 1.2
  Creation Time : Tue Oct  7 15:54:19 2014
     Raid Level : raid6
     Array Size : 11720655360 (11177.69 GiB 12001.95 GB)
  Used Dev Size : 3906885120 (3725.90 GiB 4000.65 GB)
   Raid Devices : 5
  Total Devices : 5
    Persistence : Superblock is persistent

    Update Time : Wed Oct 22 18:45:12 2014
          State : clean 
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : blueline:0  (local to host blueline)
           UUID : e307b911:b4b2b45d:f709b052:bd957d20
         Events : 152233

    Number   Major   Minor   RaidDevice State
       5       8       33        0      active sync   /dev/sdc1
       6       8       49        1      active sync   /dev/sdd1
       2       8       65        2      active sync   /dev/sde1
       3       8       81        3      active sync   /dev/sdf1
       4       8       97        4      active sync   /dev/sdg1

cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md127 : active raid6 sdg1[4] sde1[2] sdd1[6] sdf1[3] sdc1[5]
      11720655360 blocks super 1.2 level 6, 512k chunk, algorithm 2 [5/5] [UUUUU]
      
unused devices: <none>


```
Other Drives
```

df -h
Filesystem                         Size  Used Avail Use% Mounted on
/dev/mapper/isw_ffhghdabj_System1   55G  9.4G   43G  18% /
none                               4.0K     0  4.0K   0% /sys/fs/cgroup
udev                               1.8G  4.0K  1.8G   1% /dev
tmpfs                              363M  2.8M  360M   1% /run
none                               5.0M     0  5.0M   0% /run/lock
none                               1.8G     0  1.8G   0% /run/shm
none                               100M     0  100M   0% /run/user
/dev/md127                          11T  3.9T  6.5T  38% /media/raid6


```

Network Info
```

sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: Symmetric Receive-only
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: Symmetric
	Advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Current message level: 0x000060e4 (24804)
			       link ifup rx_err tx_err hw wol
	Link detected: yes

```

I have tried all sorts of things with max_stripe_size and other mdadm settings, but given the dd test is good I'm thinking it has to be something else.  Thank you for any help!

---

### Post by lukeiamyourfather on 2014-10-23
Try enabling asynchronous writes for Samba if you haven't yet (i.e. aio write size = 16384).

---

### Post by Forbees on 2014-10-23
could be something as simple as the networking infrastructure. 1000baseT puts you at 1000Mb/s which turns into 125MB/s (assuming no other network activity is going on) - how slow of network transfers are we talking?

how many other computers are on this network? could be a switch or router causing the problem too. cheaper ones even though they might have 5 gigabit ports on it will still only have a gigabit backbone, so you'll never get gigabit speeds on more than one port at a time

needless to say unless you jump to a 10gigabit infrastructure you'll never see anything near that nice 424 MB/s you get locally.

---


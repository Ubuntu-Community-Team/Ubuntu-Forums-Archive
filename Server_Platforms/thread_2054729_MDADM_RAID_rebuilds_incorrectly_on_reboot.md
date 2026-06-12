---
title: "MDADM RAID rebuilds incorrectly on reboot"
date: 2012-09-07
forum: Server Platforms
---

### Post by ownaginatious on 2012-09-07
So my computer has four 1.5 TB drives installed. Up until recently, these drives existed in two RAID1 configurations of 3 TB.

Recently I decided to create one large RAID5 device out of them instead. I did this remotely, and had no spare drive to dump data to - so I disassembled one of the RAIDs (it was just a backup of the other from a few weeks back) and since the RAID contained under 1.5 TB of data - I created a partition on one of the disks and stored it there.

So I created the RAID5 in a degraded mode with only 3 disks and copied the data back on to the new 4.5 TB RAID. After that, I added in the remaining disk that had been holding the data throughout the backup process to the RAID and let it rebuild over a few hours.

This is what the configuration looked like:

```
[root@FILEMASTER administrator]# cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4]
md0 : active raid5 sdb1[0] sdd1[4] sde1[2] sdc1[1]
      4395016704 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]

unused devices: <none>

```

So I updated my mdadm.conf file and rebooted. Now it appears the disks assemble incorrectly on reboot...

```
[root@FILEMASTER administrator]# cat /proc/mdstat
Personalities :
md0 : inactive sde1[2](S) sdb1[0](S) sdc1[1](S)
      4395018240 blocks super 1.2

md127 : inactive sdd[0](S)
      1465138496 blocks

```

I can fix it by simply dismantling the md0 and md127 arrays and then running ```
mdadm --assemble --scan
```

Obviously though, this is inconvenient - and I would prefer the RAID be built properly at boot.

Anyone have any insight on how I would fix this?

Thanks.

P.S. /dev/sdd was the 'spare' disk I added after.

---

### Post by rubylaser on 2012-09-08
You need to update your your mdadm.conf file after you make changes like this.  Once you have your array running properly just run these steps.

```
sudo -i
```

```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST fileserver" >> /etc/mdadm/mdadm.conf
echo "MAILADDR youruser@gmail.com" >> /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

```
update-initramfs -u
```

This will update your mdadm.conf file to reflect your RAID5 array and will update the initramfs.  This should allow your array to survive a reboot.

---


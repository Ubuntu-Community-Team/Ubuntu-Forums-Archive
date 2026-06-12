---
title: "Slow performance with mdadm RAID 5"
date: 2017-01-11
forum: Server Platforms
---

### Post by jordelver on 2017-01-11
Hi,
I'm experiencing (what I think is) very slow performance with my mdadm RAID 5 array.

I'm just about scraping by with my mdadm / disk knowledge, so please be kind :)

I've tested performance using bonnie++. I don't really know what I'm doing with bonnie++ (I found and copied a tutorial) but here are the results:

```
$ bonnie++ -d /media/raid/tmp -s 8G -n 0 -m RAID -f -b
```

[IMG]https://dl.dropboxusercontent.com/s/neh7w3ubsdm2z1t/2017-01-11%20at%2022.56.png[/IMG]

I ran this on both my RAID array and on the OS (SSD) disk. I know the SSD is going to be faster but I thought it might be interesting for comparison).

Here is the output of /proc/mdstat

```
$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md127 : active raid5 sda1[2] sdc1[0] sdf1[5] sdb1[3] sdd1[4] sde1[1]
      7325679680 blocks level 5, 64k chunk, algorithm 2 [6/6] [UUUUUU]

unused devices: <none>
```

As you can see, I'm using 6 disks. They are uneven sizes as I'm gradually phasing disks out to be replaced with bigger.

The array is formatted using XFS.

Here are is the output from various commands I thought might be useful:

```
$ lshw -class disk

  *-disk
       description: ATA Disk
       product: WDC WD20EFRX-68E
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 0A82
       serial: WD-WCC4M1HCFCKV
       size: 1863GiB (2TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=4096 signature=594710dd
  *-disk
       description: ATA Disk
       product: SAMSUNG HD154UI
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sdb
       version: 1118
       serial: S1Y6J1KS516328
       size: 1397GiB (1500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512
  *-disk
       description: ATA Disk
       product: SAMSUNG HD154UI
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdc
       version: 1118
       serial: S1XWJDWZ404208
       size: 1397GiB (1500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512
  *-disk
       description: ATA Disk
       product: ST2000DM001-1CH1
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sdd
       version: CC27
       serial: W1E44GKL
       size: 1863GiB (2TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=4096 signature=f7d64173
  *-disk
       description: ATA Disk
       product: SAMSUNG HD154UI
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sde
       version: 1118
       serial: S1XWJDWZ404207
       size: 1397GiB (1500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512
  *-disk
       description: ATA Disk
       product: WDC WD20EFRX-68E
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/sdf
       version: 0A82
       serial: WD-WCC4M4XHPC3H
       size: 1863GiB (2TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=4096 signature=1acbec36
  *-disk
       description: ATA Disk
       product: M4-CT128M4SSD2
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sdg
       version: 070H
       serial: 000000001144031DB84A
       size: 119GiB (128GB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=5 guid=9c769bc1-9c80-4ad1-baa9-24100e74cd51 sectorsize=512

```


```
$ lsblk

NAME      MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda         8:0    0   1.8T  0 disk  
&#9492;&#9472;sda1      8:1    0   1.8T  0 part  
  &#9492;&#9472;md127   9:127  0   6.8T  0 raid5 /media/raid
sdb         8:16   0   1.4T  0 disk  
&#9492;&#9472;sdb1      8:17   0   1.4T  0 part  
  &#9492;&#9472;md127   9:127  0   6.8T  0 raid5 /media/raid
sdc         8:32   0   1.4T  0 disk  
&#9492;&#9472;sdc1      8:33   0   1.4T  0 part  
  &#9492;&#9472;md127   9:127  0   6.8T  0 raid5 /media/raid
sdd         8:48   0   1.8T  0 disk  
&#9492;&#9472;sdd1      8:49   0   1.8T  0 part  
  &#9492;&#9472;md127   9:127  0   6.8T  0 raid5 /media/raid
sde         8:64   0   1.4T  0 disk  
&#9492;&#9472;sde1      8:65   0   1.4T  0 part  
  &#9492;&#9472;md127   9:127  0   6.8T  0 raid5 /media/raid
sdf         8:80   0   1.8T  0 disk  
&#9492;&#9472;sdf1      8:81   0   1.8T  0 part  
  &#9492;&#9472;md127   9:127  0   6.8T  0 raid5 /media/raid
sdg         8:96   0 119.2G  0 disk  
&#9500;&#9472;sdg1      8:97   0   512M  0 part  /boot/efi
&#9500;&#9472;sdg2      8:98   0 114.8G  0 part  /
&#9492;&#9472;sdg3      8:99   0     4G  0 part  [SWAP]

```


```
$ parted -l
 
Model: ATA WDC WD20EFRX-68E (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary               raid


Model: ATA SAMSUNG HD154UI (scsi)
Disk /dev/sdb: 1500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1500GB  1500GB  primary               raid


Model: ATA SAMSUNG HD154UI (scsi)
Disk /dev/sdc: 1500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1500GB  1500GB  primary               raid


Model: ATA ST2000DM001-1CH1 (scsi)
Disk /dev/sdd: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  2000GB  2000GB  primary               raid


Model: ATA SAMSUNG HD154UI (scsi)
Disk /dev/sde: 1500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1500GB  1500GB  primary               raid


Model: ATA WDC WD20EFRX-68E (scsi)
Disk /dev/sdf: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary               raid


Model: ATA M4-CT128M4SSD2 (scsi)
Disk /dev/sdg: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system     Name  Flags
 1      1049kB  538MB  537MB   fat32                 boot
 2      538MB   124GB  123GB   ext4
 3      124GB   128GB  4271MB  linux-swap(v1)


Model: Linux Software RAID Array (md)
Disk /dev/md127: 7501GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  7501GB  7501GB  xfs

```

```
$ cat /etc/mdadm/mdadm.conf
DEVICE partitions
ARRAY /dev/md0 metadata=0.90 UUID=f51f02cd:3b5c9fa9:a40e4b4e:93ecf45d name=0

MAILADDR root
```

I'm running Ubuntu 14.04.4 LTS.

I'm not sure where to start. Any ideas are welcome :)

Thanks in advance.

Cheers,
Jordan

---

### Post by TheFu on 2017-01-12
[https://serverfault.com/questions/373563/linux-real-world-hardware-raid-controller-tuning-scsi-and-cciss](https://serverfault.com/questions/373563/linux-real-world-hardware-raid-controller-tuning-scsi-and-cciss)
I've done something like this on my array. 10%-100% improvements were possible.

---

### Post by jordelver on 2017-01-13
Thank you. I'll give it a read :)

---


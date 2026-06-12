---
title: "Getting my drive back into md"
date: 2023-08-04
forum: Server Platforms
---

### Post by pqwoerituytrueiwoq on 2023-08-04
Noticed my drive dropped from the array, i pulled the drive and ran SMART test on it and it passed (did not run the 8 hour test...)

```
[FONT=monospace][COLOR=#000000]$ cat /proc/mdstat [/COLOR]
Personalities : [raid1] [raid10] [linear] [multipath] [raid0] [raid6] [raid5] [raid4]  
md2 : active raid10 sdg[1](F) sdh[3] sde[2] sdf[0] 
      7813772288 blocks super 1.2 512K chunks 2 near-copies [4/3] [U_UU] 
      bitmap: 12/59 pages [48KB], 65536KB chunk 

md0 : active raid1 sda2[1] sdb2[0] 
      124965888 blocks super 1.2 [2/2] [UU] 
      bitmap: 1/1 pages [4KB], 65536KB chunk 

md1 : active raid1 sdd1[1] sdc1[0] 
      124966912 blocks super 1.2 [2/2] [UU] 
      bitmap: 1/1 pages [4KB], 65536KB chunk
[/FONT]
```

ran this: ```
[FONT=monospace][COLOR=#000000]sudo mdadm --manage /dev/md2 --add /dev/sdg[/COLOR][/FONT]
```

how do i have it try to fix the drive's data it had some i/o errors (probably the controller being a pos[FONT=monospace][COLOR=#000000]: JMicron Technology Corp. JMB58x AHCI SATA controller[/COLOR][/FONT]) but maybe it is a sata cable?

---

### Post by darkod on 2023-08-04
I didn't understand, is the drive and controller and sata cable all good now? That is the first thing you would need to check.

If all of that is fine, there should be no issues adding the drive back.

I see sdg is in failed state (the (F) mark). Maybe you will need to remove it and add it again.
```
sudo mdadm /dev/md2 --remove /dev/sdg
sudo mdadm /dev/md2 --add /dev/sdg
```

And also some advice for the future. It is better to use partitions, not the disk itself. When preparing mdadm create one big partition on the whole disk and use that as member of the array. For example, sdg1 instead of sdg.

---

### Post by pqwoerituytrueiwoq on 2023-08-04
I think it is good, so i was trying to see if i could get it working (i unplugged the hdd from the hot swap bay and put it back in and it showed up and looked like it should work and checked the smart data)

i rebooted

still was not working so i pulled the drve and put it in my desktop and ram smart test and they passed

can i just wipe out the partition table and then try to add it again?

```
[FONT=monospace][COLOR=#000000]$ sudo mdadm --manage /dev/md2 --remove /dev/sdg [/COLOR]
mdadm: hot removed /dev/sdg from /dev/md2 
[COLOR=#000000]$ sudo mdadm --manage /dev/md2 --add /dev/sdg       [/COLOR]
mdadm: Failed to write metadata to /dev/sdg[/FONT]
```[FONT=monospace]


[/FONT]i have been told that before, but what is done is done, this was my 1st time setting up a md array, not sure how to fix it...

edit: i got it to try to go and had a eta of ~20k min, guess i am gonna need to power it down and unplug/clean and reconnect and hope... really hope this is a connection issue as i can't find anyone else having issues with this controller

---

### Post by MAFoElffen on 2023-08-04
What I do for people (my customers where I find this) is to: 
1. Back off the data, 
2. Zap the disks to remove evry trace of anything, 
3. Add a partition table and a partition on each drive
4. Redefine and assemble the new RAID Array
5. Restore the data back onto the Array.

RAID is going to degrade or fail over time. RAID is not a replacement for backups. You should be familiar with and have these kinds of things setup for the eventuality. I good disaster recovery plan includes testing and practicing the plan steps to see if it actually works. The steps above are (generally) what I use whether it is hardware RAID, mdadm, LVM2 RAID or ZFS RAIDz.

If I do that occasionally, it also take care of fragmentation.

EDIT:
As Darkod mentioned, do not use a whole raw disk for mdadm. LVM, ZFS or BTRFS. Always put those within a partition. In my honest opinion, putting those on a raw disk is a disaster waiting to happen. (For you... Again.) Take this opportunity as a wakeup call. You are now aware that it can cause problems. Please make a plan to prevent that from happening again.

---

### Post by pqwoerituytrueiwoq on 2023-08-05
i would like to use zfs, but what not sure how, but i think i found out
[https://ubuntu.com/tutorials/setup-zfs-storage-pool#2-installing-zfs](https://ubuntu.com/tutorials/setup-zfs-storage-pool#2-installing-zfs)
but doing this for a mirrored stripe (raid10)
```
zpool create mypool mirror sda sdb mirror sdc sdd
```
i was recently thinking of getting a couple 8TB drives (as i lack spare 4TB drives and they are overpriced IMO), would i be able to do this:
* 8TB (mirror)
* 8TB (mirror)
* 4TB+4TB (stripe)
So i could have 3 drives fail and not have down time (unless both 8TB dries went in that)

i have no data at risk, i know raid is not a backup, raid is to avoid down time

---

### Post by MAFoElffen on 2023-08-06
Yes. That command will create 2 two way mirrors in one command... That is, if you were more specific with how you ID your disks.

Doing what you said, you will be able to lose 2 disks. Striping 2 disks, you have ) disk failure tolerance. Though, ZFS gives you losts of warnings before that, unlike traditional RAID.

All you need to start is packages initramfs-zfs, zfsutiitls-linux and zfs-dkms. For zpool creation defines, I get a bit more detailed. For starts, where the mountpoint of the pool is going to reside within your filesystem. Then other options... 

This explains a lot of those options and the "why's" of them: [https://openzfs.github.io/openzfs-docs/Getting%20Started/Ubuntu/Ubuntu%2022.04%20Root%20on%20ZFS.html#id10](https://openzfs.github.io/openzfs-docs/Getting%20Started/Ubuntu/Ubuntu%2022.04%20Root%20on%20ZFS.html#id10)

My laptop, workstation and server are all ZFS-On-Root... For example my laptop:
```

mafoelffen@Mikes-ThinkPad-T520:~$ sudo zpool list
[sudo] password for mafoelffen: 
NAME      SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
backups  1.46T   224G  1.24T        -         -     0%    14%  1.00x    ONLINE  -
bpool    1.88G   436M  1.45G        -         -     0%    22%  1.00x    ONLINE  -
dpool     856G  1.18M   856G        -         -     0%     0%  1.00x    ONLINE  -
hpool     396G  49.1G   347G        -         -     0%    12%  1.00x    ONLINE  -
kpool     992G   407G   585G        -         -     0%    41%  1.00x    ONLINE  -
rpool     496G  23.5G   472G        -         -     0%     4%  1.00x    ONLINE  -
mafoelffen@Mikes-ThinkPad-T520:~$ sudo zfs list
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
backups                                            224G  1.20T       96K  /zfs-backups
backups/BACKUPS                                    224G  1.20T       96K  none
backups/BACKUPS/ubuntu_2204                        224G  1.20T       96K  /zfs-backups
backups/BACKUPS/ubuntu_2204/images-vm              224G  1.20T       96K  /zfs-backups/images-vm
backups/BACKUPS/ubuntu_2204/images-vm/2023-07-25   224G  1.20T      224G  /zfs-backups/images-vm/2023-07-25
bpool                                              436M  1.32G       96K  /boot
bpool/BOOT                                         435M  1.32G       96K  none
bpool/BOOT/ubuntu_2204                             435M  1.32G      435M  /boot
dpool                                             1.18M   829G       96K  /dpool
dpool/DATA                                         192K   829G       96K  none
dpool/DATA/ubuntu_2204                              96K   829G       96K  /dpool
hpool                                             49.1G   335G       96K  /home
hpool/USERDATA                                    49.1G   335G       96K  none
hpool/USERDATA/root_2204                          2.86G   335G     2.86G  /root
hpool/USERDATA/ubuntu_2204                        46.3G   335G     46.3G  /home
kpool                                              407G   554G       96K  /kpool
kpool/QEMU-KVM                                     407G   554G       96K  none
kpool/QEMU-KVM/ubuntu_2204                         407G   554G       96K  /kpool
kpool/QEMU-KVM/ubuntu_2204/ISO                     183G   554G      183G  /home/mafoelffen/Downloads/ISO
kpool/QEMU-KVM/ubuntu_2204/images                  224G   554G      224G  /var/lib/libvirt/images
kpool/QEMU-KVM/ubuntu_2204/libvirt                 528K   554G      528K  /etc/libvirt/
rpool                                             23.5G   457G       96K  /
rpool/ROOT                                        23.5G   457G       96K  none
rpool/ROOT/ubuntu_2204                            23.5G   457G     8.36G  /
rpool/ROOT/ubuntu_2204/srv                          96K   457G       96K  /srv
rpool/ROOT/ubuntu_2204/tmp                         308K   457G      308K  /tmp
rpool/ROOT/ubuntu_2204/usr                        3.18G   457G       96K  /usr
rpool/ROOT/ubuntu_2204/usr/local                  3.18G   457G     3.18G  /usr/local
rpool/ROOT/ubuntu_2204/var                        12.0G   457G       96K  /var
rpool/ROOT/ubuntu_2204/var/cache                   569M   457G      569M  /var/cache
rpool/ROOT/ubuntu_2204/var/games                    96K   457G       96K  /var/games
rpool/ROOT/ubuntu_2204/var/lib                    6.77G   457G     6.61G  /var/lib
rpool/ROOT/ubuntu_2204/var/lib/AccountsService     112K   457G      112K  /var/lib/AccountsService
rpool/ROOT/ubuntu_2204/var/lib/NetworkManager      460K   457G      460K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_2204/var/lib/apt                 100M   457G      100M  /var/lib/apt
rpool/ROOT/ubuntu_2204/var/lib/docker               96K   457G       96K  /var/lib/docker
rpool/ROOT/ubuntu_2204/var/lib/dpkg               59.4M   457G     59.4M  /var/lib/dpkg
rpool/ROOT/ubuntu_2204/var/lib/nfs                 104K   457G      104K  /var/lib/nfs
rpool/ROOT/ubuntu_2204/var/log                     638M   457G      638M  /var/log
rpool/ROOT/ubuntu_2204/var/mail                     96K   457G       96K  /var/mail
rpool/ROOT/ubuntu_2204/var/snap                   3.59G   457G     3.59G  /var/snap
rpool/ROOT/ubuntu_2204/var/spool                   328K   457G      328K  /var/spool
rpool/ROOT/ubuntu_2204/var/tmp                     452M   457G      452M  /var/tmp
rpool/ROOT/ubuntu_2204/var/www                      96K   457G       96K  /var/www

```

---

### Post by MAFoElffen on 2023-08-06
This is a look at two of the pools on my server. With RAIDz2, i can lose 2 disks from each pool and be good:
```

mafoelffen@Mikes-B460M:~$ sudo zpool status -v datapool
[sudo] password for mafoelffen: 
  pool: datapool
 state: ONLINE
  scan: scrub repaired 0B in 00:16:11 with 0 errors on Sun Jul 30 06:36:28 2023
config:

    NAME                                                   STATE     READ WRITE CKSUM
    datapool                                               ONLINE       0     0     0
      raidz2-0                                             ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA09560A-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA11601H-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA47393M-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNS0W330507J-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TB08933B-part1  ONLINE       0     0     0
    logs    
      nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part2   ONLINE       0     0     0
    cache
      nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part1   ONLINE       0     0     0

errors: No known data errors
mafoelffen@Mikes-B460M:~$ sudo zpool status -v kpool
  pool: kpool
 state: ONLINE
  scan: scrub repaired 0B in 00:06:08 with 0 errors on Sun Jul 30 06:45:27 2023
config:

    NAME                                 STATE     READ WRITE CKSUM
    kpool                                ONLINE       0     0     0
      raidz2-0                           ONLINE       0     0     0
        nvme-eui.0025385a2140bd61-part1  ONLINE       0     0     0
        nvme-eui.0025385a21418769-part1  ONLINE       0     0     0
        nvme-eui.0025385a2141f4fc-part1  ONLINE       0     0     0
        nvme-eui.0025385b21407ef0-part1  ONLINE       0     0     0

errors: No known data errors

```
Note that you should get in the habit of doing your config's by using a unique disk identifier, such as UUID or /dev/disk/by-id/... using just /dev/sdX will get you in trouble when the disks change ID's during a reboot. It happens. Then you would wonder why your disks are dropping out or your arrays or pools.

---

### Post by pqwoerituytrueiwoq on 2023-08-06
I think i might have it fixed *knock on wood*
2 issues: 1 bad cable and one dodgy connection, may also have a bad sata port as the bad cable was worse in one than the other

/dev/sdX chancing all the time  is annoying, i have a script for identifying drives, really hope you do not mean that my zfs config will break when it scrambles again...
```

[FONT=monospace][COLOR=#000000]<?php [/COLOR]
$data=shell_exec("bash -c \"udevadm info --query=all --name=/dev/sd{a..z} | egrep 'ID_SERIA
L_SHORT|DEVNAME|DEVPATH|ID_MODEL='\" 2> /dev/null");
$data=explode("\n",$data); 
foreach($data as $line){ 
        $eq=strpos($line,"="); 
        if ($eq > 3){ 
                $tag=substr($line,3,$eq-3); 
                $val=substr($line,$eq+1); 
                if($tag=="DEVPATH"){ 
                        $val=explode('/',$val)[5]; 
                        echo "\nDEV: $val\n"; 
                } 
                else{ 
                        echo "\t$tag: $val\n"; 
                } 
        } 
} 
?>


```

```
[/FONT][FONT=monospace][COLOR=#000000]$ zpool status && cat /proc/mdstat  [/COLOR]
  pool: mypool 
 state: ONLINE 
  scan: resilvered 10.7M in 00:00:01 with 0 errors on Sun Aug  6 08:33:14 2023 
config: 

        NAME        STATE     READ WRITE CKSUM 
        mypool      ONLINE       0     0     0 
          mirror-0  ONLINE       0     0     0 
            sdf     ONLINE       0     0     0 
            sdg     ONLINE       0     0     0 
          mirror-1  ONLINE       0     0     0 
            sdh     ONLINE       0     0     0 
            sde     ONLINE       0     0     0 

errors: No known data errors 
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10]  
md1 : active raid1 sdd1[1] sdc1[0] 
      124966912 blocks super 1.2 [2/2] [UU] 
      bitmap: 1/1 pages [4KB], 65536KB chunk 

md0 : active raid1 sda2[1] sdb2[0] 
      124965888 blocks super 1.2 [2/2] [UU] 
      bitmap: 1/1 pages [4KB], 65536KB chunk 

unused devices: <none>
[/FONT][FONT=monospace][COLOR=#000000]$ php ls_drives            [/COLOR]

DEV: ata1 
        DEVNAME: /dev/sda 
        ID_MODEL: INTEL_SSDSCKKF12 
        ID_SERIAL_SHORT: BTLA81061ECP128I 

DEV: ata2 
        DEVNAME: /dev/sdb 
        ID_MODEL: INTEL_SSDSCKKF12 
        ID_SERIAL_SHORT: BTLA81510DU3128I 

DEV: ata5 
        DEVNAME: /dev/sdc 
        ID_MODEL: INTEL_SSDSCKKF12 
        ID_SERIAL_SHORT: BTLA810613SC128I 

DEV: ata6 
        DEVNAME: /dev/sdd 
        ID_MODEL: INTEL_SSDSCKKF12 
        ID_SERIAL_SHORT: BTLA810616PX128I 

DEV: ata9 
        DEVNAME: /dev/sde 
        ID_MODEL: WDC_WD40EFRX-68N 
        ID_SERIAL_SHORT: WD-WCC7K0CSZY00 

DEV: ata10 
        DEVNAME: /dev/sdf 
        ID_MODEL: WDC_WD40EFRX-68N 
        ID_SERIAL_SHORT: WD-WCC7K7KKNSN9 

DEV: ata11 
        DEVNAME: /dev/sdg 
        ID_MODEL: WDC_WD40EFRX-68N 
        ID_SERIAL_SHORT: WD-WCC7K0RY7R37 

DEV: ata13 
        DEVNAME: /dev/sdh 
        ID_MODEL: WDC_WD40EFRX-68N 
        ID_SERIAL_SHORT: WD-WCC7K4PE4C1U 

DEV: usb1 
        DEVNAME: /dev/sdi 
        ID_MODEL: Compact_Flash 
        ID_SERIAL_SHORT: 20060413092100000 

DEV: usb1 
        DEVNAME: /dev/sdj 
        ID_MODEL: SM_xD-Picture 
        ID_SERIAL_SHORT: 20060413092100000 

DEV: usb1 
        DEVNAME: /dev/sdk 
        ID_MODEL: SD_MMC 
        ID_SERIAL_SHORT: 20060413092100000 

DEV: usb1 
        DEVNAME: /dev/sdl 
        ID_MODEL: MS_MS-Pro 
        ID_SERIAL_SHORT: 20060413092100000
[/FONT][FONT=monospace][COLOR=#000000]$ sudo parted -l [/COLOR]
Model: ATA INTEL SSDSCKKF12 (scsi) 
Disk /dev/sda: 128GB 
Sector size (logical/physical): 512B/512B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End     Size    File system  Name       Flags 
 1      1049kB  2097kB  1049kB               BIOS_GRUB  bios_grub 
 2      2097kB  128GB   128GB                System     raid 


Model: ATA INTEL SSDSCKKF12 (scsi) 
Disk /dev/sdb: 128GB 
Sector size (logical/physical): 512B/512B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End     Size    File system  Name       Flags 
 1      1049kB  2097kB  1049kB               BIOS_GRUB  bios_grub 
 2      2097kB  128GB   128GB                System     raid 


Model: ATA INTEL SSDSCKKF12 (scsi) 
Disk /dev/sdc: 128GB 
Sector size (logical/physical): 512B/512B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End    Size   File system  Name  Flags 
 1      1049kB  128GB  128GB               Data  raid 


Model: ATA INTEL SSDSCKKF12 (scsi) 
Disk /dev/sdd: 128GB 
Sector size (logical/physical): 512B/512B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End    Size   File system  Name  Flags 
 1      1049kB  128GB  128GB               Data  raid 


Model: ATA WDC WD40EFRX-68N (scsi) 
Disk /dev/sde: 4001GB 
Sector size (logical/physical): 512B/4096B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End     Size    File system  Name                  Flags 
 1      1049kB  4001GB  4001GB  zfs          zfs-c86ce3fb089ea106 
 9      4001GB  4001GB  8389kB 


Model: ATA WDC WD40EFRX-68N (scsi) 
Disk /dev/sdf: 4001GB 
Sector size (logical/physical): 512B/4096B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End     Size    File system  Name                  Flags 
 1      1049kB  4001GB  4001GB  zfs          zfs-a97852a977aeebcf 
 9      4001GB  4001GB  8389kB 


Model: Linux Software RAID Array (md) 
Disk /dev/md0: 128GB 
Sector size (logical/physical): 512B/512B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End    Size   File system  Name  Flags 
 1      1049kB  128GB  128GB  ext4 


Model: ATA WDC WD40EFRX-68N (scsi) 
Disk /dev/sdg: 4001GB 
Sector size (logical/physical): 512B/4096B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End     Size    File system  Name                  Flags 
 1      1049kB  4001GB  4001GB  zfs          zfs-1e1448557be278de 
 9      4001GB  4001GB  8389kB 


Model: Linux Software RAID Array (md) 
Disk /dev/md1: 128GB 
Sector size (logical/physical): 512B/512B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End    Size   File system  Name  Flags 
 1      1049kB  128GB  128GB  ext4 


Model: ATA WDC WD40EFRX-68N (scsi) 
Disk /dev/sdh: 4001GB 
Sector size (logical/physical): 512B/4096B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End     Size    File system  Name                  Flags 
 1      1049kB  4001GB  4001GB  zfs          zfs-97acb1c9618421eb 
 9      4001GB  4001GB  8389kB
[/FONT]
[FONT=monospace]
```
[/FONT]

---

### Post by ixeous on 2023-08-06
A resource I've found useful for dealing with md is [https://www.ducea.com/2009/03/08/mdadm-cheat-sheet/](https://www.ducea.com/2009/03/08/mdadm-cheat-sheet/).  You may need to zero the superblock on the drive so you can then add it back to md.

---

### Post by MAFoElffen on 2023-08-06
> **pqwoerituytrueiwoq said:**
> I think i might have it fixed *knock on wood*
2 issues: 1 bad cable and one dodgy connection, may also have a bad sata port as the bad cable was worse in one than the other

/dev/sdX chancing all the time  is annoying, i have a script for identifying drives, really hope you do not mean that my zfs config will break when it scrambles again...
```

[FONT=monospace][COLOR=#000000]<?php [/COLOR]
$data=shell_exec("bash -c \"udevadm info --query=all --name=/dev/sd{a..z} | egrep 'ID_SERIA
L_SHORT|DEVNAME|DEVPATH|ID_MODEL='\" 2> /dev/null");
$data=explode("\n",$data); 
foreach($data as $line){ 
        $eq=strpos($line,"="); 
        if ($eq > 3){ 
                $tag=substr($line,3,$eq-3); 
                $val=substr($line,$eq+1); 
                if($tag=="DEVPATH"){ 
                        $val=explode('/',$val)[5]; 
                        echo "\nDEV: $val\n"; 
                } 
                else{ 
                        echo "\t$tag: $val\n"; 
                } 
        } 
} 
?>

[/FONT]
```[FONT=monospace]

[/FONT]```
[FONT=monospace][COLOR=#000000]$ zpool status && cat /proc/mdstat  [/COLOR]
  pool: mypool 
 state: ONLINE 
  scan: resilvered 10.7M in 00:00:01 with 0 errors on Sun Aug  6 08:33:14 2023 
config: 

        NAME        STATE     READ WRITE CKSUM 
        mypool      ONLINE       0     0     0 
          mirror-0  ONLINE       0     0     0 
            sdf     ONLINE       0     0     0 
            sdg     ONLINE       0     0     0 
          mirror-1  ONLINE       0     0     0 
            sdh     ONLINE       0     0     0 
            sde     ONLINE       0     0     0 

errors: No known data errors 
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10]  
md1 : active raid1 sdd1[1] sdc1[0] 
      124966912 blocks super 1.2 [2/2] [UU] 
      bitmap: 1/1 pages [4KB], 65536KB chunk 

md0 : active raid1 sda2[1] sdb2[0] 
      124965888 blocks super 1.2 [2/2] [UU] 
      bitmap: 1/1 pages [4KB], 65536KB chunk 

unused devices: <none>
[/FONT][FONT=monospace][COLOR=#000000]$ php ls_drives            [/COLOR]

DEV: ata1 
        DEVNAME: /dev/sda 
        ID_MODEL: INTEL_SSDSCKKF12 
        ID_SERIAL_SHORT: BTLA81061ECP128I 

DEV: ata2 
        DEVNAME: /dev/sdb 
        ID_MODEL: INTEL_SSDSCKKF12 
        ID_SERIAL_SHORT: BTLA81510DU3128I 

DEV: ata5 
        DEVNAME: /dev/sdc 
        ID_MODEL: INTEL_SSDSCKKF12 
        ID_SERIAL_SHORT: BTLA810613SC128I 

DEV: ata6 
        DEVNAME: /dev/sdd 
        ID_MODEL: INTEL_SSDSCKKF12 
        ID_SERIAL_SHORT: BTLA810616PX128I 

DEV: ata9 
        DEVNAME: /dev/sde 
        ID_MODEL: WDC_WD40EFRX-68N 
        ID_SERIAL_SHORT: WD-WCC7K0CSZY00 

DEV: ata10 
        DEVNAME: /dev/sdf 
        ID_MODEL: WDC_WD40EFRX-68N 
        ID_SERIAL_SHORT: WD-WCC7K7KKNSN9 

DEV: ata11 
        DEVNAME: /dev/sdg 
        ID_MODEL: WDC_WD40EFRX-68N 
        ID_SERIAL_SHORT: WD-WCC7K0RY7R37 

DEV: ata13 
        DEVNAME: /dev/sdh 
        ID_MODEL: WDC_WD40EFRX-68N 
        ID_SERIAL_SHORT: WD-WCC7K4PE4C1U 

DEV: usb1 
        DEVNAME: /dev/sdi 
        ID_MODEL: Compact_Flash 
        ID_SERIAL_SHORT: 20060413092100000 

DEV: usb1 
        DEVNAME: /dev/sdj 
        ID_MODEL: SM_xD-Picture 
        ID_SERIAL_SHORT: 20060413092100000 

DEV: usb1 
        DEVNAME: /dev/sdk 
        ID_MODEL: SD_MMC 
        ID_SERIAL_SHORT: 20060413092100000 

DEV: usb1 
        DEVNAME: /dev/sdl 
        ID_MODEL: MS_MS-Pro 
        ID_SERIAL_SHORT: 20060413092100000
[/FONT][FONT=monospace][COLOR=#000000]$ sudo parted -l [/COLOR]
Model: ATA INTEL SSDSCKKF12 (scsi) 
Disk /dev/sda: 128GB 
Sector size (logical/physical): 512B/512B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End     Size    File system  Name       Flags 
 1      1049kB  2097kB  1049kB               BIOS_GRUB  bios_grub 
 2      2097kB  128GB   128GB                System     raid 


Model: ATA INTEL SSDSCKKF12 (scsi) 
Disk /dev/sdb: 128GB 
Sector size (logical/physical): 512B/512B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End     Size    File system  Name       Flags 
 1      1049kB  2097kB  1049kB               BIOS_GRUB  bios_grub 
 2      2097kB  128GB   128GB                System     raid 


Model: ATA INTEL SSDSCKKF12 (scsi) 
Disk /dev/sdc: 128GB 
Sector size (logical/physical): 512B/512B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End    Size   File system  Name  Flags 
 1      1049kB  128GB  128GB               Data  raid 


Model: ATA INTEL SSDSCKKF12 (scsi) 
Disk /dev/sdd: 128GB 
Sector size (logical/physical): 512B/512B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End    Size   File system  Name  Flags 
 1      1049kB  128GB  128GB               Data  raid 


Model: ATA WDC WD40EFRX-68N (scsi) 
Disk /dev/sde: 4001GB 
Sector size (logical/physical): 512B/4096B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End     Size    File system  Name                  Flags 
 1      1049kB  4001GB  4001GB  zfs          zfs-c86ce3fb089ea106 
 9      4001GB  4001GB  8389kB 


Model: ATA WDC WD40EFRX-68N (scsi) 
Disk /dev/sdf: 4001GB 
Sector size (logical/physical): 512B/4096B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End     Size    File system  Name                  Flags 
 1      1049kB  4001GB  4001GB  zfs          zfs-a97852a977aeebcf 
 9      4001GB  4001GB  8389kB 


Model: Linux Software RAID Array (md) 
Disk /dev/md0: 128GB 
Sector size (logical/physical): 512B/512B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End    Size   File system  Name  Flags 
 1      1049kB  128GB  128GB  ext4 


Model: ATA WDC WD40EFRX-68N (scsi) 
Disk /dev/sdg: 4001GB 
Sector size (logical/physical): 512B/4096B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End     Size    File system  Name                  Flags 
 1      1049kB  4001GB  4001GB  zfs          zfs-1e1448557be278de 
 9      4001GB  4001GB  8389kB 


Model: Linux Software RAID Array (md) 
Disk /dev/md1: 128GB 
Sector size (logical/physical): 512B/512B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End    Size   File system  Name  Flags 
 1      1049kB  128GB  128GB  ext4 


Model: ATA WDC WD40EFRX-68N (scsi) 
Disk /dev/sdh: 4001GB 
Sector size (logical/physical): 512B/4096B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End     Size    File system  Name                  Flags 
 1      1049kB  4001GB  4001GB  zfs          zfs-97acb1c9618421eb 
 9      4001GB  4001GB  8389kB
[/FONT]

```[FONT=monospace]
[/FONT]
If you look at your zpool status, where it has the diskid, note my past warning on using unique disk identifiers... I explain that more in your other thread, and re: [https://ubuntuforums.org/showthread.php?t=2485803&highlight=zfs+degrade](https://ubuntuforums.org/showthread.php?t=2485803&highlight=zfs+degrade)  <-- That thread was a user that used /dev/sdX in his pool create commands (instead of using unique disk identifiers), and the disks where changing designations on shutdown/reboot, degrading his arrays...

It's not just an fstab kind of thing. That condition can happen with mdadm, LVM2 RAID, ZFS RAIDz, and BTRFS RAID...

---

### Post by pqwoerituytrueiwoq on 2023-08-06
so if i am reading right
```
sudo zpool create -m /mnt/HDD mypool mirror sdf sdg mirror sdh sde
```
should have been
```
sudo zpool create -m /mnt/HDD mypool mirror /dev/disk/by-id/ata-WDC_WD40EFRX-68N32N0_WD-WCC7K7KKNSN9 /dev/disk/by-id/ata-WDC_WD40EFRX-68N32N0_WD-WCC7K0RY7R37 mirror /dev/disk/by-id/ata-WDC_WD40EFRX-68N32N0_WD-WCC7K4PE4C1U /dev/disk/by-id/ata-WDC_WD40EFRX-68N32N0_WD-WCC7K0CSZY00
```
or 
```
sudo zpool create -m /mnt/HDD mypool mirror /dev/disk/by-path/pci-0000\:2e\:00.0-ata-2 /dev/disk/by-path/pci-0000\:2e\:00.0-ata-3 mirror /dev/disk/by-path/pci-0000\:2e\:00.0-ata-5 /dev/disk/by-path/pci-0000\:2e\:00.0-ata-1
```

i assume the last one would auto allocate any drive inserted to the pool

is this fixable or do i have to wipe the array and rebuild it?
```

$ readlink /dev/disk/by-path/pci-0000\:2e\:00.0-ata-{1,2,3,5}
../../sde
../../sdf
../../sdg
../../sdh
$ ls -l /dev/disk/by-id/ata-WDC_WD40EFRX-68N32N0_WD-*| grep -v part
lrwxrwxrwx 1 root root  9 Aug  6 08:50 /dev/disk/by-id/ata-WDC_WD40EFRX-68N32N0_WD-WCC7K0CSZY00 -> ../../sde
lrwxrwxrwx 1 root root  9 Aug  6 08:50 /dev/disk/by-id/ata-WDC_WD40EFRX-68N32N0_WD-WCC7K0RY7R37 -> ../../sdg
lrwxrwxrwx 1 root root  9 Aug  6 08:50 /dev/disk/by-id/ata-WDC_WD40EFRX-68N32N0_WD-WCC7K4PE4C1U -> ../../sdh
lrwxrwxrwx 1 root root  9 Aug  6 08:50 /dev/disk/by-id/ata-WDC_WD40EFRX-68N32N0_WD-WCC7K7KKNSN9 -> ../../sdf

```

---

### Post by MAFoElffen on 2023-08-07
The way you declared that. logically, I see RAID10 (2 mirrored drives times 2 in one pool.) 

If you used this one...
```

sudo zpool create \
    -m /mnt/HDD \
    mypool \
    mirror \
    /dev/disk/by-id/ata-WDC_WD40EFRX-68N32N0_WD-WCC7K7KKNSN9-part1 \
    /dev/disk/by-id/ata-WDC_WD40EFRX-68N32N0_WD-WCC7K0RY7R37-part1 \
    mirror \
    /dev/disk/by-id/ata-WDC_WD40EFRX-68N32N0_WD-WCC7K4PE4C1U-part1 \
    /dev/disk/by-id/ata-WDC_WD40EFRX-68N32N0_WD-WCC7K0CSZY00-part1

```
Even if the are in hot-swap bays and you pulled them out, then put them in a different order (shuffled them), the system, on boot, would find the disks, the partitions on them and use them... That would be the advantage of using those types of Unique identifiers.

I added "-part1", because you are going to want to partition them, right? GPT partition table and most likely using type code "BF07", which is ZFS Reserved...

To do that, destroy it, and use sgdisk, which is the cli API for GDisk... That's what I use, because I con use it from scripts.

You can use either -m /mnt/HDD, or -o mountpoint=/mnt/HDD for your mount point... If you search on my username, you can find a thread where I led someone through ZFS Pool tuning... for your disks, I would use option property "-o ashift=12 and some other options, like for compression. They will help with performance. Something like this:
```

sudo su -

mkdir /HDD ## Or something more descriptive for your mountpoint.

zpool create \
[COLOR=#008000]    -o ashift=12 \
    -o autotrim=on \
    -O acltype=posixacl -O xattr=sa -O dnodesize=auto \
    -O compression=lz4 \
    -O normalization=formD \
    -O relatime=on \
    -O canmount=off -O mountpoint=/HDD \
[/COLOR]    mypool \
    mirror \
    /dev/disk/by-id/ata-WDC_WD40EFRX-68N32N0_WD-WCC7K7KKNSN9-part1 \
    /dev/disk/by-id/ata-WDC_WD40EFRX-68N32N0_WD-WCC7K0RY7R37-part1 \
    mirror \
    /dev/disk/by-id/ata-WDC_WD40EFRX-68N32N0_WD-WCC7K4PE4C1U-part1 \
    /dev/disk/by-id/ata-WDC_WD40EFRX-68N32N0_WD-WCC7K0CSZY00-part1

```
The options in green are options I use on all my Linux ZFS pools...

The ashift=12 property will set the block size, that is what I would recommend for spun disks. SSD's and NVMe I would do ashift =13. In my benchmarks for tuning, this setting seems to be the best for performance. It can only be set during pool creation.

I turn on autotrim on all my pools.

In the next line, that is Linux ZFS ACL compatibility. That really is required for some things such as SAMBA and NFS shares.

Next line, I declare which compression type to use. That is the ype which seems to be the best perfomance balanced with a good comrpession rate. You would think that this might slow things down, ebcause you use CPU for compression right? The CPU load is neglegable, and perfomance go up, becuase you are having to read and write less data (less data to move).

The normalization property affects how filenames on/in a dataset are compared in regards to special characters. This property indicates whether a file system should perform a unicode normalization of file names whenever two file names are compared, and which normalization algorithm should be used.

"relatime" is another specifically ZFS on Linux property. Setting this value to on means the access time is only updated under one of two circumstances: If the mtime or ctime values changed. If the existing access time has not been updated within the past 24 hours (it will be updated the next time the file is accessed).

The options I described above are for Pool Tuning...

There are two other types of options I set for specific circumstances. If I am going to use a cache, then I add
```

    -o cachefile=/etc/zfs/zpool.cache 

```
If I am going to use ZFS native encryption then I add
```

    -O encryption=on -O keylocation=prompt -O keyformat=passphrase 

```
To set the passphrase as a prompt, or sometimes I'll set it up with a keyfile.

EDIT:
Notice I use mounts from either the root (/) or inside of Home... I'm sort of a trueist. By best practices, I leave /mnt for temporary mounts, just like leaving /media for temporary mounts of removable media. You can do it... But I also contribute to boot-info and boot-repair, as well as am the founder of the Ama-Gi Project... so I know we use /mnt for temporary mounts to chroot into an installed system to repair it. That gets sticky when the user mounts other "things" there.

---

### Post by pqwoerituytrueiwoq on 2023-08-07
[FONT=monospace][COLOR=#000000]oh, /mnt for temp ones, i thought /media was for temp and /mnt was for manual custom mounts

how would i replace a drive? and yes it is supposed to be a raid 10 setup

most of the data i have is mp3 files (owncloud sync) and i am using a ryzen 2200GE w/ 8gb ram (dual channel) still recommend compression?
when i say 8gb ram i mean 8gb minus my pfsense vm's ram allocation still recommenced compression?

note that the server runs mpd using my mp3 library on the server

```
$ sudo parted -l 
```[/COLOR]```

Model: ATA INTEL SSDSCKKF12 (scsi) 
Disk /dev/sda: 128GB 
Sector size (logical/physical): 512B/512B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End     Size    File system  Name       Flags 
 1      1049kB  2097kB  1049kB               BIOS_GRUB  bios_grub 
 2      2097kB  128GB   128GB                System     raid 


Model: ATA INTEL SSDSCKKF12 (scsi) 
Disk /dev/sdb: 128GB 
Sector size (logical/physical): 512B/512B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End     Size    File system  Name       Flags 
 1      1049kB  2097kB  1049kB               BIOS_GRUB  bios_grub 
 2      2097kB  128GB   128GB                System     raid 


Model: ATA INTEL SSDSCKKF12 (scsi) 
Disk /dev/sdc: 128GB 
Sector size (logical/physical): 512B/512B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End    Size   File system  Name  Flags 
 1      1049kB  128GB  128GB               Data  raid 


Model: ATA INTEL SSDSCKKF12 (scsi) 
Disk /dev/sdd: 128GB 
Sector size (logical/physical): 512B/512B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End    Size   File system  Name  Flags 
 1      1049kB  128GB  128GB               Data  raid 


Model: ATA WDC WD40EFRX-68N (scsi) 
Disk /dev/sde: 4001GB 
Sector size (logical/physical): 512B/4096B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End     Size    File system  Name                  Flags 
 1      1049kB  4001GB  4001GB  zfs          zfs-c86ce3fb089ea106 
 9      4001GB  4001GB  8389kB 


Model: ATA WDC WD40EFRX-68N (scsi) 
Disk /dev/sdf: 4001GB 
Sector size (logical/physical): 512B/4096B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End     Size    File system  Name                  Flags 
 1      1049kB  4001GB  4001GB  zfs          zfs-a97852a977aeebcf 
 9      4001GB  4001GB  8389kB 


Model: Linux Software RAID Array (md) 
Disk /dev/md0: 128GB 
Sector size (logical/physical): 512B/512B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End    Size   File system  Name  Flags 
 1      1049kB  128GB  128GB  ext4 


Model: ATA WDC WD40EFRX-68N (scsi) 
Disk /dev/sdg: 4001GB 
Sector size (logical/physical): 512B/4096B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End     Size    File system  Name                  Flags 
 1      1049kB  4001GB  4001GB  zfs          zfs-1e1448557be278de 
 9      4001GB  4001GB  8389kB 


Model: Linux Software RAID Array (md) 
Disk /dev/md1: 128GB 
Sector size (logical/physical): 512B/512B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End    Size   File system  Name  Flags 
 1      1049kB  128GB  128GB  ext4 


Model: ATA WDC WD40EFRX-68N (scsi) 
Disk /dev/sdh: 4001GB 
Sector size (logical/physical): 512B/4096B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End     Size    File system  Name                  Flags 
 1      1049kB  4001GB  4001GB  zfs          zfs-97acb1c9618421eb 
 9      4001GB  4001GB  8389kB
```

before i created the pool i had a empty gpt partition table on each HDD
[/FONT]

---

### Post by MAFoElffen on 2023-08-08
Differences:
> 
What is the difference between MNT and media directory?




Technically,  there is no functional difference whatsoever between the two. /mnt is a  standard directory, as is /media/... The difference is in what they  should be used for, emphasis on should. **/media is supposed to be the mount point for removable media while /mnt is for temporary mounts initiated by the user**.

/media is sort of "special"... If you have automount turned on (on desktops), then udisk will create a folder under /media with the user's username... Then when a USB flash drive is plugged in, or in nautilus, you select a drive that was not mounted, (to mount it), then it creates a folder under that username folder under that, which a folder that sort of decribes that, and set permission for that user to read it. For instance, let me plug in a flash drive to show you... (Windows Enterprise ToGo)
```

mafoelffen@Mikes-ThinkPad-T520:~$ tree -L 3 /media
/media
&#9492;&#9472;&#9472; mafoelffen
    &#9492;&#9472;&#9472; CCCOMA_X64FRE_EN-US_DV9
        &#9500;&#9472;&#9472; $Recycle.Bin
        &#9500;&#9472;&#9472; $WinREAgent
        &#9500;&#9472;&#9472; autorun.ico
        &#9500;&#9472;&#9472; autorun.inf
        &#9500;&#9472;&#9472; Boot
        &#9500;&#9472;&#9472; bootmgr
        &#9500;&#9472;&#9472; BOOTNXT
        &#9500;&#9472;&#9472; Documents and Settings -> ./Users
        &#9500;&#9472;&#9472; DumpStack.log.tmp
        &#9500;&#9472;&#9472; EFI
        &#9500;&#9472;&#9472; hiberfil.sys
        &#9500;&#9472;&#9472; Intel
        &#9500;&#9472;&#9472; pagefile.sys
        &#9500;&#9472;&#9472; PerfLogs
        &#9500;&#9472;&#9472; ProgramData
        &#9500;&#9472;&#9472; Program Files
        &#9500;&#9472;&#9472; Program Files (x86)
        &#9500;&#9472;&#9472; Recovery
        &#9500;&#9472;&#9472; swapfile.sys
        &#9500;&#9472;&#9472; System Volume Information
        &#9500;&#9472;&#9472; Users
        &#9492;&#9472;&#9472; Windows

16 directories, 8 files

```
Even with an empty GPT Table,.. If you forget to tell it to use a partition, and mistakenly tell it to use the raw disk (like you did), it will overwrite the partition table. 

Do something like this to prep your disks:
```

sudo su -

DISKS=("/dev/disk/by-id/ata-WDC_WD40EFRX-68N32N0_WD-WCC7K0CSZY00" \
    "/dev/disk/by-id/ata-WDC_WD40EFRX-68N32N0_WD-WCC7K0RY7R37" \
    "/dev/disk/by-id/ata-WDC_WD40EFRX-68N32N0_WD-WCC7K4PE4C1U" \
    "/dev/disk/by-id/ata-WDC_WD40EFRX-68N32N0_WD-WCC7K7KKNSN9")

for DISK in ${DISKS[@]}
do
  sgdisk --zap-all $DISK
  sgdisk -n1:0:0 -c1:mydata -t1:BF03 $DISK 
done

```
Then all your partitions will be:
```

/dev/disk/by-id/ata-WDC_WD40EFRX-68N32N0_WD-WCC7K0CSZY00-part1
/dev/disk/by-id/ata-WDC_WD40EFRX-68N32N0_WD-WCC7K0RY7R37-part1
/dev/disk/by-id/ata-WDC_WD40EFRX-68N32N0_WD-WCC7K4PE4C1U-part1
/dev/disk/by-id/ata-WDC_WD40EFRX-68N32N0_WD-WCC7K7KKNSN9-part1

```

---

### Post by pqwoerituytrueiwoq on 2023-08-08
[FONT=monospace][COLOR=#000000]
```
$ ls /dev/disk/by-id/ |grep WCC7K0CSZY00
```[/COLOR]```

ata-WDC_WD40EFRX-68N32N0_WD-[COLOR=#ff5454]**WCC7K0CSZY00**[/COLOR]
ata-WDC_WD40EFRX-68N32N0_WD-[COLOR=#ff5454]**WCC7K0CSZY00**[/COLOR][COLOR=#000000]-part1 [/COLOR]
ata-WDC_WD40EFRX-68N32N0_WD-[COLOR=#ff5454]**WCC7K0CSZY00**[/COLOR][COLOR=#000000]-part9 [/COLOR]
scsi-0ATA_WDC_WD40EFRX-68N_WD-[COLOR=#ff5454]**WCC7K0CSZY00**[/COLOR]
scsi-0ATA_WDC_WD40EFRX-68N_WD-[COLOR=#ff5454]**WCC7K0CSZY00**[/COLOR][COLOR=#000000]-part1 [/COLOR]
scsi-0ATA_WDC_WD40EFRX-68N_WD-[COLOR=#ff5454]**WCC7K0CSZY00**[/COLOR][COLOR=#000000]-part9 [/COLOR]
scsi-1ATA_WDC_WD40EFRX-68N32N0_WD-[COLOR=#ff5454]**WCC7K0CSZY00**[/COLOR]
scsi-1ATA_WDC_WD40EFRX-68N32N0_WD-[COLOR=#ff5454]**WCC7K0CSZY00**[/COLOR][COLOR=#000000]-part1 [/COLOR]
scsi-1ATA_WDC_WD40EFRX-68N32N0_WD-[COLOR=#ff5454]**WCC7K0CSZY00**[/COLOR][COLOR=#000000]-part9 [/COLOR]
scsi-SATA_WDC_WD40EFRX-68N_WD-[COLOR=#ff5454]**WCC7K0CSZY00**[/COLOR]
scsi-SATA_WDC_WD40EFRX-68N_WD-[COLOR=#ff5454]**WCC7K0CSZY00**[/COLOR][COLOR=#000000]-part1 [/COLOR]
scsi-SATA_WDC_WD40EFRX-68N_WD-[COLOR=#ff5454]**WCC7K0CSZY00**[/COLOR][COLOR=#000000]-part9[/COLOR]
```[COLOR=#000000]
Did zfs not make 2 partitions on the table?[/COLOR]
[/FONT]```
[FONT=monospace][COLOR=#000000]Model: ATA WDC WD40EFRX-68N (scsi) [/COLOR]
Disk /dev/sde: 4001GB 
Sector size (logical/physical): 512B/4096B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End     Size    File system  Name                  Flags 
 1      1049kB  4001GB  4001GB  zfs          zfs-c86ce3fb089ea106 
 9      4001GB  4001GB  8389kB[/FONT]
```[FONT=monospace]
[/FONT]

---

### Post by pqwoerituytrueiwoq on 2023-08-08
[FONT=monospace][COLOR=#000000]
```
$ ls /dev/disk/by-id/ |grep WCC7K0CSZY00 
```[/COLOR]```

ata-WDC_WD40EFRX-68N32N0_WD-[COLOR=#ff5454]**WCC7K0CSZY00**[/COLOR]
ata-WDC_WD40EFRX-68N32N0_WD-[COLOR=#ff5454]**WCC7K0CSZY00**[/COLOR][COLOR=#000000]-part1 [/COLOR]
ata-WDC_WD40EFRX-68N32N0_WD-[COLOR=#ff5454]**WCC7K0CSZY00**[/COLOR][COLOR=#000000]-part9 [/COLOR]
scsi-0ATA_WDC_WD40EFRX-68N_WD-[COLOR=#ff5454]**WCC7K0CSZY00**[/COLOR]
scsi-0ATA_WDC_WD40EFRX-68N_WD-[COLOR=#ff5454]**WCC7K0CSZY00**[/COLOR][COLOR=#000000]-part1 [/COLOR]
scsi-0ATA_WDC_WD40EFRX-68N_WD-[COLOR=#ff5454]**WCC7K0CSZY00**[/COLOR][COLOR=#000000]-part9 [/COLOR]
scsi-1ATA_WDC_WD40EFRX-68N32N0_WD-[COLOR=#ff5454]**WCC7K0CSZY00**[/COLOR]
scsi-1ATA_WDC_WD40EFRX-68N32N0_WD-[COLOR=#ff5454]**WCC7K0CSZY00**[/COLOR][COLOR=#000000]-part1 [/COLOR]
scsi-1ATA_WDC_WD40EFRX-68N32N0_WD-[COLOR=#ff5454]**WCC7K0CSZY00**[/COLOR][COLOR=#000000]-part9 [/COLOR]
scsi-SATA_WDC_WD40EFRX-68N_WD-[COLOR=#ff5454]**WCC7K0CSZY00**[/COLOR]
scsi-SATA_WDC_WD40EFRX-68N_WD-[COLOR=#ff5454]**WCC7K0CSZY00**[/COLOR][COLOR=#000000]-part1 [/COLOR]
scsi-SATA_WDC_WD40EFRX-68N_WD-[COLOR=#ff5454]**WCC7K0CSZY00**[/COLOR][COLOR=#000000]-part9[/COLOR]
```[COLOR=#000000]
Did zfs not make 2 partition on the table?[/COLOR]
```


```[/FONT]```
[FONT=monospace][COLOR=#000000]Model: ATA WDC WD40EFRX-68N (scsi) [/COLOR]
Disk /dev/sde: 4001GB 
Sector size (logical/physical): 512B/4096B 
Partition Table: gpt 
Disk Flags:  

Number  Start   End     Size    File system  Name                  Flags 
 1      1049kB  4001GB  4001GB  zfs          zfs-c86ce3fb089ea106 
 9      4001GB  4001GB  8389kB[/FONT]
```

edit: i found how to fix the device identifier without rebuilding the array from scratch
[https://discourse.ubuntu.com/t/setup-a-zfs-storage-pool/13960](https://discourse.ubuntu.com/t/setup-a-zfs-storage-pool/13960)
```
sudo zpool export mypool && sudo zpool import -d /dev/disk/by-id mypool && zpool status
```


```
[FONT=monospace][COLOR=#000000]$ zpool status [/COLOR]
  pool: mypool 
 state: ONLINE 
  scan: scrub repaired 6.50M in 00:01:34 with 0 errors on Tue Aug  8 13:11:23 2023 
config: 

        NAME                        STATE     READ WRITE CKSUM 
        mypool                      ONLINE       0     0     0 
          mirror-0                  ONLINE       0     0     0 
            wwn-0x50014ee263e2b396  ONLINE       0     0     0 
            wwn-0x50014ee263ce2c81  ONLINE       0     0     0 
          mirror-1                  ONLINE       0     0     0 
            wwn-0x50014ee263e27e85  ONLINE       0     0     0 
            wwn-0x50014ee265d71fad  ONLINE       0     0     0 

errors: No known data errors
[/FONT][FONT=monospace][COLOR=#000000]$ ls -l /dev/disk/by-id/wwn*| grep -v 'part' [/COLOR]
lrwxrwxrwx 1 root root  9 Aug  8 11:01 /dev/disk/by-id/wwn-0x50014ee263ce2c81 -> ../../sdg 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 /dev/disk/by-id/wwn-0x50014ee263e27e85 -> ../../sdh 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 /dev/disk/by-id/wwn-0x50014ee263e2b396 -> ../../sdf 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 /dev/disk/by-id/wwn-0x50014ee265d71fad -> ../../sde 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 /dev/disk/by-id/wwn-0x55cd2e414f4a0b50 -> ../../sdc 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 /dev/disk/by-id/wwn-0x55cd2e414f4a6b29 -> ../../sda 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 /dev/disk/by-id/wwn-0x55cd2e414f4afc55 -> ../../sdd 
lrwxrwxrwx 1 root root  9 Aug  8 11:01 /dev/disk/by-id/wwn-0x55cd2e414f579528 -> ../../sdb
[/FONT]

```

---

### Post by MAFoElffen on 2023-08-08
Sort of... When it takes over a whole disk, it adds it's own partition, one for metadata.

If you had partitioned the disk with one partition and told it to use that, such as these, then everything would be within that partition.
```

Disk /dev/sda: 1.82 TiB, 2000398934016 bytes, 3907029168 sectors
Disk model: Samsung SSD 870 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 99518CF8-1EFB-450C-9702-C7397EA1812C

Device     Start        End    Sectors  Size Type
/dev/sda1   2048 3907029134 3907027087  1.8T Solaris reserved 1


Disk /dev/sdb: 1.82 TiB, 2000398934016 bytes, 3907029168 sectors
Disk model: Samsung SSD 870 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: C1007DFB-85BD-4288-88E0-FC72F3DE384C

Device     Start        End    Sectors  Size Type
/dev/sdb1   2048 3907029134 3907027087  1.8T Solaris reserved 1


Disk /dev/sdc: 1.82 TiB, 2000398934016 bytes, 3907029168 sectors
Disk model: Samsung SSD 870 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: E41B7FC0-7534-40F4-ABBD-439A9EA7970A

Device     Start        End    Sectors  Size Type
/dev/sdc1   2048 3907029134 3907027087  1.8T Solaris reserved 1


Disk /dev/sdd: 476.94 GiB, 512110190592 bytes, 1000215216 sectors
Disk model: Crucial_CT512MX1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 0898B436-3871-48AF-A559-E72C3DA31DC0

Device         Start        End   Sectors   Size Type
/dev/sdd1       2048      34815     32768    16M Microsoft reserved
/dev/sdd2      34816  998969343 998934528 476.3G Microsoft basic data
/dev/sdd3  998969344 1000212479   1243136   607M Windows recovery environment


Disk /dev/sde: 1.82 TiB, 2000398934016 bytes, 3907029168 sectors
Disk model: Samsung SSD 870 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 0CFD9F81-C126-44BD-BCD8-3AA801394880

Device     Start        End    Sectors  Size Type
/dev/sde1   2048 3907029134 3907027087  1.8T Solaris reserved 1


Disk /dev/sdf: 1.82 TiB, 2000398934016 bytes, 3907029168 sectors
Disk model: Samsung SSD 870 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: F81F302F-594E-4F3B-A2AF-76AF24CE5B02

Device     Start        End    Sectors  Size Type
/dev/sdf1   2048 3907029134 3907027087  1.8T Solaris reserved 1

```
The above are 5 SATA SSD disks, with one partition each, which are all members of a ZFS RAIDz2 Array... 

With ZFS, if you give it the whole raw disk, it does create a GPT partition table, and creates 2 partition: One for it's data, and the other at the end (8MB reserved partition) for it's metadata. ZFS will 'try' to determine the sectors present, and the blocksize (more on this in the next paragraph) to do this. It would then use the smallest & slowest object as it's reference point... The problem then comes up when you add a drive to the pool, and it is smaller and/or slower.

This subject goes back and forth between people and groups. Some say that if you do that, then ZFS Sets internal flags, telling it that it owns all parts of the disk, and turns on 'optimizations' that it would not normally turn on it it didn't... That used to be true, but is no longer such. When drives got bigger, the block sizes got bigger, and the firmware started lying about what blocksize it had underneath the covers. They did this to be compliant with a certain Windows OS, which required it to report that it was a certain block size. But translated it in their firmware to what they really were. It can cause problems when you give something unbound containers. I'll leave it at that.

RE: [https://jrs-s.net/2018/04/11/primer-how-data-is-stored-on-disk-with-zfs/](https://jrs-s.net/2018/04/11/primer-how-data-is-stored-on-disk-with-zfs/)

Creating your own partition sizes, you have total control of the size of what you are using. That way you can ensure that you are giving something the size you think you are. With ZFS properties, you can control the ashift and recordsize... and any other properties. Doing it that way, the metadata is created within the partition you tell it to use. years of experience show me this is more durable, doing it this way.

I know what it says in the doc's. I don't always beieve that and do my own tests, benchmarks, and take note of what others get when I help them. There are differences that seem to be important in how they work, and what makes them readily dependable. I learn from my mistakes. LOL. And sometimes when someone says "That won't work", If it seems posisble, I'll try it just to see for myself what really happens.

---

### Post by MAFoElffen on 2023-08-08
I think you had asked how I change disks...

Usually if a disk fails, the disk is marked as failed and the pool will go into a degraded mode...

In that case, if I have a question whether it is actually failed or just got some write error, I will use zpool clear to resilver it, then use zpool scrub to look for and repair errors. ...All while online.

I have had disks fail, where I then use the zpool replace command to replace the old disk with a new disk. That will remove the old disk from the array,  the new disk will resilver, and when finished, bring itself online... 

If I am upgrading a RAIDz array to larger disks, then I ensure the autoexpand property is set to on, offline a disk, then replace it with a larger disk... Wait for that disk to resilver, then continue with the next disk. After each resilver, while bringing it online, ZFS recalc's it's stat's, looking at all it's members. When all the disks are replaced, ZFS will compute the stat's seeing all members as being "larger" and autoexpand it's size/capacity.

Some Doc's say to offline the pool to replace a disk. Replace the disk. Then bring the pool back online. I have never really had to do it that, way, but I know that option is still an alternative.

Note that here is a beta feature where you can expand the number (add disks) of disks in an array, without destroying and re-creating that array. It's still in beta. And ven when it does that, it does not load-balance what is there on it's own. It just continues what is written as new, in the new config. To load-balance, you would still have to back-off and reload/rewrite the data fresh. You can always add another vdev of disks to a pool to expand the pool size...

---

### Post by pqwoerituytrueiwoq on 2023-08-08
> **MAFoElffen said:**
> 
With ZFS, if you give it the whole raw disk, it does create a GPT partition table, and creates 2 partition: One for it's data, and the other at the end (8MB reserved partition) for it's metadata. ZFS will 'try' to determine the sectors present, and the blocksize (more on this in the next paragraph) to do this. It would then use the smallest & slowest object as it's reference point... **The problem then comes up when you add a drive to the pool, and it is smaller and/or slower.**
then for the time being i should be good, no plans to add smaller or slower drives, infant i managed to find another 4 drives of the same model priced reasonable, so i will have 4 cold spares Saturday (well after i complete all the smart test...)

if i mix models i would add a 8tb as a parity mirror, and that drive will SUCK to change out... on that note my SSDs will suck to swap out, but i have 6 cold spares

i made sure i was getting CMR drives after the SMR issue came up in the news

as for the performance with my measly 1 Gbps network, looks like i am using 86% of my bandwidth and 70-100% of one CPU core (looking in htop), i think i am CPU limited (the origin can read @~200MB/s)
```

chad@niceserver:/mnt/HDD$ sudo wget http://10.0.0.50:81/2023-05-03-raspios-bullseye-armhf-lite.img  
--2023-08-08 22:35:38--  http://10.0.0.50:81/2023-05-03-raspios-bullseye-armhf-lite.img 
Connecting to 10.0.0.50:81... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 1967128576 (1.8G) 
Saving to: ‘2023-05-03-raspios-bullseye-armhf-lite.img’ 

2023-05-03-raspios-bullseye-armhf-li 100%[=====================================================================>]   1.83G   108MB/s    in 18s      

2023-08-08 22:35:57 (102 MB/s) - ‘2023-05-03-raspios-bullseye-armhf-lite.img’ saved [1967128576/1967128576] 

chad@niceserver:/mnt/HDD$ sudo rm 2023-05-03-raspios-bullseye-armhf-lite.img  
chad@niceserver:/mnt/HDD$ iperf -s 
------------------------------------------------------------ 
Server listening on TCP port 5001 
TCP window size:  128 KByte (default) 
------------------------------------------------------------ 
[  1] local 10.0.0.69 port 5001 connected with 10.0.0.50 port 41078 
[ ID] Interval       Transfer     Bandwidth 
[  1] 0.0000-10.0237 sec  1.10 GBytes   941 Mbits/sec 

```

---

### Post by MAFoElffen on 2023-08-09
This is one of the utilities I use for bench-marking my pools... I change directory to inside the pool I want to test, then from the command line, do: 
```

fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting

```
Here is the results of 3 of my pools:
```

mafoelffen@Mikes-B460M:/KVM_Pool$ fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][100.0%][w=2508MiB/s][w=2508 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=456840: Wed Aug  9 19:06:45 2023
  write: IOPS=2315, BW=2315MiB/s (2428MB/s)(10.0GiB/4423msec); 0 zone resets
    slat (usec): min=112, max=16942, avg=382.75, stdev=253.10
    clat (usec): min=3, max=487029, avg=13238.93, stdev=26334.70
     lat (usec): min=488, max=487585, avg=13622.21, stdev=26376.43
    clat percentiles (msec):
     |  1.00th=[    5],  5.00th=[    5], 10.00th=[    5], 20.00th=[    6],
     | 30.00th=[    7], 40.00th=[   12], 50.00th=[   13], 60.00th=[   15],
     | 70.00th=[   17], 80.00th=[   18], 90.00th=[   19], 95.00th=[   19],
     | 99.00th=[   20], 99.50th=[   23], 99.90th=[  485], 99.95th=[  485],
     | 99.99th=[  489]
   bw (  MiB/s): min= 1798, max= 3144, per=100.00%, avg=2484.40, stdev=422.77, samples=8
   iops        : min= 1798, max= 3144, avg=2484.25, stdev=422.88, samples=8
  lat (usec)   : 4=0.01%, 10=0.03%, 250=0.01%, 500=0.02%, 750=0.02%
  lat (usec)   : 1000=0.02%
  lat (msec)   : 2=0.09%, 4=0.21%, 10=37.94%, 20=60.72%, 50=0.63%
  lat (msec)   : 500=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=547, max=547, avg=547.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  548],  5.00th=[  548], 10.00th=[  548], 20.00th=[  548],
     | 30.00th=[  548], 40.00th=[  548], 50.00th=[  548], 60.00th=[  548],
     | 70.00th=[  548], 80.00th=[  548], 90.00th=[  548], 95.00th=[  548],
     | 99.00th=[  548], 99.50th=[  548], 99.90th=[  548], 99.95th=[  548],
     | 99.99th=[  548]
  cpu          : usr=14.11%, sys=76.53%, ctx=2175, majf=14, minf=13
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=2315MiB/s (2428MB/s), 2315MiB/s-2315MiB/s (2428MB/s-2428MB/s), io=10.0GiB (10.7GB), run=4423-4423msec

mafoelffen@Mikes-B460M:/data$ fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]                          
TEST: (groupid=0, jobs=1): err= 0: pid=504929: Wed Aug  9 19:15:11 2023
  write: IOPS=1423, BW=1424MiB/s (1493MB/s)(10.0GiB/7193msec); 0 zone resets
    slat (usec): min=106, max=9390, avg=478.34, stdev=533.55
    clat (nsec): min=1127, max=2309.7M, avg=21623319.58, stdev=126295684.72
     lat (usec): min=142, max=2310.9k, avg=22101.89, stdev=126397.93
    clat percentiles (msec):
     |  1.00th=[    5],  5.00th=[    5], 10.00th=[    6], 20.00th=[    6],
     | 30.00th=[    6], 40.00th=[    6], 50.00th=[    8], 60.00th=[   10],
     | 70.00th=[   11], 80.00th=[   32], 90.00th=[   35], 95.00th=[   54],
     | 99.00th=[   77], 99.50th=[   81], 99.90th=[ 2299], 99.95th=[ 2299],
     | 99.99th=[ 2299]
   bw (  MiB/s): min=  438, max= 5246, per=100.00%, avg=1993.80, stdev=1673.96, samples=10
   iops        : min=  438, max= 5246, avg=1993.80, stdev=1673.96, samples=10
  lat (usec)   : 2=0.02%, 4=0.03%, 250=0.03%, 500=0.05%, 750=0.04%
  lat (usec)   : 1000=0.03%
  lat (msec)   : 2=0.20%, 4=0.37%, 10=66.75%, 20=9.06%, 50=17.63%
  lat (msec)   : 100=5.50%, >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=645, max=645, avg=645.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  644],  5.00th=[  644], 10.00th=[  644], 20.00th=[  644],
     | 30.00th=[  644], 40.00th=[  644], 50.00th=[  644], 60.00th=[  644],
     | 70.00th=[  644], 80.00th=[  644], 90.00th=[  644], 95.00th=[  644],
     | 99.00th=[  644], 99.50th=[  644], 99.90th=[  644], 99.95th=[  644],
     | 99.99th=[  644]
  cpu          : usr=5.20%, sys=25.58%, ctx=21306, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=1424MiB/s (1493MB/s), 1424MiB/s-1424MiB/s (1493MB/s-1493MB/s), io=10.0GiB (10.7GB), run=7193-7193msec

mafoelffen@msi-ubuntu:/tmp$ fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
TEST: Laying out IO file (1 file / 2048MiB)
Jobs: 1 (f=1)
TEST: (groupid=0, jobs=1): err= 0: pid=4094866: Wed Aug  9 19:12:00 2023
  write: IOPS=4892, BW=4892MiB/s (5130MB/s)(10.0GiB/2093msec); 0 zone resets
    slat (usec): min=103, max=1223, avg=192.83, stdev=66.96
    clat (nsec): min=1317, max=116400k, avg=6295756.03, stdev=6260864.91
     lat (usec): min=152, max=116672, avg=6488.67, stdev=6281.92
    clat percentiles (msec):
     |  1.00th=[    4],  5.00th=[    5], 10.00th=[    5], 20.00th=[    6],
     | 30.00th=[    6], 40.00th=[    6], 50.00th=[    6], 60.00th=[    6],
     | 70.00th=[    6], 80.00th=[    7], 90.00th=[    9], 95.00th=[   10],
     | 99.00th=[   16], 99.50th=[   16], 99.90th=[  115], 99.95th=[  116],
     | 99.99th=[  116]
   bw (  MiB/s): min= 4582, max= 5274, per=100.00%, avg=4984.50, stdev=304.27, samples=4
   iops        : min= 4582, max= 5274, avg=4984.50, stdev=304.27, samples=4
  lat (usec)   : 2=0.04%, 250=0.05%, 500=0.07%, 750=0.10%, 1000=0.06%
  lat (msec)   : 2=0.31%, 4=3.22%, 10=92.40%, 20=3.45%, 250=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=619, max=619, avg=619.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  620],  5.00th=[  620], 10.00th=[  620], 20.00th=[  620],
     | 30.00th=[  620], 40.00th=[  620], 50.00th=[  620], 60.00th=[  620],
     | 70.00th=[  620], 80.00th=[  620], 90.00th=[  620], 95.00th=[  620],
     | 99.00th=[  620], 99.50th=[  620], 99.90th=[  620], 99.95th=[  620],
     | 99.99th=[  620]
  cpu          : usr=17.30%, sys=74.09%, ctx=1571, majf=14, minf=14
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=4892MiB/s (5130MB/s), 4892MiB/s-4892MiB/s (5130MB/s-5130MB/s), io=10.0GiB (10.7GB), run=2093-2093msec

```
Hmmm. Reading with more interest. LOL. Is that Raspberry Pi I see? I have a RaspPi 4 that I have in my living room, that boots from m.2 NVMe....

4 spares to your 4 spares? For what storage capacity? And what is this on with what memory RAM?

Have you thought about doing RAIDz2 or RAIDz3? You can lose 2 drives with RAIDz2, 3 drives with RAIDz3. With RAID10, you can lose 2 drives, but not of the same vDev, because you are striped across the vdevs. 

I use RAIDz2. I use that as both a balance of dependability, and the performance increase. The speed is amazing. I just did a RAIDz Pool tuning thread, where I got someone's ZFS spun-disk RAIDz3 pool up to 500MB/s writes. It started out as only being about 15MB/s. RE: [https://ubuntuforums.org/showthread.php?t=2486010&highlight=zfs+performance](https://ubuntuforums.org/showthread.php?t=2486010&highlight=zfs+performance). Mine,  even in a degraded state, is over 1.3GB/s sustained writes.

What were the disk sizes again? Was going to do the math, to compare capacities and play with the numbers...

---

### Post by pqwoerituytrueiwoq on 2023-08-09
I was using a raspberry pi model B, then a B+, finally i think a 2B+ (the 1st one to get a better than 100Mbps NIC)

at this time i have retried the Pis from active duty, and replaced them with PICOs and a [x86 server]("https://imgur.com/a/bJsP80E") that does way more than the Pi did 

I have 4 x 4TB WD RED drives (WD40EFRX; the CMR model) in my server (raid10 style) connected to a [JMB585 M.2 sata card]("https://www.amazon.com/Internal-Non-Raid-Adapter-Desktop-Support/dp/B07T3RMFFT") (i got a 'referb' on ebay for $20)

i have 4 cold spares on the way of the same model

about 300MB/s would be what i would expect for 2 of these HDDs in raid 0

```
[FONT=monospace][COLOR=#54ff54]**chad@niceserver**[/COLOR][COLOR=#000000]:[/COLOR][/FONT][FONT=monospace][COLOR=#5454ff]**/mnt/HDD/testDir**[/COLOR][COLOR=#000000]$ fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporti[/COLOR]ng 
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32 
fio-3.28 
Starting 1 process 
TEST: Laying out IO file (1 file / 2048MiB) 
Jobs: 1 (f=1): [W(1)][21.9%][w=269MiB/s][w=269 IOPS][eta 00m:25s] 
Jobs: 1 (f=1): [W(1)][37.1%][w=296MiB/s][w=296 IOPS][eta 00m:22s]  
Jobs: 1 (f=1): [W(1)][52.8%][w=245MiB/s][w=245 IOPS][eta 00m:17s]  
Jobs: 1 (f=1): [W(1)][67.6%][w=295MiB/s][w=295 IOPS][eta 00m:12s]  
Jobs: 1 (f=1): [W(1)][83.8%][w=294MiB/s][w=294 IOPS][eta 00m:06s]  
Jobs: 1 (f=1): [W(1)][97.4%][w=213MiB/s][w=213 IOPS][eta 00m:01s]  
Jobs: 1 (f=1): [W(1)][97.6%][eta 00m:01s]                          
TEST: (groupid=0, jobs=1): err= 0: pid=1164784: Wed Aug  9 23:38:01 2023 
  write: IOPS=245, BW=245MiB/s (257MB/s)(10.0GiB/41755msec); 0 zone resets 
    slat (usec): min=196, max=2448.0k, avg=3612.79, stdev=25587.13 
    clat (usec): min=2, max=4781.5k, avg=124752.81, stdev=293365.24 
     lat (usec): min=241, max=4784.8k, avg=128366.62, stdev=294586.57 
    clat percentiles (msec): 
     |  1.00th=[   11],  5.00th=[   12], 10.00th=[   16], 20.00th=[   88], 
     | 30.00th=[  100], 40.00th=[  102], 50.00th=[  105], 60.00th=[  108], 
     | 70.00th=[  113], 80.00th=[  124], 90.00th=[  155], 95.00th=[  190], 
     | 99.00th=[  253], 99.50th=[ 2500], 99.90th=[ 4732], 99.95th=[ 4799], 
     | 99.99th=[ 4799] 
   bw (  KiB/s): min=12288, max=1247232, per=100.00%, avg=291664.46, stdev=173447.16, samples=70 
   iops        : min=   12, max= 1218, avg=284.83, stdev=169.38, samples=70 
  lat (usec)   : 4=0.01%, 10=0.04%, 250=0.01%, 500=0.01%, 750=0.01% 
  lat (usec)   : 1000=0.01% 
  lat (msec)   : 2=0.03%, 4=0.11%, 10=0.66%, 20=11.60%, 50=2.38% 
  lat (msec)   : 100=18.94%, 250=65.07%, 500=0.21%, 1000=0.30%, >=2000=0.61% 
  fsync/fdatasync/sync_file_range: 
    sync (nsec): min=1382, max=1382, avg=1382.00, stdev= 0.00 
    sync percentiles (nsec): 
     |  1.00th=[ 1384],  5.00th=[ 1384], 10.00th=[ 1384], 20.00th=[ 1384], 
     | 30.00th=[ 1384], 40.00th=[ 1384], 50.00th=[ 1384], 60.00th=[ 1384], 
     | 70.00th=[ 1384], 80.00th=[ 1384], 90.00th=[ 1384], 95.00th=[ 1384], 
     | 99.00th=[ 1384], 99.50th=[ 1384], 99.90th=[ 1384], 99.95th=[ 1384], 
     | 99.99th=[ 1384] 
  cpu          : usr=1.02%, sys=8.73%, ctx=76900, majf=1, minf=15 
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0% 
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0% 
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0% 
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0 
     latency   : target=0, window=0, percentile=100.00%, depth=32 

Run status group 0 (all jobs): 
  WRITE: bw=245MiB/s (257MB/s), 245MiB/s-245MiB/s (257MB/s-257MB/s), io=10.0GiB (10.7GB), run=41755-41755msec
[/FONT]
```

---

### Post by MAFoElffen on 2023-08-10
I like your system. Well thought out.

I think a good read for you would be this article: [https://calomel.org/zfs_raid_speed_capacity.html](https://calomel.org/zfs_raid_speed_capacity.html)

With your system and your drives, I threw the numbers together and came up with this:
```

Mirror x 2 x 2 + 4x 4TB Drives, 4 in reserve (spares)... <*Current>
7.722351TB

RAIDz2, with hot spares
4 drives - 7.488341TB
5 drives - 11.440520TB
6 drives - 15.444702TB
7 drives - 17.930057TB

RAIDz3, with hot spares.
5 drives - 7.722351TB
6 drives - 10.902143TB
7 drives - 15.368620TB

```
Both those, options, you end up with more storage capacity, that is less at risk. With RAIDz2, you can lose 'any' 2 drives and the write speed would be fastest. With RAIDz3, you can lose 'any' 3 drives and Write speed would be faster than RAID10, but slower than RAIDz2. Both of those (double and triple parity), are safer than the single striping of RAID10 between the mirrors.

Just some food for thought. You have the resources there to try them and see for yourself. It would cost you nothing but the time. That and you could learn by playing with those, right? You could use one-two of the drives for compressed backups... While using one to add to the pool, and one-as a hot spare... That was my thoughts, tempered on things you might find out for yourself with those.

To do RAIDz2, the minimum would be 4 drives. That would put you at just below your current capacity, but with 2 parity drives. You don't see the jump in benefits until 5 drives, where it is going to be more at home. I do vdevs up to 8-11 drives, then add more vdevs in groups of 5-11 drives above that. I usually follow a rule of thumb of ^2 or 2*+1 (5, 7, 9...) as potentially going to be the best performance... 

But the minimum 4 drive RAIDz2 is very fast. Do not discount that.

EDIT: A good recovery plan is one that you have tested to ensure it works. It is early and you are in the mood for testing and changes.

As test, pull a cable on a drive and let it fail and degrade. Reboot the machine with it connected back up. Clear the errors... And have it resilver. See how long it takes to complete. See that you are still online while that is still happening. That is your real-world results.

For 4TB spun drives, I would expect about 40-50 minutes, depending on what is written to them.

EDIT2:
A note on memory. My rule of thumb for ZFS is ((capacity in TB's *2) + 1)= RAM in GB's required.

---

### Post by pqwoerituytrueiwoq on 2023-08-11
With the amount of data i have atm i could just raid 1 the array, that just seems overkill with over 3 drives, i really do not want to go to 5 drives cause if i mount the drive in the case it becomes a PITA to change and that is how you end up with a unsecured drive on the bottom of a case, if raidz2 would any 2 drives to fail and not bring the array off line and only cost a ~200GB that sounds like a nice option (raid10 is easier for me to understand how it works)

---

### Post by MAFoElffen on 2023-08-11
> **pqwoerituytrueiwoq said:**
> 
...
if raidz2 would any 2 drives to fail and not bring the array off line and only cost a ~200GB that sounds like a nice option
...

Yes, any two drives can go offline and it would be degraded, but still online.

Some  of my machines have 4 drives in RAIDz2, One of those, I was planning to add another drive, that I had ordered. What I didn't know at the time was that Native Command Queing (NCQ) was causing errors on my drives. Once I toggled that off, those errors stopped coming up... But anyway, before that, I have had one drive offline and not even noticed until I looked at my reports. It was still running great, with great performance.

That experience taught me a few things. One, with ZFS, that I could use errors to trigger warnings to me, before a drive actually drops out.That and with RAIDz2, that a degraded Array was trivial and not much to worry about. It was very easy to recover from, and I could use my array (online) while I did it. Because the array was Samsung QVO 870's, with SLOG &  L2ARC cache's the array only takes 11 minutes to resilver.

---


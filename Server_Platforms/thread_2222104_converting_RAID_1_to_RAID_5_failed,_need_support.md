---
title: "converting RAID 1 to RAID 5 failed, need support :/"
date: 2014-05-05
forum: Server Platforms
---

### Post by Christophe_Stenstr on 2014-05-05
Hello,

I tried to convert a RAID 1 array to RAID 5. The initial plan was to the move while keeping the data on the disks. I followed this tutorial [http://csgeek-random.blogspot.fr/2012/11/converting-from-raid-1-to-raid-5.html](http://csgeek-random.blogspot.fr/2012/11/converting-from-raid-1-to-raid-5.html) .

I'm running Ubuntu 14.04

After this step:[INDENT][COLOR=#666666][FONT=Lora]#update this as appropriate. mdadm --create /dev/md0 --level=5 --raid-devices=2 /dev/sda1 /dev/sdd1
[/FONT][/COLOR][/INDENT]
I couldn't mount my RAID array anymore. As a noob, I decided to continue to follow the tutorial anyway.

After this step:[INDENT][COLOR=#666666][FONT=Lora]mdadm --add /dev/md0 /dev/sdb1
mdadm --grow /dev/md0 --raid-devices=3
[/FONT][/COLOR][/INDENT]
I couldn't mount my RAID array either (please note that I added [FONT=Menlo]sudo sfdisk -d /dev/sdd | sudo sfdisk /dev/sdc[/FONT] just before this step). At this time I started to get very worried...
The mdadm /dev/md0 array resync was running. At this time I decided to reboot the server with the "reboot" command but the computer got stucked... I waited a long wait I pushed the reset button on the front of the computer.

After reboot, there is a raid 5 array running on /dev/md127 instead of /dev/md0 _AND NO REBUILD/RESYNC ANYMORE_.
I modified mdadm.conf to reconfigure it on /dev/md0 with no success.
I can not mount this raid array, I get this message[INDENT][FONT=Menlo]mount: wrong fs type, bad option, bad superblock on /dev/md127,[/FONT][/INDENT]
[FONT=Menlo]       missing codepage or helper program, or other error[/FONT]
[FONT=Menlo]       In some cases useful info is found in syslog - try[/FONT]
[FONT=Menlo]       dmesg | tail  or so
[/FONT]

So I think that I lost these datas but as a noob I am not sure.
_So the question is, are these datas lost or not?_

Here are some datas that maybe could help you to analyse:
```


[FONT=Menlo]spinal@spinal-server:~$ sudo mount /data_RAID/[/FONT]
[FONT=Menlo]mount: wrong fs type, bad option, bad superblock on /dev/md127,[/FONT]
[FONT=Menlo]       missing codepage or helper program, or other error[/FONT]
[FONT=Menlo]       In some cases useful info is found in syslog - try[/FONT]
[FONT=Menlo]       dmesg | tail  or so[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]spinal@spinal-server:~$ cat /proc/mdstat [/FONT]
[FONT=Menlo]Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] [/FONT]
[FONT=Menlo]md127 : active (auto-read-only) raid5 sde1[0] sdb1[2] sdd1[3][/FONT]
[FONT=Menlo]      2930009088 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU][/FONT]

[FONT=Menlo]unused devices: <none>[/FONT]
[FONT=Menlo]spinal@spinal-server:~$ sudo mdadm --detail /dev/md127[/FONT]
[FONT=Menlo]/dev/md127:[/FONT]
[FONT=Menlo]        Version : 1.2[/FONT]
[FONT=Menlo]  Creation Time : Sat May  3 14:36:38 2014[/FONT]
[FONT=Menlo]     Raid Level : raid5[/FONT]
[FONT=Menlo]     Array Size : 2930009088 (2794.27 GiB 3000.33 GB)[/FONT]
[FONT=Menlo]  Used Dev Size : 1465004544 (1397.14 GiB 1500.16 GB)[/FONT]
[FONT=Menlo]   Raid Devices : 3[/FONT]
[FONT=Menlo]  Total Devices : 3[/FONT]
[FONT=Menlo]    Persistence : Superblock is persistent[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]    Update Time : Mon May  5 09:53:20 2014[/FONT]
[FONT=Menlo]          State : clean [/FONT]
[FONT=Menlo] Active Devices : 3[/FONT]
[FONT=Menlo]Working Devices : 3[/FONT]
[FONT=Menlo] Failed Devices : 0[/FONT]
[FONT=Menlo]  Spare Devices : 0[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]         Layout : left-symmetric[/FONT]
[FONT=Menlo]     Chunk Size : 512K[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]           Name : spinal-server:0  (local to host spinal-server)[/FONT]
[FONT=Menlo]           UUID : dfb6ce9e:cf4f0971:2a11cb2b:427f8d1d[/FONT]
[FONT=Menlo]         Events : 292[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]    Number   Major   Minor   RaidDevice State[/FONT]
[FONT=Menlo]       0       8       65        0      active sync   /dev/sde1[/FONT]
[FONT=Menlo]       2       8       17        1      active sync   /dev/sdb1[/FONT]
[FONT=Menlo]       3       8       49        2      active sync   /dev/sdd1[/FONT]
[FONT=Menlo]spinal@spinal-server:~$ sudo lshw -c disk[/FONT]
[FONT=Menlo]  *-disk                  [/FONT]
[FONT=Menlo]       description: ATA Disk[/FONT]
[FONT=Menlo]       product: WDC WD20EARS-00M[/FONT]
[FONT=Menlo]       vendor: Western Digital[/FONT]
[FONT=Menlo]       physical id: 0.0.0[/FONT]
[FONT=Menlo]       bus info: scsi@0:0.0.0[/FONT]
[FONT=Menlo]       logical name: /dev/sda[/FONT]
[FONT=Menlo]       version: 51.0[/FONT]
[FONT=Menlo]       serial: WD-WMAZA3007810[/FONT]
[FONT=Menlo]       size: 1863GiB (2TB)[/FONT]
[FONT=Menlo]       capabilities: partitioned partitioned:dos[/FONT]
[FONT=Menlo]       configuration: ansiversion=5 sectorsize=512 signature=00058676[/FONT]
[FONT=Menlo]  *-disk[/FONT]
[FONT=Menlo]       description: ATA Disk[/FONT]
[FONT=Menlo]       product: WDC WD15EADS-00P[/FONT]
[FONT=Menlo]       vendor: Western Digital[/FONT]
[FONT=Menlo]       physical id: 0.0.0[/FONT]
[FONT=Menlo]       bus info: scsi@1:0.0.0[/FONT]
[FONT=Menlo]       logical name: /dev/sdb[/FONT]
[FONT=Menlo]       version: 01.0[/FONT]
[FONT=Menlo]       serial: WD-WCAVU0245500[/FONT]
[FONT=Menlo]       size: 1397GiB (1500GB)[/FONT]
[FONT=Menlo]       capabilities: partitioned partitioned:dos[/FONT]
[FONT=Menlo]       configuration: ansiversion=5 sectorsize=512 signature=0005c17a[/FONT]
[FONT=Menlo]  *-disk[/FONT]
[FONT=Menlo]       description: ATA Disk[/FONT]
[FONT=Menlo]       product: Patriot Warp V2[/FONT]
[FONT=Menlo]       physical id: 0.0.0[/FONT]
[FONT=Menlo]       bus info: scsi@3:0.0.0[/FONT]
[FONT=Menlo]       logical name: /dev/sdc[/FONT]
[FONT=Menlo]       version: 02.1[/FONT]
[FONT=Menlo]       serial: MK04093706141000B[/FONT]
[FONT=Menlo]       size: 29GiB (32GB)[/FONT]
[FONT=Menlo]       capabilities: partitioned partitioned:dos[/FONT]
[FONT=Menlo]       configuration: ansiversion=5 sectorsize=512 signature=fbabeb3d[/FONT]
[FONT=Menlo]  *-disk[/FONT]
[FONT=Menlo]       description: ATA Disk[/FONT]
[FONT=Menlo]       product: WDC WD20EFRX-68E[/FONT]
[FONT=Menlo]       vendor: Western Digital[/FONT]
[FONT=Menlo]       physical id: 0.0.0[/FONT]
[FONT=Menlo]       bus info: scsi@4:0.0.0[/FONT]
[FONT=Menlo]       logical name: /dev/sdd[/FONT]
[FONT=Menlo]       version: 80.0[/FONT]
[FONT=Menlo]       serial: WD-WMC4M2731898[/FONT]
[FONT=Menlo]       size: 1863GiB (2TB)[/FONT]
[FONT=Menlo]       capabilities: partitioned partitioned:dos[/FONT]
[FONT=Menlo]       configuration: ansiversion=5 sectorsize=4096[/FONT]
[FONT=Menlo]  *-disk[/FONT]
[FONT=Menlo]       description: ATA Disk[/FONT]
[FONT=Menlo]       product: WDC WD20EFRX-68A[/FONT]
[FONT=Menlo]       vendor: Western Digital[/FONT]
[FONT=Menlo]       physical id: 0.0.0[/FONT]
[FONT=Menlo]       bus info: scsi@5:0.0.0[/FONT]
[FONT=Menlo]       logical name: /dev/sde[/FONT]
[FONT=Menlo]       version: 80.0[/FONT]
[FONT=Menlo]       serial: WD-WMC301950734[/FONT]
[FONT=Menlo]       size: 1863GiB (2TB)[/FONT]
[FONT=Menlo]       capabilities: partitioned partitioned:dos[/FONT]
[FONT=Menlo]       configuration: ansiversion=5 sectorsize=4096[/FONT]
[FONT=Menlo]  *-cdrom[/FONT]
[FONT=Menlo]       description: DVD-RAM writer[/FONT]
[FONT=Menlo]       product: BDDVDRW CH08LS10[/FONT]
[FONT=Menlo]       vendor: HL-DT-ST[/FONT]
[FONT=Menlo]       physical id: 0.0.0[/FONT]
[FONT=Menlo]       bus info: scsi@6:0.0.0[/FONT]
[FONT=Menlo]       logical name: /dev/cdrom[/FONT]
[FONT=Menlo]       logical name: /dev/sr0[/FONT]
[FONT=Menlo]       version: 1.00[/FONT]
[FONT=Menlo]       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram[/FONT]
[FONT=Menlo]       configuration: ansiversion=5 status=nodisc[/FONT]
[FONT=Menlo]spinal@spinal-server:~$ [/FONT]

```

I hope someone will help me, and thank by advance :)

---

### Post by TheFu on 2014-05-05
I would never attempt an in-place RAID change, especially without a backup. RAID is not a substitute for backups - EVER.

Delete all the RAID devices, create the RAID5 that you want, restore the data from the backup that you made prior to starting this undertaking.

Oh ... any fdisk, cfdisk, sfdisk are deprecated thanks to GPT and 2TB+ HDDs. Use parted, gdisk and gparted going forward.  If your HDDs are 2TB (or less) and MBR partitioned, no harm (due only to fdisk/cfdisk/sfdisk) happened. That doesn't mean incorrect use didn't happen, however.  It is just easier to always use GPT and 4K-sector knowledgeable tools now.

If you don't have a backup ... er ... I haven't a clue.

---


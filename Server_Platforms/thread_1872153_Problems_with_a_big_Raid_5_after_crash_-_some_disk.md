---
title: "Problems with a big Raid 5 after crash - some disks with efi+gpt"
date: 2011-10-30
forum: Server Platforms
---

### Post by nullzone on 2011-10-30
Hey there friends,

   I am getting a problem that it making my weekend a nightmare.

   I have a server with a big raid5 software formed by 6x2TB SATA disks.
   2 of those 6 HD had GPT partitions + EFI (since those 2 HDs had a diferent geometry and forced me to do 2 TB partition in that way). In conclusión, I had 6x2TB similar partitions (2 of then coming from 2 disk with EFI/GPT).

   Well, the system HD crashed and I did reinstall it. Problem is that I can only see 4 of those 6 partitons now (after reinstall) in the /dev . It likes that there are there but ... ??? why arent they created on boot in the /dev to make use of them?

I have used the original Ubuntu version that I had installed (9.10) and a 10.04 with the same result.

Also, it likes that sdh is acting like a MBR disk with a GPT partion, nor a EFI.

Honesty, I'd love any kind of help at this point ... 

```

---------
root@servidor:~# grep -i part /boot/config-2.6.31-14-server | grep -i efi 
CONFIG_EFI_PARTITION=y
---------
root@servidor:~# fdisk -l

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders
Units = cylinders of 5103 * 512 = 2612736 bytes
Disk identifier: 0xe1e283ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      765634  1953513560   83  Linux

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders
Units = cylinders of 5103 * 512 = 2612736 bytes
Disk identifier: 0x1a868d23

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      765634  1953513560   83  Linux

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1           1         319+  ee  GPT

Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders
Units = cylinders of 5103 * 512 = 2612736 bytes
Disk identifier: 0x00050392

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      765634  1953513560   83  Linux

Disk /dev/sdg: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders
Units = cylinders of 5103 * 512 = 2612736 bytes
Disk identifier: 0x9a6fe201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1      765634  1953513560   83  Linux

Disk /dev/sdh: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaabc6a43

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1      267350  2147483647+  ee  GPT


---------

root@servidor:~# sfdisk -l

Disk /dev/sdd: 243201 cylinders, 255 heads, 63 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/81/63 (instead of 243201/255/63).
For this listing I'll assume that geometry.
Units = cylinders of 2612736 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdd1          0+ 765633- 765634- 1953513560   83  Linux
                end: (c,h,s) expected (1023,80,63) found (513,80,63)
/dev/sdd2          0       -       0          0    0  Empty
/dev/sdd3          0       -       0          0    0  Empty
/dev/sdd4          0       -       0          0    0  Empty

Disk /dev/sde: 243201 cylinders, 255 heads, 63 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/81/63 (instead of 243201/255/63).
For this listing I'll assume that geometry.
Units = cylinders of 2612736 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sde1          0+ 765633- 765634- 1953513560   83  Linux
                end: (c,h,s) expected (1023,80,63) found (513,80,63)
/dev/sde2          0       -       0          0    0  Empty
/dev/sde3          0       -       0          0    0  Empty
/dev/sde4          0       -       0          0    0  Empty

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util sfdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 243201 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdc1          0+      0-      1-       319+  ee  GPT
                start: (c,h,s) expected (0,0,2) found (1023,254,63)
                end: (c,h,s) expected (0,10,10) found (1023,254,63)
/dev/sdc2          0       -       0          0    0  Empty
/dev/sdc3          0       -       0          0    0  Empty
/dev/sdc4          0       -       0          0    0  Empty

Disk /dev/sdf: 243201 cylinders, 255 heads, 63 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/81/63 (instead of 243201/255/63).
For this listing I'll assume that geometry.
Units = cylinders of 2612736 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdf1          0+ 765633- 765634- 1953513560   83  Linux
                end: (c,h,s) expected (1023,80,63) found (513,80,63)
/dev/sdf2          0       -       0          0    0  Empty
/dev/sdf3          0       -       0          0    0  Empty
/dev/sdf4          0       -       0          0    0  Empty

Disk /dev/sdg: 243201 cylinders, 255 heads, 63 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/81/63 (instead of 243201/255/63).
For this listing I'll assume that geometry.
Units = cylinders of 2612736 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdg1          0+ 765633- 765634- 1953513560   83  Linux
                end: (c,h,s) expected (1023,80,63) found (513,80,63)
/dev/sdg2          0       -       0          0    0  Empty
/dev/sdg3          0       -       0          0    0  Empty
/dev/sdg4          0       -       0          0    0  Empty

Disk /dev/sdh: 243201 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdh1          0+ 267349- 267350- 2147483647+  ee  GPT
                start: (c,h,s) expected (0,0,2) found (0,0,1)
/dev/sdh2          0       -       0          0    0  Empty
/dev/sdh3          0       -       0          0    0  Empty
/dev/sdh4          0       -       0          0    0  Empty

Disk /dev/sdi: 91201 cylinders, 255 heads, 63 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/2/4 (instead of 91201/255/63).
For this listing I'll assume that geometry.
Units = cylinders of 4096 bytes, blocks of 1024 bytes, counting from 0

```

---

### Post by ian dobson on 2011-10-30
Hi,

Have you created your mdadm.conf file and updated your inital ram disk?

Id 83 is for Linux , and as 2 of your drives are id ee is GPT mdadm won't automatically create the raid device from your drives.

Edit: oH I've just read your post again and your saying that the drives aren't comming up in /dev.
What do you see in dmesg? any messages for your drives?

Regards
Ian Dobson

---

### Post by nullzone on 2011-11-03
Hello,

   the drivers are comming up in /dev, partitions arent. That's exactly the problem and the reason because I cant reassamble the raid.

   how is those partitions descriptors arent created in /dev only becuase drivers are using MBR?

> **ian dobson said:**
> Hi,

Have you created your mdadm.conf file and updated your inital ram disk?

Id 83 is for Linux , and as 2 of your drives are id ee is GPT mdadm won't automatically create the raid device from your drives.

Edit: oH I've just read your post again and your saying that the drives aren't comming up in /dev.
What do you see in dmesg? any messages for your drives?

Regards
Ian Dobson

---

### Post by ian dobson on 2011-11-03
Hi,

OK, now I'm really confused. Your kernel appears to be compled with gpt support but the partitions aren't being seen. So do you see any interesting messages in dmesg?

Regards
Ian Dobson

---

### Post by nullzone on 2011-11-11
Hey ian,

   sorry about this delay. I have been traveling again.

   Actually, dmesg or /var/log/message dont show anything wrong.
   Anyway, as expected, it doesnt show the available GPT partitions in both harddisks but the devices themselves.

```
sd 1:0:0:0: Attached scsi generic sg1 type 0
sd 1:0:0:0: [sdb] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
sd 1:0:0:0: [sdb] Write Protect is off
sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 sdb: sdb1
scsi 2:0:0:0: Direct-Access     ATA      WDC WD20EARS-00S 80.0 PQ: 0 ANSI: 5
sd 2:0:0:0: Attached scsi generic sg2 type 0
sd 2:0:0:0: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
sd 2:0:0:0: [sdc] Write Protect is off
sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 sdc:
scsi 3:0:0:0: Direct-Access     ATA      WDC WD20EARS-00M 50.0 PQ: 0 ANSI: 5
sd 3:0:0:0: Attached scsi generic sg3 type 0
sd 3:0:0:0: [sdd] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
sd 3:0:0:0: [sdd] Write Protect is off
sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 sdd:  sdd1
...
scsi 7:0:0:0: Direct-Access     ATA      WDC WD20EARS-00M 50.0 PQ: 0 ANSI: 5
sd 7:0:0:0: [sdh] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
sd 7:0:0:0: Attached scsi generic sg7 type 0
sd 7:0:0:0: [sdh] Write Protect is off
sd 7:0:0:0: [sdh] Mode Sense: 00 3a 00 00
sd 7:0:0:0: [sdh] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 sdh:

```

---

### Post by nullzone on 2011-11-11
huh? Is LAGER BLOCK DEVICE off by default???

```
# grep -i lbd /boot/config-2.6.31-14-server
#

```

---

### Post by mastro59 on 2012-03-05
I had the same problem with a Openmedaivault server. after a reboot the raid Sw excluded 2/4 disks (sdb and sdc, which result now to have valid partition GPT. I believe there was a false contact on the SATA connector. I was not able to see the disks, and only after powering down the server and having checked the cables the disks showed up in the bios boot. 
Now the 4 disks are visible in the bios boot and are listed in the dev directory. Is there a way I can at least make one of the 2 exclude HDs visible again to the raid5 array? Even if in degraded mode I would at least be able to backup my files. 

When I created this array I didnt' low level format any of the HD, I only deleted the partition using GParted. Honestly this is the first time I hear a LLF is needed. LLFormatting can take a lot of time and is quite risky....if LLF is not completed the HD can be trashed. This  happened to me with a 750GB Samsung disk, fortunately it was still in warranty. 

Any suggestion is more than welcome....have about 2Tbytes of data I hope to recover.

---

### Post by deagol on 2012-03-05
It's probably too late now... but nevertheless:

Maybe I'm missing something here, but have you checked that the partition(s) you are missing are visible with a gpt aware partitioning program? 
All I see in your post are fdisk and sfdisk outputs, both complaining that they don't understand GPT. So the output only shows that there IS a gpt partition TABLE, but not if there are any GPT partitions... (What you see as sdc1 and sdh1 is a placeholder partition, for old tools, not the Raid partition you are looking for. Linux will ignore these, and use the correct GPT partition table.)

I guess it's possible something happened to the GPT partition tables, so you definitly should check that out...

I'm also running a raid5 with 4x 2TB disks on GBT (just for fun and learning), so here's an sample how one of my disks is looking in "parted -l"

```

Model: ATA WDC WD2002FYPS-0 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      17.4kB  2000GB  2000GB               primary  raid

```

---


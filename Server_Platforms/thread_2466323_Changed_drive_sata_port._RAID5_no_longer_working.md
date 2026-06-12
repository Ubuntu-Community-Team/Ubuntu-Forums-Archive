---
title: "Changed drive sata port. RAID5 no longer working"
date: 2021-08-25
forum: Server Platforms
---

### Post by strat00s on 2021-08-25
[COLOR=#000000]I have a pretty frustrating problem here. I have a server with 6 drives (sdc as a boot drive, sdd as 2tb backup and sda, sdb, sde, sdf as RAID5). Everything worked fine, except lately one single drive (sde) sometimes failed for no reason. And to fix this I had to reboot my server and re-add via *mdadm --manage /dev/md0 --re-add /dev/sde*. I ran smart tests on that drive and they never returned any problems. This drive (together with another drive sdf) was connected to a PCI-E SATA adapter. So I thought that maybe moving the drive to an onboard SATA port might fix the problem. And with that, I decided to move the other drive as well. So now, everything is connected directly to the mobo.


And comes the problem. Once I turned the server on, the RAID wouldn't start. For some unknown reason, moving the drives around somehow broke the RAID.
Running *mdadm --detail* on the RAID returns the following:
```

/dev/md0:     Version : 1.2
   Creation Time : Thu May 6 10:19:43 2021
     Raid Level : raid5
   Used Dev Size : 18446744073709551615
    Raid Devices : 4
   Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Wed Aug 25 14:35:20 2021
       State : active, FAILED, Not Started
   Active Devices : 2
  Working Devices : 2
   Failed Devices : 0
   Spare Devices : 0

       Layout : left-symmetric
     Chunk Size : 512K

Consistency Policy : unknown

        Name : HomeServer:0 (local to host HomeServer)
        UUID : 97298aaf:6c2e1a99:179c931c:db773d51
       Events : 30469

   Number Major Minor RaidDevice State
    -   0    0    0   removed
    -   0    0    1   removed
    -   0    0    2   removed
    -   0    0    3   removed

    -   8    0    0   sync /dev/sda
    -   8   16    1   sync /dev/sdb

```
As you can see, only sda and sdb are recognized.


So I stoped the RAID and tried to reassemble it using *mdadm --assemble --scan -v*, which gave me this:
```

mdadm: looking for devices for /dev/md0
mdadm: Cannot assemble mbr metadata on /dev/sdf
mdadm: No super block found on /dev/sde (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sde
mdadm: No super block found on /dev/sdc5 (Expected magic a92b4efc, got db8ed616)
mdadm: no RAID superblock on /dev/sdc5
mdadm: /dev/sdc2 is too small for md: size is 2 sectors.
mdadm: no RAID superblock on /dev/sdc2
mdadm: No super block found on /dev/sdc1 (Expected magic a92b4efc, got 0000041b)
mdadm: no RAID superblock on /dev/sdc1
mdadm: No super block found on /dev/sdc (Expected magic a92b4efc, got b3453333)
mdadm: no RAID superblock on /dev/sdc
mdadm: No super block found on /dev/sdd1 (Expected magic a92b4efc, got 000004ea)
mdadm: no RAID superblock on /dev/sdd1
mdadm: No super block found on /dev/sdd (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sdd
mdadm: /dev/sdb is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sda is identified as a member of /dev/md0, slot 0.
mdadm: added /dev/sdb to /dev/md0 as 1
mdadm: no uptodate device for slot 2 of /dev/md0
mdadm: no uptodate device for slot 3 of /dev/md0
mdadm: added /dev/sda to /dev/md0 as 0
mdadm: /dev/md0 assembled from 2 drives - not enough to start the array.

```
So superblock on sde and sdf drives are suddenly gone. But how?
Running *mdadm --examine /dev/sd?* seems to confirm this:
```

/dev/sda:
      Magic : a92b4efc
     Version : 1.2
   Feature Map : 0x1
   Array UUID : 97298aaf:6c2e1a99:179c931c:db773d51
      Name : HomeServer:0 (local to host HomeServer)
  Creation Time : Thu May 6 10:19:43 2021
   Raid Level : raid5
  Raid Devices : 4




 Avail Dev Size : 7813776048 (3725.90 GiB 4000.65 GB)
   Array Size : 11720658432 (11177.69 GiB 12001.95 GB)
  Used Dev Size : 7813772288 (3725.90 GiB 4000.65 GB)
   Data Offset : 261120 sectors
  Super Offset : 8 sectors
  Unused Space : before=261040 sectors, after=3760 sectors
      State : clean
   Device UUID : 0cc32dc9:f4d74ada:eb6b735d:aa646359




Internal Bitmap : 8 sectors from superblock
   Update Time : Wed Aug 25 14:35:20 2021
  Bad Block Log : 512 entries available at offset 24 sectors
    Checksum : a0421fad - correct
     Events : 30469




     Layout : left-symmetric
   Chunk Size : 512K




  Device Role : Active device 0
  Array State : AAA. ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdb:
      Magic : a92b4efc
     Version : 1.2
   Feature Map : 0x1
   Array UUID : 97298aaf:6c2e1a99:179c931c:db773d51
      Name : HomeServer:0 (local to host HomeServer)
  Creation Time : Thu May 6 10:19:43 2021
   Raid Level : raid5
  Raid Devices : 4




 Avail Dev Size : 7813776048 (3725.90 GiB 4000.65 GB)
   Array Size : 11720658432 (11177.69 GiB 12001.95 GB)
  Used Dev Size : 7813772288 (3725.90 GiB 4000.65 GB)
   Data Offset : 261120 sectors
  Super Offset : 8 sectors
  Unused Space : before=261040 sectors, after=3760 sectors
      State : clean
   Device UUID : 6cddf9b2:ff102af5:ad8a9440:5a34374a




Internal Bitmap : 8 sectors from superblock
   Update Time : Wed Aug 25 14:35:20 2021
  Bad Block Log : 512 entries available at offset 24 sectors
    Checksum : 78e2618b - correct
     Events : 30469




     Layout : left-symmetric
   Chunk Size : 512K




  Device Role : Active device 1
  Array State : AAA. ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdc:
  MBR Magic : aa55
Partition[0] :  435445760 sectors at    2048 (type 83)
Partition[1] :  33411074 sectors at  435449854 (type 05)
/dev/sdd:
  MBR Magic : aa55
Partition[0] : 3907029167 sectors at      1 (type ee)
/dev/sde:
  MBR Magic : aa55
Partition[0] : 4294967295 sectors at      1 (type ee)
/dev/sdf:
  MBR Magic : aa55
Partition[0] : 4294967295 sectors at      1 (type ee)

```


So, do you guys have any idea, what happened to my drives? And is this even fixable?
I even tried putting everything back as it was (putting drives back on the PCI-E card as they were before, but nothing seems to fix it).[/COLOR]

---

### Post by darkod on 2021-08-25
First of all, I don't know what happened to the font of the post because it is very pale and difficult to read. Almost like inverted...

Second, the problem might be because you are using the disks directly as raid members. However I have no definite proof about this. And especially when changing controllers, which you did, maybe that is the source of your problems.

You should use partitions with mdadm, not the whole disk device itself. Instead, create a partition (I usually leave the last 15-20MB unallocated) and use the partition as mdadm member. This allows you to easily replace disks in the future also in case where you buy another brand and the disk has few sectors less.

Going back to your problem. You already tried to reassemble and it didn't work.

Option A
Stop any failed array if it is currently assembled and try to force the assemble.
```
sudo mdadm --stop /dev/md0
sudo mdadm --assemble --verbose --force /dev/md0 /dev/sd[abef]
```

If that didn't work try again but changing the second command little:
```
sudo --assemble --verbose --force --run /dev/md0 /dev/sd[abef]
```

If option A didn't help let us know and we will talk option B.

---

### Post by not-published on 2021-08-25
Did you switch it back to the SATA ports that worked to see if that still works?  How many sata, which are supported by Intel chipset which are supported by optional motherboard chipset?

Did a cable go bad when you switched?

What level of SCSI?  Does your raid require the first disk have the header?  Does your scsi raid put headers on every disk?  Did you read the manual?

Switch it back to when it worked.  Back it up if you don't have a backup.  Reload the backup onto your new configuration after switching cables around.  Safest thing to do.

---

### Post by strat00s on 2021-08-25
> **darkod said:**
> First of all, I don't know what happened to the font of the post because it is very pale and difficult to read. Almost like inverted...

Second, the problem might be because you are using the disks directly as raid members. However I have no definite proof about this. And especially when changing controllers, which you did, maybe that is the source of your problems.

You should use partitions with mdadm, not the whole disk device itself. Instead, create a partition (I usually leave the last 15-20MB unallocated) and use the partition as mdadm member. This allows you to easily replace disks in the future also in case where you buy another brand and the disk has few sectors less.

Going back to your problem. You already tried to reassemble and it didn't work.

Option A
Stop any failed array if it is currently assembled and try to force the assemble.
```
sudo mdadm --stop /dev/md0
sudo mdadm --assemble --verbose --force /dev/md0 /dev/sd[abef]
```

If that didn't work try again but changing the second command little:
```
sudo --assemble --verbose --force --run /dev/md0 /dev/sd[abef]
```

If option A didn't help let us know and we will talk option B.

[COLOR=#000000][COLOR=#000000]Sorry for the font. It should be ok now.[/COLOR]
[COLOR=#000000]I tried your option A and it returned this:
[/COLOR]```
[/COLOR]mdadm: looking for devices for /dev/md0
mdadm: No super block found on /dev/sde (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sde
mdadm: /dev/sde has no superblock - assembly aborted
```[COLOR=#000000]
[COLOR=#000000]Which I think looks promising, as now it's only a single drive that seems to have a problem (and that is recoverable on RAID5).[/COLOR]
[COLOR=#000000]So maybe forcing it with just sd[abf] would reassembly it as a degraded RAID and I can format the sde drive and add it once again?[/COLOR]
[COLOR=#000000]Please let me know if this makes any sense[/COLOR][/COLOR]

---

### Post by rsteinmetz70112 on 2021-08-25
Have you checked the drives to see if one or more are malfunctioning?

---

### Post by strat00s on 2021-08-25
> **not-published said:**
> Did you switch it back to the SATA ports that worked to see if that still works? How many sata, which are supported by Intel chipset which are supported by optional motherboard chipset?

Did a cable go bad when you switched?

What level of SCSI? Does your raid require the first disk have the header? Does your scsi raid put headers on every disk? Did you read the manual?

Switch it back to when it worked. Back it up if you don't have a backup. Reload the backup onto your new configuration after switching cables around. Safest thing to do.
Yes, they are now as they were before (connected to their old SATA ports).
The cables are ok.
Isn't SCSI different from SATA? And no idea about the headers. There is kinda no manual for unplugging and plugging SATA drives.
[COLOR=#000000]
> **rsteinmetz70112 said:**
> Have you checked the drives to see if one or more are malfunctioning?
Yes. All the drives are working just fine. I ran the smart test on all of them and none report any problems.[/COLOR]

---

### Post by darkod on 2021-08-26
Yes, try the command with only abf and let us know. Not sure if it stopped after detecting that sde doesn't have a superblock, but worth of try.

Even if it fails again, there is still option B. But lets not get ahead of ourselves.

PS. And I would be trying this using the onboard ports, the way you want it to work. My first option would be to try repair it connected to onboard so that you can leave it like that. As you wanted... I know it's natural to try put things back as they were but that didn't assemble it either.

---

### Post by rsteinmetz70112 on 2021-08-26
sdd sde and sdf all report ee partition type. That is "Indication that this legacy MBR is followed by an EFI header"

Are we sure the letters didn't change? It seems possible with all the plugging and unplugging, possibly the current sde is the former sdd

---

### Post by strat00s on 2021-08-26
[COLOR=#000000]> **darkod said:**
> Yes, try the command with only abf and let us know. Not sure if it stopped after detecting that sde doesn't have a superblock, but worth of try.

Even if it fails again, there is still option B. But lets not get ahead of ourselves.

PS. And I would be trying this using the onboard ports, the way you want it to work. My first option would be to try repair it connected to onboard so that you can leave it like that. As you wanted... I know it's natural to try put things back as they were but that didn't assemble it either.
[/COLOR][COLOR=#000000]Sadly it just stopped after the sde drive. So I got the same message about the sdf while trying it only with abf.[/COLOR]
[COLOR=#000000]I re-plugged it back as I wanted it (so all the drives are now connected to the onboard sata ports). And after checking the smart status I determined, that the sde drive is now sdd and sdf is sdc. So the raid is now across a,b,c,d (or rather a,b,d,c as that's the order I used when creating the raid initially. At least I think...).[/COLOR]
[COLOR=#000000]So I guess next I am trying the second option.[/COLOR]
[COLOR=#000000]Also while researching this, it might also be possible to "fix" it by "recreating" the array in the exact same order as before but with --assume-clean flag[/COLOR]

---

### Post by strat00s on 2021-08-26
> **rsteinmetz70112 said:**
> sdd sde and sdf all report ee partition type. That is "Indication that this legacy MBR is followed by an EFI header"

Are we sure the letters didn't change? It seems possible with all the plugging and unplugging, possibly the current sde is the former sdd
I am 100% certain that I plugged them back as they were. sde and sdf were the only drives from the RAID that I replugged from the pcie controller onto the motherboard.
And that's what I don't understand. Just by replugging the HDDs they suddenly report as gpt with protective mbr.
Running *gdisk -l* on all my current drives give me this:
```
stratos@HomeServer:~$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 1.0.3

Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.
Disk /dev/sda: 7814037168 sectors, 3.6 TiB
Model: ST4000DM004-2CV1
Sector size (logical/physical): 512/4096 bytes
Disk identifier (GUID): 95DDD556-5AE4-4F70-9C39-2A8EF89732DE
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 7814037134
Partitions will be aligned on 2048-sector boundaries
Total free space is 7814037101 sectors (3.6 TiB)

Number  Start (sector)    End (sector)  Size       Code  Name


stratos@HomeServer:~$ sudo gdisk -l /dev/sdb
GPT fdisk (gdisk) version 1.0.3

Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.
Disk /dev/sdb: 7814037168 sectors, 3.6 TiB
Model: ST4000DM004-2CV1
Sector size (logical/physical): 512/4096 bytes
Disk identifier (GUID): B3C11B98-898E-4CA8-B141-F79BBB63E669
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 7814037134
Partitions will be aligned on 2048-sector boundaries
Total free space is 7814037101 sectors (3.6 TiB)

Number  Start (sector)    End (sector)  Size       Code  Name


stratos@HomeServer:~$ sudo gdisk -l /dev/sdc
GPT fdisk (gdisk) version 1.0.3

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdc: 7814037168 sectors, 3.6 TiB
Model: WDC WD40EFAX-68J
Sector size (logical/physical): 512/4096 bytes
Disk identifier (GUID): 0CB38614-0CBB-4D78-8EB0-8F9FB189FF28
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 7814037134
Partitions will be aligned on 2048-sector boundaries
Total free space is 7814037101 sectors (3.6 TiB)

Number  Start (sector)    End (sector)  Size       Code  Name


stratos@HomeServer:~$ sudo gdisk -l /dev/sdd
GPT fdisk (gdisk) version 1.0.3

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdd: 7814037168 sectors, 3.6 TiB
Model: WDC WD40EFAX-68J
Sector size (logical/physical): 512/4096 bytes
Disk identifier (GUID): E06F92D5-8CDA-4938-81A7-AAD6E60EA8BA
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 7814037134
Partitions will be aligned on 2048-sector boundaries
Total free space is 7814037101 sectors (3.6 TiB)

Number  Start (sector)    End (sector)  Size       Code  Name


stratos@HomeServer:~$ sudo gdisk -l /dev/sde
GPT fdisk (gdisk) version 1.0.3

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present

***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************

Disk /dev/sde: 468862128 sectors, 223.6 GiB
Model: KINGSTON SA400S3
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): 67FB853F-D130-4AA3-AC55-3B2A926EC13B
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 468862094
Partitions will be aligned on 2048-sector boundaries
Total free space is 5229 sectors (2.6 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048       435447807   207.6 GiB   8300  Linux filesystem
   5       435449856       468860927   15.9 GiB    8200  Linux swap
```

sde is clearly my boot drive (now) and sdc and sdd (they are now plugged into the mobo, that's why they are no longer sde and sdf) show GPT partition table with protective MBR.

---

### Post by darkod on 2021-08-26
Yeah, option B is the recreate with --assume-clean. But we are not there yet and be careful with that because a --create used wrongly can wipe the existing data.

If the disks changed names (which is normal when changing ports, I didn't pick up on that earlier), then review the abcd status:
```
sudo mdadm -E /dev/sd[abcd]
```

Depending on what the superblocks say, you can try the forced assemble again but now with some of the following disk orders: abcd, abc, abd.

I just want to explore all options of forced assemble, before going with the recreate.

---

### Post by MAFoElffen on 2021-08-27
> **darkod said:**
> If the disks changed names (which is normal when changing ports, I didn't pick up on that earlier), then review the abcd status:
That is exactly what I was thinking. mdam does it's assemble on /dev/mdXXX names insteaDs of uuids of disks and partitions...

It is curious that you haven't posted your mdadm.conf file to show what is "was"...

Are you booting now or booting from a LiveCD? 

Could you please post the results of 
```

sudo fdisk -l | sed '/\/dev\/loop/,+3 d' | grep -e 'Disk\|Device\|/dev/' | sed 's/\x1b\[[0-9;]*m//g' 
lsblk -o NAME,SIZE,FSTYPE,LABEL,MOUNTPOINT,MODEL,HOTPLUG,PARTUUID,UUID | grep -v '/snap/'

```

That, along with your mdam.conf file, might help darkod to see where things lie now and how to help you... That might show if things were reassigned or renamed from what it was...

---

### Post by strat00s on 2021-08-27
[COLOR=#000000]> **darkod said:**
> Yeah, option B is the recreate with --assume-clean. But we are not there yet and be careful with that because a --create used wrongly can wipe the existing data.

If the disks changed names (which is normal when changing ports, I didn't pick up on that earlier), then review the abcd status:
```
sudo mdadm -E /dev/sd[abcd]
```

Depending on what the superblocks say, you can try the forced assemble again but now with some of the following disk orders: abcd, abc, abd.

I just want to explore all options of forced assemble, before going with the recreate.

Here is mdadm -E on those drives (same as before, as sde is now sdd and sdf is sdc.
```
/dev/sda:          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 97298aaf:6c2e1a99:179c931c:db773d51
           Name : HomeServer:0  (local to host HomeServer)
  Creation Time : Thu May  6 10:19:43 2021
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 7813776048 (3725.90 GiB 4000.65 GB)
     Array Size : 11720658432 (11177.69 GiB 12001.95 GB)
  Used Dev Size : 7813772288 (3725.90 GiB 4000.65 GB)
    Data Offset : 261120 sectors
   Super Offset : 8 sectors
   Unused Space : before=261040 sectors, after=3760 sectors
          State : clean
    Device UUID : 0cc32dc9:f4d74ada:eb6b735d:aa646359


Internal Bitmap : 8 sectors from superblock
    Update Time : Wed Aug 25 14:35:20 2021
  Bad Block Log : 512 entries available at offset 24 sectors
       Checksum : a0421fad - correct
         Events : 30469


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 0
   Array State : AAA. ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdb:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 97298aaf:6c2e1a99:179c931c:db773d51
           Name : HomeServer:0  (local to host HomeServer)
  Creation Time : Thu May  6 10:19:43 2021
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 7813776048 (3725.90 GiB 4000.65 GB)
     Array Size : 11720658432 (11177.69 GiB 12001.95 GB)
  Used Dev Size : 7813772288 (3725.90 GiB 4000.65 GB)
    Data Offset : 261120 sectors
   Super Offset : 8 sectors
   Unused Space : before=261040 sectors, after=3760 sectors
          State : clean
    Device UUID : 6cddf9b2:ff102af5:ad8a9440:5a34374a


Internal Bitmap : 8 sectors from superblock
    Update Time : Wed Aug 25 14:35:20 2021
  Bad Block Log : 512 entries available at offset 24 sectors
       Checksum : 78e2618b - correct
         Events : 30469


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 1
   Array State : AAA. ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdc:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)
/dev/sdd:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)
```
And running the mdadm force with any combination always returns that either sdc or sdd are bad (cannot assemble mbr metadata -> no superblock)



> **MAFoElffen said:**
> That is exactly what I was thinking. mdam does it's assemble on /dev/mdXXX names insteaDs of uuids of disks and partitions...

It is curious that you haven't posted your mdadm.conf file to show what is "was"...

Are you booting now or booting from a LiveCD? 

Could you please post the results of 
```

sudo fdisk -l | sed '/\/dev\/loop/,+3 d' | grep -e 'Disk\|Device\|/dev/' | sed 's/\x1b\[[0-9;]*m//g' 
lsblk -o NAME,SIZE,FSTYPE,LABEL,MOUNTPOINT,MODEL,HOTPLUG,PARTUUID,UUID | grep -v '/snap/'

```

That, along with your mdam.conf file, might help darkod to see where things lie now and how to help you... That might show if things were reassigned or renamed from what it was...
Here is the mdadm config:
```
# mdadm.conf#
# !NB! Run update-initramfs -u after updating this file.
# !NB! This will ensure that initramfs has an uptodate copy.
#
# Please refer to mdadm.conf(5) for information about this file.
#


# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers


# automatically tag new arrays as belonging to the local system
HOMEHOST <system>


# instruct the monitoring daemon where to send mail alerts
MAILADDR root


# definitions of existing MD arrays


# This configuration was auto-generated on Mon, 12 Oct 2020 22:04:00 +0200 by mkconf
ARRAY /dev/md0 uuid=97298aaf:6c2e1a99:179c931c:db773d51
```

I am booting from the ssd (sde drive now)

Here is the result:
```
stratos@HomeServer:~$ sudo fdisk -l | sed '/\/dev\/loop/,+3 d' | grep -e 'Disk\|Device\|/dev/' | sed 's/\x1b\[[0-9;]*m//g'Disk /dev/sdb: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Disk model: ST4000DM004-2CV1
Disk /dev/sdc: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Disk model: WDC WD40EFAX-68J
Disklabel type: gpt
Disk identifier: 0CB38614-0CBB-4D78-8EB0-8F9FB189FF28
Disk /dev/sdd: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Disk model: WDC WD40EFAX-68J
Disklabel type: gpt
Disk identifier: E06F92D5-8CDA-4938-81A7-AAD6E60EA8BA
Disk /dev/sda: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Disk model: ST4000DM004-2CV1
Disk /dev/sde: 223.6 GiB, 240057409536 bytes, 468862128 sectors
Disk model: KINGSTON SA400S3
Disklabel type: dos
Disk identifier: 0x15711b42
Device     Boot     Start       End   Sectors   Size Id Type
/dev/sde1  *         2048 435447807 435445760 207.7G 83 Linux
/dev/sde2       435449854 468860927  33411074    16G  5 Extended
/dev/sde5       435449856 468860927  33411072    16G 82 Linux swap / Solaris

stratos@HomeServer:~$ lsblk -o NAME,SIZE,FSTYPE,LABEL,MOUNTPOINT,MODEL,HOTPLUG,PARTUUID,UUID | grep -v '/snap/'
NAME     SIZE FSTYPE            LABEL        MOUNTPOINT MODEL                 HOTPLUG PARTUUID                             UUID
sda      3.7T linux_raid_member HomeServer:0            ST4000DM004-2CV104          0                                      97298aaf-6c2e-1a99-179c-931cdb773d51
sdb      3.7T linux_raid_member HomeServer:0            ST4000DM004-2CV104          0                                      97298aaf-6c2e-1a99-179c-931cdb773d51
sdc      3.7T                                           WDC_WD40EFAX-68JH4N0        0                                      
sdd      3.7T                                           WDC_WD40EFAX-68JH4N0        0                                      
sde    223.6G                                           KINGSTON_SA400S37240G       0                                      
&#9500;&#9472;sde1 207.7G ext4                           /                                      0 15711b42-01                          06bbc857-32f4-4541-b202-ab7cd8d05a24
&#9500;&#9472;sde2     1K                                                                       0 15711b42-02                          
&#9492;&#9472;sde5    16G LVM2_member                                                           0 15711b42-05                          wsphmH-yp0Q-B66C-nnX5-8HeG-l8z5-TbwypW
```[/COLOR]

---

### Post by TheFu on 2021-08-27
Don't use devices (/dev/sd[a-z]) when assembling arrays. Use UUIDs.  This is configured in the mdadm.conf file.

By changing the SATA port used, you've changed the device discovery process used by the Linux kernel. The order that devices are found, determines the device name they are assigned for that boot.   

/proc/mdstat has md2 as:
```
md2 : active raid1 sdg2[1] sdf2[0]
      1338985536 blocks [2/2] [UU]

```
and it is mounted as /Data/r2
```
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/md2       ext4  1.3T  1.2T   15G  99% /Data/r2

```

Here's an example array definition from only of my servers running in RAID1.
```
ARRAY /dev/md2 UUID=[COLOR="#FF0000"]08ef65fd:9c02d85a:ea0c067b:86e1af4c[/COLOR]
```

```
$ \lsblk -o name,label,uuid,mountpoint
NAME    LABEL           UUID                                 MOUNTPOINT
sdf                                                          
&#9500;&#9472;sdf1                                                       
&#9500;&#9472;sdf2                  [COLOR="#FF0000"]08ef65fd-9c02-d85a-ea0c-067b86e1af4c[/COLOR] 
&#9474; &#9492;&#9472;md2                 eec33187-943a-4dbf-b695-a613b1095ae2 /Data/r2
sdg                                                          
&#9500;&#9472;sdg1                                                       
&#9500;&#9472;sdg2                  [COLOR="#FF0000"]08ef65fd-9c02-d85a-ea0c-067b86e1af4c[/COLOR] 
&#9474; &#9492;&#9472;md2                 eec33187-943a-4dbf-b695-a613b1095ae2 /Data/r2

```
See how the identical UUID is put onto each partition that makes up the array, then used in the assembly of md2?  At creation time, the UUID for md2 was listed. I made a note about it.  An mdadm --examine should output it. Can also see the UUID in /dev/disk/by-uuid/
```
lrwxrwxrwx 1 root root   9 Aug 27 01:45 eec33187-943a-4dbf-b695-a613b1095ae2 -> ../../md2
```
Yep.

---

### Post by strat00s on 2021-08-27
> **TheFu said:**
> Don't use devices (/dev/sd[a-z]) when assembling arrays. Use UUIDs.  This is configured in the mdadm.conf file.

By changing the SATA port used, you've changed the device discovery process used by the Linux kernel. The order that devices are found, determines the device name they are assigned for that boot.   

/proc/mdstat has md2 as:
```
md2 : active raid1 sdg2[1] sdf2[0]
      1338985536 blocks [2/2] [UU]

```
and it is mounted as /Data/r2
```
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/md2       ext4  1.3T  1.2T   15G  99% /Data/r2

```

Here's an example array definition from only of my servers running in RAID1.
```
ARRAY /dev/md2 UUID=[COLOR="#FF0000"]08ef65fd:9c02d85a:ea0c067b:86e1af4c[/COLOR]
```

```
$ \lsblk -o name,label,uuid,mountpoint
NAME    LABEL           UUID                                 MOUNTPOINT
sdf                                                          
&#9500;&#9472;sdf1                                                       
&#9500;&#9472;sdf2                  [COLOR="#FF0000"]08ef65fd-9c02-d85a-ea0c-067b86e1af4c[/COLOR] 
&#9474; &#9492;&#9472;md2                 eec33187-943a-4dbf-b695-a613b1095ae2 /Data/r2
sdg                                                          
&#9500;&#9472;sdg1                                                       
&#9500;&#9472;sdg2                  [COLOR="#FF0000"]08ef65fd-9c02-d85a-ea0c-067b86e1af4c[/COLOR] 
&#9474; &#9492;&#9472;md2                 eec33187-943a-4dbf-b695-a613b1095ae2 /Data/r2

```
See how the identical UUID is put onto each partition that makes up the array, then used in the assembly of md2?  At creation time, the UUID for md2 was listed. I made a note about it.  An mdadm --examine should output it. Can also see the UUID in /dev/disk/by-uuid/
```
lrwxrwxrwx 1 root root   9 Aug 27 01:45 eec33187-943a-4dbf-b695-a613b1095ae2 -> ../../md2
```
Yep.
I don't want this to sound rude, but how exactly does this help me fix my array?
I get it that I can use uuids, but this has nothing to do with that. I am trying to find out, where did the superblocks go from the 2 drives and how to build the array once again.

---

### Post by darkod on 2021-08-27
Hold on everyone, lets take a step back. According to mdadm.conf that was posted recently, the array is defined with UUIDs so that part is correct. The problem is that sdc and sdd do not have the array UUID any more (superblock). Either because they were moved from PCIe controller to onboard or because of another issue.

However, strat00s, do remember this. mdadm should work with partitions, not whole disk designators. So in future when using arrays use for example sda1 and sdb1, not sda and sdb to create the array. It is too late to change that in this array because that would mean losing the data. But it is a good point to remember for future arrays.

So now we are left only with the last option, the recreate. The command would be something like this (make sure you stop and partial arrays first in case you have some assembled). And you need to remove the superblock from sda and sdb first too:
```
sudo mdadm --zero-superblock /dev/sda
sudo mdadm --zero-superblock /dev/sdb
sudo mdadm --create --verbose --assume-clean /dev/md0 /dev/sd[abcd]
```

In case that works, mount it as RO and check data/folders inside:
```
sudo mount -o ro /dev/md0 /mnt
cd /mnt
ls
```

Post the output of the create verbose output. Good luck. :)

---

### Post by TheFu on 2021-08-27
> **strat00s said:**
> I don't want this to sound rude, but how exactly does this help me fix my array?
I get it that I can use uuids, but this has nothing to do with that. I am trying to find out, where did the superblocks go from the 2 drives and how to build the array once again.

Not rude at all. Good question. 
I see **now** the mdadm.conf uses UUIDs, so that should be working. Sorry I missed that previously.

The initial problem statement was this:
>  And comes the problem. Once I turned the server on, the RAID wouldn't start. For some unknown reason, moving the drives around somehow broke the RAID.
The most common cause was not using UUIDs, but using device names directly which have changed.  By using UUIDs, all the drives would be found, regardless of the device name - so the superblocks would be discovered too. But the now available mdadm.conf shows a UUID being used.

It was just a guess. 

Also, how do you KNOW that the cables are fine today vs last week? Any movement of a SATA cable can break it. Repositioning inside a case can cause interference with power cables near SATA cables too.

If the drives die or the HBA dies or the PSU is starting to fail or the cables are vibrated loose, then those would also need to be addressed.  Of all the cables I've used over the decades, SATA cables seem to fail more than any others. Much more. Exponentially more, next would be ethernet connectors - perhaps 1/20th failure of SATA cables. Last would be USB cables. Think only those portable, spring-loaded USB cables have broke here, never any of the normal, desktop, USB cables.  I have had USB ports become too lose and fail due to vibration, however. 

+1 on always laying down a GPT before setting up a RAID onto one of the partitions. **sgdisk --clear $DEV** Just ensure the partitions are exactly the same size as existing partitions in the RAID, so you can mix disk models and vendors in the array.  Usually, I make a clone of the partition table (**sgdisk** --replicate=second_device_filename), then move the secondary GPT header at the end of the drive.  **sgdisk --move-second-header** is a method for that.  I find sgdisk is much easier to automate than the other partitioning tools.

---

### Post by strat00s on 2021-08-27
> **darkod said:**
> Hold on everyone, lets take a step back. According to mdadm.conf that was posted recently, the array is defined with UUIDs so that part is correct. The problem is that sdc and sdd do not have the array UUID any more (superblock). Either because they were moved from PCIe controller to onboard or because of another issue.

However, strat00s, do remember this. mdadm should work with partitions, not whole disk designators. So in future when using arrays use for example sda1 and sdb1, not sda and sdb to create the array. It is too late to change that in this array because that would mean losing the data. But it is a good point to remember for future arrays.

So now we are left only with the last option, the recreate. The command would be something like this (make sure you stop and partial arrays first in case you have some assembled). And you need to remove the superblock from sda and sdb first too:
```
sudo mdadm --zero-superblock /dev/sda
sudo mdadm --zero-superblock /dev/sdb
sudo mdadm --create --verbose --assume-clean /dev/md0 /dev/sd[abcd]
```

In case that works, mount it as RO and check data/folders inside:
```
sudo mount -o ro /dev/md0 /mnt
cd /mnt
ls
```

Post the output of the create verbose output. Good luck. :)
When recreating the array, the order of the drives list does matter, right? So I think the old order was abef. And e is now d and f is c, so it should be  .../sd[abdc]?

---

### Post by darkod on 2021-08-27
In theory with --assume-clean it detects existing data so I am not 100% sure it matters. That is why I say to mount it RO for checks after recreating and avoid writing any data on it. If the order is incorrect, you wouldn't be able to read any data. In such case you can zero again all 4 superblocks, and try another recreate with different order.

So if you best guess right now is abdc then try that first.

---

### Post by strat00s on 2021-08-27
> **darkod said:**
> In theory with --assume-clean it detects existing data so I am not 100% sure it matters. That is why I say to mount it RO for checks after recreating and avoid writing any data on it. If the order is incorrect, you wouldn't be able to read any data. In such case you can zero again all 4 superblocks, and try another recreate with different order.

So if you best guess right now is abdc then try that first.
Also I guess that I need to add *--level=5* and *--raid-devices=4*, correct? As right now I am getting this:
```
stratos@HomeServer:~$ sudo mdadm --create --verbose --assume-clean /dev/md0 /dev/sd[abdc]
mdadm: no raid-devices specified.
```
As always gonna wait for a response, as I want to screw this as little as possible.

---

### Post by darkod on 2021-08-27
Yeah, I was not sure about the --level and --raid-devices parameters. The example I found was without them. But it never hurts to add them, because we know they are true. So add them and give it a go.

PS. Or it might be it's simply not liking our order of parameters:
```
sudo mdadm --create /dev/md0 --verbose --assume-clean --level=5 --raid-devices=4 /dev/sd[abdc]
```

---

### Post by strat00s on 2021-08-27
> **darkod said:**
> Yeah, I was not sure about the --level and --raid-devices parameters. The example I found was without them. But it never hurts to add them, because we know they are true. So add them and give it a go.

PS. Or it might be it's simply not liking our order of parameters:
```
sudo mdadm --create /dev/md0 --verbose --assume-clean --level=5 --raid-devices=4 /dev/sd[abdc]
```
Well, I forgot to save the output, but it just said, that partition tables will be removed from sdc and sdd, as they are no longer needed.

And I can't mount it
```
stratos@HomeServer:~$ sudo mount -o ro /dev/md0 /mnt/test
mount: /mnt/test: wrong fs type, bad option, bad superblock on /dev/md0, missing codepage or helper program, or other error.
```

```
stratos@HomeServer:~$ lsblkNAME   MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda      8:0    0   3.7T  0 disk  
&#9492;&#9472;md0    9:0    0  10.9T  0 raid5 
sdb      8:16   0   3.7T  0 disk  
&#9492;&#9472;md0    9:0    0  10.9T  0 raid5 
sdc      8:32   0   3.7T  0 disk  
&#9492;&#9472;md0    9:0    0  10.9T  0 raid5 
sdd      8:48   0   3.7T  0 disk  
&#9492;&#9472;md0    9:0    0  10.9T  0 raid5 
sde      8:64   0 223.6G  0 disk  
&#9500;&#9472;sde1   8:65   0 207.7G  0 part  /
&#9500;&#9472;sde2   8:66   0     1K  0 part  
&#9492;&#9472;sde5   8:69   0    16G  0 part 
```
```
stratos@HomeServer:~$ sudo mdadm --examine /dev/md0 
mdadm: No md superblock detected on /dev/md0.
```

---

### Post by darkod on 2021-08-27
Not mounting might mean the order was wrong. Stop md0, zero all 4 superblocks, and do the create again with order abcd. Then the RO mount and check.

Also, you use --examine on raid members, and --detail on md devices. You can't use --examine on /dev/md0.

---

### Post by TheFu on 2021-08-27
After creating a new array, a file system must be laid down onto it.  Use **mkfs** for that.

```
sudo mkfs -t ext4 /dev/md0
```

Then the mount can work.  Or you could make md0 into an LVM PV, but I get the feeling that isn't desired.

---

### Post by darkod on 2021-08-27
> After creating a new array, a file system must be laid down onto it. Use mkfs for that.

The only difference here is that we are trying to save the existing array and data if I understood correctly. Formatting it with mkfs beats that point. :)

---

### Post by strat00s on 2021-08-27
> **darkod said:**
> The only difference here is that we are trying to save the existing array and data if I understood correctly. Formatting it with mkfs beats that point. :)
yep, but it seems like it's gone. No matter the order, it can't mount it...

---

### Post by TheFu on 2021-08-27
> **darkod said:**
> The only difference here is that we are trying to save the existing array and data if I understood correctly. Formatting it with mkfs beats that point. :)

Zeroing the superblocks would prevent that, right?  
[https://raid.wiki.kernel.org/index.php/A_guide_to_mdadm](https://raid.wiki.kernel.org/index.php/A_guide_to_mdadm) says:
>  Create

This is the first of the two modes you will use a lot. As the name implies, it creates arrays, and writes the superblocks for arrays that have them. **It also fires off initialisation - making sure that the disks of a mirror are identical, or that on a parity array the parities are correct.** This is why raids 5&6 are created in degraded mode - if they weren't then any check of the raid would spew errors for areas that hadn't been written to. 

[https://raid.wiki.kernel.org/index.php/RAID_Recovery](https://raid.wiki.kernel.org/index.php/RAID_Recovery)  has some techniques.

I just noticed that the sector counts in the different RAID devices are different.  Wouldn't that prevent creation of the array previously?
```

/dev/sdd: Partition[0] : 3907029167 sectors at      1 (type ee)
/dev/sde: Partition[0] : 4294967295 sectors at      1 (type ee)
/dev/sdf: Partition[0] : 4294967295 sectors at      1 (type ee)
```

sdc isn't anywhere near the size for this array. It is about 10x too small.  I hope the array size is limited to 3907029167 per device by the software. A 3-drive RAID5 array?

---

### Post by strat00s on 2021-08-27
> **TheFu said:**
> Zeroing the superblocks would prevent that, right?  
[https://raid.wiki.kernel.org/index.php/A_guide_to_mdadm](https://raid.wiki.kernel.org/index.php/A_guide_to_mdadm) says:


[https://raid.wiki.kernel.org/index.php/RAID_Recovery](https://raid.wiki.kernel.org/index.php/RAID_Recovery)  has some techniques.

I just noticed that the sector counts in the different RAID devices are different.  Wouldn't that prevent creation of the array previously?
```

/dev/sdd: Partition[0] : 3907029167 sectors at      1 (type ee)
/dev/sde: Partition[0] : 4294967295 sectors at      1 (type ee)
/dev/sdf: Partition[0] : 4294967295 sectors at      1 (type ee)
```

sdc isn't anywhere near the size for this array. It is about 10x too small.  I hope the array size is limited to 3907029167 per device by the software. A 3-drive RAID5 array?
This when it was connected the old way (sde and sdf via the pcie card). sdd in this case was my boot ssd, sde and sdf were 2 hdds from the array.
I had a 4 drive raid 5 array. And it seems like I lost it just by moving the drives around physically...

---

### Post by MAFoElffen on 2021-08-28
Did you have a good back up?

Because you all seemed to miss the point, which darkod hit on very early and this was his (the OP's) output proving it... Sorry to point this out, but: The OP doesn't know. about this. TheFu has it on his output from his server's, but no-one noticed that the the OP doesn't... Look at the OP's output...
```

stratos@HomeServer:~$ sudo fdisk -l | sed '/\/dev\/loop/,+3 d' | grep -e 'Disk\|Device\|/dev/' | sed 's/\x1b\[[0-9;]*m//g'
Disk /dev/sd[COLOR=#ff0000]b[/COLOR]: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Disk model: ST4000DM004-2CV1
Disk /dev/sd[COLOR=#ff0000]c:[/COLOR] 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Disk model: WDC WD40EFAX-68J
Disklabel type:[COLOR=#ff0000] gpt[/COLOR]
Disk identifier: 0CB38614-0CBB-4D78-8EB0-8F9FB189FF28
Disk /dev/sd[COLOR=#ff0000]d[/COLOR]: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Disk model: WDC WD40EFAX-68J
Disklabel type:[COLOR=#ff0000] gpt[/COLOR]
Disk identifier: E06F92D5-8CDA-4938-81A7-AAD6E60EA8BA
Disk /dev/sd[COLOR=#ff0000]a[/COLOR]: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Disk model: ST4000DM004-2CV1
Disk /dev/sde: 223.6 GiB, 240057409536 bytes, 468862128 sectors
Disk model: KINGSTON SA400S3
Disklabel type: dos
Disk identifier: 0x15711b42
Device     Boot     Start       End   Sectors   Size Id Type
/dev/sde1  *         2048 435447807 435445760 207.7G 83 Linux
/dev/sde2       435449854 468860927  33411074    16G  5 Extended
/dev/sde5       435449856 468860927  33411072    16G 82 Linux swap / Solaris

stratos@HomeServer:~$ lsblk -o NAME,SIZE,FSTYPE,LABEL,MOUNTPOINT,MODEL,HOTPLUG,PARTUUID,UUID | grep -v '/snap/'
NAME     SIZE FSTYPE            LABEL        MOUNTPOINT MODEL                 HOTPLUG PARTUUID                             UUID
sd[COLOR=#ff0000]a[/COLOR]      3.7T [COLOR=#ff0000]linux_raid_member[/COLOR] HomeServer:0            ST4000DM004-2CV104          0                                      97298aaf-6c2e-1a99-179c-931cdb773d51
sd[COLOR=#ff0000]b[/COLOR]      3.7T [COLOR=#ff0000]linux_raid_member[/COLOR] HomeServer:0            ST4000DM004-2CV104          0                                      97298aaf-6c2e-1a99-179c-931cdb773d51
sd[COLOR=#ff0000]c[/COLOR]      3.7T                                           WDC_WD40EFAX-68JH4N0        0                                      
sd[COLOR=#ff0000]d[/COLOR]      3.7T                                           WDC_WD40EFAX-68JH4N0        0                                      
sde    223.6G                                           KINGSTON_SA400S37240G       0                                      
&#9500;&#9472;sde1 207.7G ext4                           /                                      0 15711b42-01                          06bbc857-32f4-4541-b202-ab7cd8d05a24
&#9500;&#9472;sde2     1K                                                                       0 15711b42-02                          
&#9492;&#9472;sde5    16G LVM2_member                                                           0 15711b42-05                          wsphmH-yp0Q-B66C-nnX5-8HeG-l8z5-TbwypW

```[COLOR=#000000]
Look at this output closely...

Hint... What do you all [COLOR=#ff0000]not see[/COLOR], and [COLOR=#ff0000]is missing[/COLOR] from disks [COLOR=#ff0000]sd[a-d][/COLOR]? What is recommended that you install mdadm RAID to: Disks or partitions? And what is missing from the disks sd[c-d]? And are those the same disks that are missing the superblocks? 

Disks sda through sdd do not show any partitions. There is no sda1, sdb1, sdc1, sdd1... Drives sd[c,d] shows GPT partition types... Partition types for sd[a,b]? ...They  do not show drive label types. [COLOR=#000000]And the Op's output is Post #22, shows mdx devices... but still has  absolutely no partitions on any of those drives. Refer back to TheFu's output from his servers, from Post #14 for comparison... I could show you mine, but they would be the same...

The problem is... That it "is" possible to install mdadm on raw drives without partitions. It is even possible to create LVM on RAID without partitions. That doesn't mean it's the right way to do it,or that they will be reliable that way... And in my opinion, if done that way, it's only a matter of time before they fail, because that's not the way they are designed to be able to work. The got confused (and allowed that), and reality caught up. Their day's were numbered from it's conception. Because it's creation was outside of it's designed environment.
[/COLOR]
You want to look at it closer and in more detail? Download the boot_info script and run it to get a more detailed report on what is going on. The factors are there... [https://github.com/baedacool/bootinfoscript/blob/nvme-support/bootinfoscript](https://github.com/baedacool/bootinfoscript/blob/nvme-support/bootinfoscript)

Like I asked... Do you have a good backup of what was there?

Long ago... even with using hardware RAID... RAID and snapshots are not a replacement for backups. And even with RAID, snapshots, and backup's... In Server, uptime is premium. I learned the hard way, that sometimes it's easier and faster, if your RAID Array fails, if it doesn't reassemble and rebuild (after replacing a failed member)... Then just create fresh and restore. You have RAID5, with 2 out of 4 members down. It's been down how many days now?

My recommendation would be, that if you do not have a good backup, run the boot_info scripts on your system and see if there is "anything" there salvageable. If there is, "recover" that to "somewhere"... Zero out the drives. Create new GPT Partition tables, Partition the drives and create a new array to restore to... Something that can be reliable. But then again, that is just me.
[/COLOR]

---

### Post by strat00s on 2021-08-28
> **MAFoElffen said:**
> Did you have a good back up?

Because you all seemed to miss the point, which darkod hit on very early and this was his (the OP's) output proving it... Sorry to point this out, but: The OP doesn't know. about this. TheFu has it on his output from his server's, but no-one noticed that the the OP doesn't... Look at the OP's output...
```

stratos@HomeServer:~$ sudo fdisk -l | sed '/\/dev\/loop/,+3 d' | grep -e 'Disk\|Device\|/dev/' | sed 's/\x1b\[[0-9;]*m//g'
Disk /dev/sd[COLOR=#ff0000]b[/COLOR]: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Disk model: ST4000DM004-2CV1
Disk /dev/sd[COLOR=#ff0000]c:[/COLOR] 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Disk model: WDC WD40EFAX-68J
Disklabel type:[COLOR=#ff0000] gpt[/COLOR]
Disk identifier: 0CB38614-0CBB-4D78-8EB0-8F9FB189FF28
Disk /dev/sd[COLOR=#ff0000]d[/COLOR]: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Disk model: WDC WD40EFAX-68J
Disklabel type:[COLOR=#ff0000] gpt[/COLOR]
Disk identifier: E06F92D5-8CDA-4938-81A7-AAD6E60EA8BA
Disk /dev/sd[COLOR=#ff0000]a[/COLOR]: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Disk model: ST4000DM004-2CV1
Disk /dev/sde: 223.6 GiB, 240057409536 bytes, 468862128 sectors
Disk model: KINGSTON SA400S3
Disklabel type: dos
Disk identifier: 0x15711b42
Device     Boot     Start       End   Sectors   Size Id Type
/dev/sde1  *         2048 435447807 435445760 207.7G 83 Linux
/dev/sde2       435449854 468860927  33411074    16G  5 Extended
/dev/sde5       435449856 468860927  33411072    16G 82 Linux swap / Solaris

stratos@HomeServer:~$ lsblk -o NAME,SIZE,FSTYPE,LABEL,MOUNTPOINT,MODEL,HOTPLUG,PARTUUID,UUID | grep -v '/snap/'
NAME     SIZE FSTYPE            LABEL        MOUNTPOINT MODEL                 HOTPLUG PARTUUID                             UUID
sd[COLOR=#ff0000]a[/COLOR]      3.7T [COLOR=#ff0000]linux_raid_member[/COLOR] HomeServer:0            ST4000DM004-2CV104          0                                      97298aaf-6c2e-1a99-179c-931cdb773d51
sd[COLOR=#ff0000]b[/COLOR]      3.7T [COLOR=#ff0000]linux_raid_member[/COLOR] HomeServer:0            ST4000DM004-2CV104          0                                      97298aaf-6c2e-1a99-179c-931cdb773d51
sd[COLOR=#ff0000]c[/COLOR]      3.7T                                           WDC_WD40EFAX-68JH4N0        0                                      
sd[COLOR=#ff0000]d[/COLOR]      3.7T                                           WDC_WD40EFAX-68JH4N0        0                                      
sde    223.6G                                           KINGSTON_SA400S37240G       0                                      
&#9500;&#9472;sde1 207.7G ext4                           /                                      0 15711b42-01                          06bbc857-32f4-4541-b202-ab7cd8d05a24
&#9500;&#9472;sde2     1K                                                                       0 15711b42-02                          
&#9492;&#9472;sde5    16G LVM2_member                                                           0 15711b42-05                          wsphmH-yp0Q-B66C-nnX5-8HeG-l8z5-TbwypW

```[COLOR=#000000]
Look at this output closely...

Hint... What do you all [COLOR=#ff0000]not see[/COLOR], and [COLOR=#ff0000]is missing[/COLOR] from disks [COLOR=#ff0000]sd[a-d][/COLOR]? What is recommended that you install mdadm RAID to: Disks or partitions? And what is missing from the disks sd[c-d]? And are those the same disks that are missing the superblocks? 

Disks sda through sdd do not show any partitions. There is no sda1, sdb1, sdc1, sdd1... Drives sd[c,d] shows GPT partition types... Partition types for sd[a,b]? ...They  do not show drive label types. [COLOR=#000000]And the Op's output is Post #22, shows mdx devices... but still has  absolutely no partitions on any of those drives. Refer back to TheFu's output from his servers, from Post #14 for comparison... I could show you mine, but they would be the same...

The problem is... That it "is" possible to install mdadm on raw drives without partitions. It is even possible to create LVM on RAID without partitions. That doesn't mean it's the right way to do it,or that they will be reliable that way... And in my opinion, if done that way, it's only a matter of time before they fail, because that's not the way they are designed to be able to work. The got confused (and allowed that), and reality caught up. Their day's were numbered from it's conception. Because it's creation was outside of it's designed environment.
[/COLOR]
You want to look at it closer and in more detail? Download the boot_info script and run it to get a more detailed report on what is going on. The factors are there... [https://github.com/baedacool/bootinfoscript/blob/nvme-support/bootinfoscript](https://github.com/baedacool/bootinfoscript/blob/nvme-support/bootinfoscript)

Like I asked... Do you have a good backup of what was there?

Long ago... even with using hardware RAID... RAID and snapshots are not a replacement for backups. And even with RAID, snapshots, and backup's... In Server, uptime is premium. I learned the hard way, that sometimes it's easier and faster, if your RAID Array fails, if it doesn't reassemble and rebuild (after replacing a failed member)... Then just create fresh and restore. You have RAID5, with 2 out of 4 members down. It's been down how many days now?

My recommendation would be, that if you do not have a good backup, run the boot_info scripts on your system and see if there is "anything" there salvageable. If there is, "recover" that to "somewhere"... Zero out the drives. Create new GPT Partition tables, Partition the drives and create a new array to restore to... Something that can be reliable. But then again, that is just me.
[/COLOR]
Of course that I don't have a backup. If I had, we wouldn't be having this conversation in the first place. Losing data on this array is more of an inconvenience than a tragedy. I can easily re-download everything. There was nothing really important. Also, I don't have a few TBs of drives lying around for backups.
I know that raid is not a backup, but that is not why I made it. I was hoping for somewhat a large "drive" that would sustain single drive failures, so that I won't use data just purely just by drive failing.
And yes, I did not use partitions, which was pointed out multiple times and I am gonna do that the next time.
But even with all of my mistakes, why did I lose my raid just by moving the drives around physically?.

---

### Post by MAFoElffen on 2021-08-28
[COLOR=#000000]Yes. I have been there with a personal media center. I am sorry for the lose.

My guess would be, just by  from drive reassignment. I skipped over the details... You can correct me if I am wrong, but I think you said you had one that was previously esata, then well... added a PCVIE SATA controller... and somehow it seems like they got reassigned. 
I've done where I had a Hardware RAID controller that started acting up... replaced with what was the same model RAIDS controller. Set it up the same... and didn't want to come up.

IDK. But at this point, without looking at it with some low level tools to see what is going on, we're guessing. The boot_info script looks at the disks and what is on them with low level hex dumps to analyze what is there and identifies what it is.... In fact I was looking through that code earlier today. 3800 lines of it. But when it comes down to it... It look like it was setup without partitions from that I can see there... Maybe that script can see if they ever where there, and if the superblocks are there but corrupted... IDK

It might be worth a quick try at least. Or at least you would have the data on what might have gone wrong.
[/COLOR]

---

### Post by strat00s on 2021-08-28
> **MAFoElffen said:**
> [COLOR=#000000]Yes. I have been there with a personal media center. I am sorry for the lose.

My guess would be, just by  from drive reassignment. I skipped over the details... You can correct me if I am wrong, but I think you said you had one that was previously esata, then well... added a PCVIE SATA controller... and somehow it seems like they got reassigned. 
I've done where I had a Hardware RAID controller that started acting up... replaced with what was the same model RAIDS controller. Set it up the same... and didn't want to come up.

IDK. But at this point, without looking at it with some low level tools to see what is going on, we're guessing. The boot_info script looks at the disks and what is on them with low level hex dumps to analyze what is there and identifies what it is.... In fact I was going through the code on that earlier today. 3800 lines of code. But when it comes down to it... It was setup without partitions that I can see at this point... Maybe that script can see if they ever where there, and if the supreblocks are there but corrupted... IDK

It might be worth a quick try at least. Or at least you would have the data on what might have gone wrong.
[/COLOR]
All of them were normal SATA, except those 2 that went haywire were connected to PCIE sata controller.
The script didn't show anything interesting about them and it pretty much found nothing on them

---

### Post by MAFoElffen on 2021-08-28
Meaning that the boot_info script says they are "blank"? Nothing on those two drives?

---

### Post by strat00s on 2021-08-28
> **MAFoElffen said:**
> Meaning that the boot_info script says they are "blank"? Nothing on those two drives?
If you want to [go through it]("https://pastebin.com/0yRjyaxH"), be my guest. But I think it did not find anything useful on them

---

### Post by MAFoElffen on 2021-08-28
Ouch.

Just reviewed it all. I am sorry for your lose. 

That confirms there is nothing there on sdc and sdd to hook to at all. At least now you know and can direct your efforts from here constructively.

if it were me... The drives may be okay physically. Do a long low level test to verify and start over with new partition tables and partitions. A long low level test will wipe the drives... but also mark out anything it finds bad. That's what we would do to certify used drives for resale.

---

### Post by strat00s on 2021-08-28
> **MAFoElffen said:**
> Ouch.

Just reviewed it all. I am sorry for your lose. 

That confirms there is nothing there on sdc and sdd to hook to at all. At least now you know and can direct your efforts from here constructively.

if it were me... The drives may be okay physically. Do a long low level test to verify and start over with new partition tables and partitions. A long low level test will wipe the drives... but also mark out anything it finds bad. That's what we would do to certify used drives for resale.
Do you have a particular software in mind (preferably one that can run in terminal)? I doubt that you mean SMART test

---

### Post by MAFoElffen on 2021-08-28
Seagate Seatools bootable: [https://www.seagate.com/support/downloads/seatools/](https://www.seagate.com/support/downloads/seatools/)

It usually takes 3-5 hours per TB...

The manual is at that link also...

---

### Post by strat00s on 2021-08-28
> **MAFoElffen said:**
> Seagate Seatools bootable: [https://www.seagate.com/support/downloads/seatools/](https://www.seagate.com/support/downloads/seatools/)

It usually takes 3-5 hours per TB...

The manual is at that link also...
I was hoping for something to run on the server. But holly cow. That will take 2-3 days (each drive is 4TB) :/

---

### Post by darkod on 2021-08-28
I am also very surprised that this would happen only by moving disks around on the SATA ports. It definitely shouldn't...

This almost looks like the two disks that were on PCIe somehow got reformatted or a partition table was written on them. You wouldn't have that PCIe card in some RAID mode would you? Or the onboard SATA ports where you moved them to.

Bottom line, it really does seem you can't save this array. How you proceed from here depends on you.

You can do a long term test on the disks first, but I doubt it is worth it personally. You will be making RAID again, and the probability to have two disks fail at same time is low.

Anyway, with or without the long term test, after that you should partition the disks and create your new RAID5 array using 4 partitions.

You know how it goes from there. You format it, mount it, and use it... :)

---

### Post by strat00s on 2021-08-28
> **darkod said:**
> This almost looks like the two disks that were on PCIe somehow got reformatted or a partition table was written on them. You wouldn't have that PCIe card in some RAID mode would you? Or the onboard SATA ports where you moved them to.
The card is too cheap for something like that. And the motherboard does not have any hw raid support.
So I am going to format each drive, create partition on each drive and then create the raid using the partitions.

---

### Post by TheFu on 2021-08-28
> **strat00s said:**
> The card is too cheap for something like that. And the motherboard does not have any hw raid support.
So I am going to format each drive, create partition on each drive and then create the raid using the partitions.

When you create the partitions for mdadm use, ensure they are EXACTLY the same size. Consistency matters. Lots of disk tools don't work when there aren't any partition tables.

BTW, I've moved mdadm arrays to new systems multiple times in the past. Had no issues.  The disk controllers completely changed. They were just JBOD. The drive connections inside the array didn't change, but all the device names did, but they retained the same "order".  c, d, e, f --> e, f, g, h

I keep the exact commands used to create every mdadm array. Never know when it will be handy.  Learned that the hard way.  Also have notes for steps to replace a failed disk.  One of the keys to that is to tell mdadm that a device has failed BEFORE removing it.  That isn't always possible, of course, so it isn't absolutely critical.

When storage in my mdadm starts failing, I'll be migrating to either LVM-RAID or ZFS. Haven't decided which.  ZFS would be more useful, I think.

---

### Post by strat00s on 2021-08-28
> **TheFu said:**
> When you create the partitions for mdadm use, ensure they are EXACTLY the same size. Consistency matters. Lots of disk tools don't work when there aren't any partition tables.

BTW, I've moved mdadm arrays to new systems multiple times in the past. Had no issues.  The disk controllers completely changed. They were just JBOD. The drive connections inside the array didn't change, but all the device names did, but they retained the same "order".  c, d, e, f --> e, f, g, h

I keep the exact commands used to create every mdadm array. Never know when it will be handy.  Learned that the hard way.  Also have notes for steps to replace a failed disk.  One of the keys to that is to tell mdadm that a device has failed BEFORE removing it.  That isn't always possible, of course, so it isn't absolutely critical.

When storage in my mdadm starts failing, I'll be migrating to either LVM-RAID or ZFS. Haven't decided which.  ZFS would be more useful, I think.
I made sure they have the same size and was also pretty surprised to learn, that all 4 of those drives (2 from seagate, 2 from wd) have the exact same size (I made the partition a bit smaller just in case, but same).

---

### Post by MAFoElffen on 2021-08-28
I have an Ubuntu flavored Support LiveCD Project.

I wrote a script for it that  queries  the disk's firmware and writes a report, using hdparm. It  prompts the user for the drive, drives or drive range to select those  drive(s). It also scans the Security Sections of those disk's firmware,  to see if they support a firmware security wipe and calculates the time  it would take to do it with a script. (Of course, it only takes passing the commands concurrently and take's the time of the  longest drive). Because doing a security wipe by a drive's firmware only takes about 1.5 hr/TB for SATA, and 8 min/TB for SSD.

The reason I mention that is you might want to  just type in one command and make sure you now have good communications  through your new controller and such, to all your drives... Just for  good measure.
```

sudo hdparm -I /dev/sd[a-e] | less

```
That will just query the information on your drives...

---


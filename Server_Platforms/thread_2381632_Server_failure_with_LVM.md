---
title: "Server failure with LVM"
date: 2018-01-03
forum: Server Platforms
---

### Post by linuxandy76 on 2018-01-03
Good Morning and HNY :)

I am hoping someone will be able to point me in the right direction on how to get my server fixed and at least some data recovered. Short story, we had a new cooker installed which managed to trip the power a couple of times and it managed to kill the server. Setup is as follows: 

Ubuntu 14.04 
LVM with 4 disks
1 additional disk ( outside existing LVM ) 

From what I have managed to glean so far, of the four disks that are part of the LVM its the SDA disk that has gone faulty - it has a swap partition on it, but the actual root partition is no longer available, which is where I get the following message: 

[h=2]ALERT /dev/mapper/ubuntu--vg-root does not exist DROPPING to Shell[/h]
I have rebuilt the server on a separate disk so that I can at least look at what is going on - how do I go about recovering the root partition ? 

Thanks in advance.

---

### Post by darkod on 2018-01-03
Unfortunately if it can't read the disk correctly it will be very difficult to recover the data. You have all disks installed into a new machine now, right?

To activate all LVM (in case it is not), you can try:
```
sudo vgchange -ay
```

That is detecting all LVM devices and activating the VGs. If that works you are on good track...

PS. You should also be able to see all readable partitions with:
```
lsblk
```

---

### Post by linuxandy76 on 2018-01-03
Hi darkod, 

Unfortunately when I run lsblk, I can only see the lvm swap partition - it doesnt show the root partition at all - this is the output of the various commands: 

```
blkid
NAME                  MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sdf                     8:80   0   1.8T  0 disk 
&#9492;&#9472;sdf1                  8:81   0   1.8T  0 part 
sdd                     8:48   0 931.5G  0 disk 
&#9500;&#9472;sdd2                  8:50   0     1K  0 part 
&#9492;&#9472;sdd5                  8:53   0 931.3G  0 part 
  &#9492;&#9472;entreprise-data   253:1    0 928.2G  0 lvm  /media/boys
sdb                     8:16   0 931.5G  0 disk 
&#9492;&#9472;sdb1                  8:17   0 931.5G  0 part 
sde                     8:64   0 465.8G  0 disk 
&#9500;&#9472;sde2                  8:66   0     1K  0 part 
&#9500;&#9472;sde5                  8:69   0 465.5G  0 part 
&#9474; &#9492;&#9472;apollo--vg-swap_1 253:0    0   3.9G  0 lvm  
&#9492;&#9472;sde1                  8:65   0   243M  0 part 
sdc                     8:32   0 465.8G  0 disk 
&#9492;&#9472;sdc1                  8:33   0 465.8G  0 part 
sda                     8:0    0 465.8G  0 disk 
&#9500;&#9472;sda2                  8:2    0     1K  0 part 
&#9500;&#9472;sda5                  8:5    0   3.9G  0 part [SWAP]
&#9492;&#9472;sda1                  8:1    0 461.9G  0 part /


vgdisplay
  --- Volume group ---
  VG Name               apollo-vg
  System ID             
  Format                lvm2
  Metadata Areas        4
  Metadata Sequence No  11
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               0
  Max PV                0
  Cur PV                4
  Act PV                4
  VG Size               3.64 TiB
  PE Size               4.00 MiB
  Total PE              953804
  Alloc PE / Size       1000 / 3.91 GiB
  Free  PE / Size       952804 / 3.63 TiB
  VG UUID               Cj1Nj2-fKhq-i80z-ZtPd-HNru-c1Ts-uY4265
   
  --- Volume group ---
  VG Name               entreprise
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  9
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               931.27 GiB
  PE Size               4.00 MiB
  Total PE              238405
  Alloc PE / Size       237627 / 928.23 GiB
  Free  PE / Size       778 / 3.04 GiB
  VG UUID               v3GWj1-hLai-iQlv-75qN-2r0v-UDMt-RUwK1q


lvdisplay
  --- Logical volume ---
  LV Path                /dev/apollo-vg/swap_1
  LV Name                swap_1
  VG Name                apollo-vg
  LV UUID                JLjBRh-Znkf-k53o-XpCJ-dwzP-Owjk-TnUfxB
  LV Write Access        read/write
  LV Creation host, time , 
  LV Status              available
  # open                 0
  LV Size                3.91 GiB
  Current LE             1000
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:0
   
  --- Logical volume ---
  LV Path                /dev/entreprise/data
  LV Name                data
  VG Name                entreprise
  LV UUID                NcdBFT-OGUw-Tc1z-ijAd-710B-L8UL-pWoTYD
  LV Write Access        read/write
  LV Creation host, time , 
  LV Status              available
  # open                 1
  LV Size                928.23 GiB
  Current LE             237627
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:1


pvdisplay
  --- Physical volume ---
  PV Name               /dev/sde5
  VG Name               apollo-vg
  PV Size               465.52 GiB / not usable 2.00 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              119173
  Free PE               118173
  Allocated PE          1000
  PV UUID               aib9B7-521v-1wcN-xjHI-Pu2K-LAvI-zJfMYA
   
  --- Physical volume ---
  PV Name               /dev/sdb1
  VG Name               apollo-vg
  PV Size               931.51 GiB / not usable 4.00 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              238466
  Free PE               238466
  Allocated PE          0
  PV UUID               9BK8DS-NDHP-raPo-dlGO-oGTZ-FIsc-3yjVW4
   
  --- Physical volume ---
  PV Name               /dev/sdc1
  VG Name               apollo-vg
  PV Size               465.76 GiB / not usable 3.00 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              119234
  Free PE               119234
  Allocated PE          0
  PV UUID               nZLEq4-FJMc-b6vS-lWKv-3QtS-lmjI-3QmjLg
   
  --- Physical volume ---
  PV Name               /dev/sdf1
  VG Name               apollo-vg
  PV Size               1.82 TiB / not usable 4.00 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              476931
  Free PE               476931
  Allocated PE          0
  PV UUID               s0sATe-D0Dj-qMrx-Ua8E-45pC-DJE2-seeNjH
   
  --- Physical volume ---
  PV Name               /dev/sdd5
  VG Name               entreprise
  PV Size               931.27 GiB / not usable 4.00 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              238405
  Free PE               778
  Allocated PE          237627
  PV UUID               H7IwbM-QVX7-RJg6-QUnF-NkFj-2Cdn-1xVrwY


fdisk -l
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x2300a221


Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 968579071 968577024 461.9G 83 Linux
/dev/sda2       968581118 976771071   8189954   3.9G  5 Extended
/dev/sda5       968581120 976771071   8189952   3.9G 82 Linux swap / Solaris




Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000be230


Device     Boot Start        End    Sectors   Size Id Type
/dev/sdb1        2048 1953523711 1953521664 931.5G 83 Linux




Disk /dev/sdc: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0007d938


Device     Boot Start       End   Sectors   Size Id Type
/dev/sdc1        2048 976773119 976771072 465.8G 83 Linux




Disk /dev/sdd: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000b6f90


Device     Boot  Start        End    Sectors   Size Id Type
/dev/sdd2       501758 1953523711 1953021954 931.3G  5 Extended
/dev/sdd5       501760 1953523711 1953021952 931.3G 8e Linux LVM




Disk /dev/sde: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000f3aa7


Device     Boot  Start       End   Sectors   Size Id Type
/dev/sde1  *      2048    499711    497664   243M 83 Linux
/dev/sde2       501758 976771071 976269314 465.5G  5 Extended
/dev/sde5       501760 976771071 976269312 465.5G 8e Linux LVM




Disk /dev/sdf: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 3EA9DB14-7801-47B8-AB64-2778BA19B37A


Device     Start        End    Sectors  Size Type
/dev/sdf1   2048 3907028991 3907026944  1.8T Linux filesystem




Disk /dev/mapper/apollo--vg-swap_1: 3.9 GiB, 4194304000 bytes, 8192000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/mapper/entreprise-data: 928.2 GiB, 996679876608 bytes, 1946640384 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```

---

### Post by darkod on 2018-01-03
Can you summarize which partitions belong to VG apollo-vg because I'm not sure if the faulty one is listed or not???

I can see the following in pvdisplay:
sde5, sdb1, sdc1, sdf1

Are those all? Which one is the faulty disk/partition?

---

### Post by linuxandy76 on 2018-01-04
Hi Darko, 

Sorry I didnt put that information in initially, I realised that I hadnt explained the structure out v well. The disks are organised as follows: 

**sda **- this is the new hard disk that I used to rebuild the system with, and is not part of the original apollo-vg so it can be ignored

**sdd** - this is a standalone disk from another system that is not part of the apollo-vg, but I am able to access this fine so it can be ignored

**sdb, sdc, sde, sdf** - these are the original disks that are part of the apollo-vg, and disk sde* would have been the **original** sda disk before the server went bang. 

I have managed to run e2fsck against sde1 which seemed to repair a few failures, but have not managed to do the same against either sde2 or sde5. The other disks appear to be okay, but I just cannot get the apollo-vg-root to become available, and it is does not appear whenever I do an lvdisplay. 

Running vgdisplay shows that it should have 4 pv's in it, which is right, but whenever I try to boot with just those four disks it dumps it back to the initramd prompt. 

Thanks 

Andy

---

### Post by darkod on 2018-01-04
OK, hold on... I think with little luck you might still save this.

The way I see it, sde5 was the only partition from sde that was used for the LVM. The other partitions on the disk are sde2 of 1KB (for system usage) and sde1 of 243MB (probably for /boot of the original installation).

But lsblk at least shows sde5 which means it is not completely lost.

Don't run fsck against sde5, the partition does not hold the filesystem. The partition is part of LVM and the LV is holding the filesystem, so the fsck should be run against it.

So next thing you need to achieve is somehow to activate the /dev/apollo-vg/root LV so that you can try fsck on it. Try searching online for instructions how to activate a LV when one member is corrupt. I will try to find something too when I have free time.

Just be careful and try not touching sde5 too much, in this case it is only like a "container" used for LVM. The files are not in it, so to speak... The LVM layer is in between.

---

### Post by darkod on 2018-01-04
Can you show us the result of this:
```
sudo pvscan
```

I have found some pages related to recovering LVM but lets see if your case fits into one of these...
[https://www.novell.com/coolsolutions/appnote/19386.html](https://www.novell.com/coolsolutions/appnote/19386.html)
[http://blog.adamsbros.org/2009/05/30/recover-lvm-volume-groups-and-logical-volumes-without-backups/](http://blog.adamsbros.org/2009/05/30/recover-lvm-volume-groups-and-logical-volumes-without-backups/)

---

### Post by linuxandy76 on 2018-01-14
Right, managed to get some time on this - pvscan shows: 

lubuntu@lubuntu:~$ sudo pvscan
  PV /dev/sda5   VG apollo-vg       lvm2 [465.52 GiB / 461.61 GiB free]
  PV /dev/sdb1   VG apollo-vg       lvm2 [931.51 GiB / 931.51 GiB free]
  PV /dev/sdc1   VG apollo-vg       lvm2 [465.76 GiB / 465.76 GiB free]
  PV /dev/sdd1   VG apollo-vg       lvm2 [1.82 TiB / 1.82 TiB free]
  Total: 4 [3.64 TiB] / in use: 4 [3.64 TiB] / in no VG: 0 [0   ]

I have got the disks back in there original arrangement, so there should be no confusing anything - the only thing that might be a bit of a fly in the ointment is that the 1.82tb disk was originally SDE1, so I am not sure if that changes things.

---

### Post by linuxandy76 on 2018-01-14
lubuntu@lubuntu:~$ sudo lvdisplay
  --- Logical volume ---
  LV Path                /dev/apollo-vg/swap_1
  LV Name                swap_1
  VG Name                apollo-vg
  LV UUID                JLjBRh-Znkf-k53o-XpCJ-dwzP-Owjk-TnUfxB
  LV Write Access        read/write
  LV Creation host, time , 
  LV Status              NOT available
  LV Size                3.91 GiB
  Current LE             1000
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto

I am running this via a USB stick, hence the additional disks: 

lubuntu@lubuntu:~$ sudo blkid
/dev/sda1: UUID="b2126c6a-4430-46dc-89cd-54c7f6d29089" TYPE="ext2" PARTUUID="000f3aa7-01"
/dev/sde1: UUID="781A-82E2" TYPE="vfat" PARTUUID="000cff16-01"
/dev/loop0: TYPE="squashfs"
/dev/sda5: UUID="aib9B7-521v-1wcN-xjHI-Pu2K-LAvI-zJfMYA" TYPE="LVM2_member" PARTUUID="000f3aa7-05"
/dev/sdb1: UUID="9BK8DS-NDHP-raPo-dlGO-oGTZ-FIsc-3yjVW4" TYPE="LVM2_member" PARTUUID="000be230-01"
/dev/sdc1: UUID="nZLEq4-FJMc-b6vS-lWKv-3QtS-lmjI-3QmjLg" TYPE="LVM2_member" PARTUUID="0007d938-01"
/dev/sdd1: UUID="s0sATe-D0Dj-qMrx-Ua8E-45pC-DJE2-seeNjH" TYPE="LVM2_member" PARTLABEL="2tb" PARTUUID="39e0163b-3688-428f-b206-2a732d1fa3f1"
/dev/zram0: UUID="42416b75-1660-41f2-9438-bb1860637c96" TYPE="swap"
/dev/zram1: UUID="005ad8f1-a062-48a1-b4dd-bc865d71b3af" TYPE="swap"
/dev/zram2: UUID="f378c477-c5ee-4557-bb01-ffe48d86426c" TYPE="swap"
/dev/zram3: UUID="5d439c58-0af4-41d6-9015-e4d4666091e4" TYPE="swap"

---

### Post by darkod on 2018-01-14
Well, pvscan actually finds all 4 members and doesn't print any errors. Don't worry about sde1 or sdd1, LVM has another ways to figure out what belongs where. You can see it reports sdd1 as member of apollo-vg and doesn't complain.

If you try to activate all LVs with verbose mode, what does it say:
```
sudo vgchange -ay -v
```

---

### Post by linuxandy76 on 2018-01-15
Output: 
lubuntu@lubuntu:~$ sudo vgchange -ay -v
    Activating logical volume apollo-vg/swap_1.
    activation/volume_list configuration setting not defined: Checking only host tags for apollo-vg/swap_1.
    Creating apollo--vg-swap_1
    Loading apollo--vg-swap_1 table (253:0)
    Resuming apollo--vg-swap_1 (253:0)
    Activated 1 logical volumes in volume group apollo-vg
  1 logical volume(s) in volume group "apollo-vg" now active

---

### Post by linuxandy76 on 2018-01-27
Managed to find this in my backup directory:

# Generated by LVM2 version 2.02.168(2) (2016-11-30): Sat Jan 27 12:48:49 2018

contents = "Text Format Volume Group"
version = 1

description = "Created *after* executing 'vgcfgbackup'"

creation_host = "lubuntu"       # Linux lubuntu 4.13.0-21-generic #24-Ubuntu SMP Mon Dec 18 17:29:35 UTC 2017 i686
creation_time = 1517057329      # Sat Jan 27 12:48:49 2018

apollo-vg {
        id = "Cj1Nj2-fKhq-i80z-ZtPd-HNru-c1Ts-uY4265"
        seqno = 13
        format = "lvm2"                 # informational
        status = ["RESIZEABLE", "READ", "WRITE"]
        flags = []
        extent_size = 8192              # 4 Megabytes
        max_lv = 0
        max_pv = 0
        metadata_copies = 0

        physical_volumes {

                pv0 {
                        id = "aib9B7-521v-1wcN-xjHI-Pu2K-LAvI-zJfMYA"
                        device = "/dev/sda5"    # Hint only

                        status = ["ALLOCATABLE"]
                        flags = []
                        dev_size = 976269312    # 465.521 Gigabytes
                        pe_start = 384
                        pe_count = 119173       # 465.52 Gigabytes
                }

                pv1 {
                        id = "9BK8DS-NDHP-raPo-dlGO-oGTZ-FIsc-3yjVW4"
                        device = "/dev/sdb1"    # Hint only

                        status = ["ALLOCATABLE"]
                        flags = []
                        dev_size = 1953521664   # 931.512 Gigabytes
                        pe_start = 2048
                        pe_count = 238466       # 931.508 Gigabytes
                }

                pv2 {
                        id = "nZLEq4-FJMc-b6vS-lWKv-3QtS-lmjI-3QmjLg"
                        device = "/dev/sdc1"    # Hint only

                        status = ["ALLOCATABLE"]
                        flags = []
                        dev_size = 976771072    # 465.761 Gigabytes
                        pe_start = 2048
                        pe_count = 119234       # 465.758 Gigabytes
pv3 {
                        id = "s0sATe-D0Dj-qMrx-Ua8E-45pC-DJE2-seeNjH"
                        device = "/dev/sdd1"    # Hint only

                        status = ["ALLOCATABLE"]
                        flags = []
                        dev_size = 3907026944   # 1.81935 Terabytes
                        pe_start = 2048
                        pe_count = 476931       # 1.81935 Terabytes
                }
        }

        logical_volumes {

                swap_1 {
                        id = "JLjBRh-Znkf-k53o-XpCJ-dwzP-Owjk-TnUfxB"
                        status = ["READ", "WRITE", "VISIBLE"]
                        flags = []
                        segment_count = 1

                        segment1 {
                                start_extent = 0
                                extent_count = 1000     # 3.90625 Gigabytes

                                type = "striped"
                                stripe_count = 1        # linear

                                stripes = [
                                        "pv0", 118161



It is very obviously missing the Root partition - how do I get this back ? 

Thanks

---

### Post by darkod on 2018-01-27
You have a file create with vgcfgbackup? Is it from before the failure?

---

### Post by linuxandy76 on 2018-01-27
Irritatingly, its not. I managed to use this [webpage]("http://blog.adamsbros.org/2009/05/30/recover-lvm-volume-groups-and-logical-volumes-without-backups/") and I *think* I may be able to find the information i want, but it isnt easy - there is a lot of data to wade through and no easy way to get it into an easily readable format. [URL="http://blog.adamsbros.org/2009/05/30/recover-lvm-volume-groups-and-logical-volumes-without-backups/"]
[/URL]

---

### Post by darkod on 2018-01-27
I had seen similar articles, but the issue is in these cases it complains directly about the lvm metadata. In your case it does not. What is weird is that your machine still sees the sda5 partition. It's not like it is completely dead...

---

### Post by darkod on 2018-01-27
In his case I think the issue was only with metadata, which he managed to solve successfully. But you can give it a shot too, get a koppix CD and do the first part of the tutorial (the troubleshooting steps).

Maybe you will manage to get more info to work with... At this moment I am unsure if only editing metadata can save your VG though.

---

### Post by linuxandy76 on 2018-01-27
I think it should look more like this: 

# Generated by LVM2 version 2.02.98(2) (2012-10-15): SatFeb  6 17:00:03 2016

contents = "Text Format Volume Group"
version = 1

description = ""

creation_host = "apollo" # Linux apollo 3.13.0-77-generic #121-Ubuntu SMP Wed Jan 20 10:50:59 UTC 2016 i686
creation_time = 1454778003.# Sat Feb  6 17:00:03 2016


apollo-vg {
id = "Cj1Nj2-fKhq-i80z-ZtPd-HNru-c1Ts-uY4265"
seqno = 8
format = "lvm2" # informational
status =["RESIZEABLE", "READ", "WRITE"]
flags = []
extent_size= 8192
max_lv = 0
max_pv = 0
metadata_copies = 0

physical_volumes {

pv0 {
id = "aib9B7-521v-1wcN-xjHI-Pu2K-LAvI-zJfMYA"
device = "/dev/sda5"

status = ["ALLOCATABLE"]
flags = []
dev_size = 976269312
pe_start = 384
pe_count = 119173
}

pv1 {
id = "9BK8DS-NDHP-raPo-dlGO-oGTZ-FIsc-3yjVW4"
device = "/dev/sdb1"

status = ["ALLOCATABLE"]
flags = []
dev_size = 1953521664
pe_start = 2048
pe_count = 238466
}

pv2 {
id = "nZLEq4-FJMc-b6vS-lWKv-3QtS-lmjI-3QmjLg"
device = "/dev/sdc1"

status = ["ALLOCATABLE"]

flags = []
dev_size = 976771072
pe_start = 2048
pe_count = 119234
}

pv3 {
id = "s0sATe-D0Dj-qMrx-Ua8E-45pC-DJE2-seeNjH"
device = "/dev/sdd1"

status = ["ALLOCATABLE"]
flags = []
dev_size = 3907026944
pe_start = 2048
pe_count = 476931
}
}

logical_volumes {

root {
id = "eaMp86-9xVd-E3PY-yyOy-NeJg-8Ev9-ONVZ5n"
status = ["READ", "WRITE", "VISIBLE"]
flags = []
segment_count = 5

segment1 {
start_extent = 0
extent_count = 118161

type = "striped"
stripe_count = 1 # linear

stripes = [

"pv0", 0 
] 
}

segment2 {
start_extent = 118161
extent_count = 12

type = "striped"
stripe_count = 1 # linear

stripes = [
"pv0",119161
]
}

segment3 {
start_extent = 118173
extent_count= 238466
type = "striped"

stripe_count = 1.# linear

stripes = [
"pv1", 0 ]
}
segment4 {
start_extent = 356639
extent_count = 119234

type = "striped"
stripe_count = 1 # linear

stripes = [
"pv2", 0 ]
}
segment5 {
start_extent = 475873
extent_count =476931

type = "striped"
stripe_count = 1 # linear

stripes = [
"pv3", 0 
]
}
}

swap_1 {
id = "JLjBRh-Znkf-k53o-XpCJ-dwzP-Owjk-TnUfxB"
status = ["READ", "WRITE", "VISIBLE"]
flags = []
segment_count = 1

segment1 {
start_extent = 0
extent_count = 1000

type = "striped"
stripe_count = 1 # linear

stripes = [

"pv0", 118161 
]
}
}
}
}

---

### Post by linuxandy76 on 2018-01-27
I am hoping that the above gets me back on track - there is about 2.5tb worth of data there I would like to be able to get back. Annoyingly, I have been trying to get some backups of the data for the last 18 months or so but just hadnt found the time or a reasonable solution to get it done........

All because we had a new cooker installed and it blew the power - I have been blaming my wife and so have the kids !

---

### Post by darkod on 2018-01-27
If you didn't have a vgcgfbackup file taken, trying to construct one yourself can be dangerous.

I would try what he says at the end of his blog post. If I understand it correctly, he thinks he could have activated the VG and LVs anyway by using vgchange with --ignorelockingfailure. So before trying to use vgcfgrestore with a file you invented yourself, I would try something like this (in verbose mode):
```
vgchange -v -ay --ignorelockingfailure /dev/apollo-vg
```

---

### Post by darkod on 2018-01-27
Before trying to activate it, did you try running vgck or pvck to check it out first? You can deactivate the swap lv with:
```
vgchange -an /dev/apollo-vg
```

Best to run checks with volumes deactivated.

---

### Post by linuxandy76 on 2018-01-28
I managed to reconstruct the file with all the relevant information, and managed to boot the server - currently back to where we were beforehand. Thanks for your help Darkod

---


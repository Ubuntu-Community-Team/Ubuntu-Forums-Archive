---
title: "server boot drive failed, need help mounting existing raid drive"
date: 2022-11-14
forum: Server Platforms
---

### Post by tross9 on 2022-11-14
[COLOR=#000000][COLOR=#000000]my main boot drive sda failed, and I'm tiring to reinstall 16.04 ( will upgrade to 18 when dust settles )[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]I had a single raid drive ( need to use the second drive in another machine and had to break the mirror )[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]so the system was ( and should be)[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]1 - boot drive sda[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]1 - raid drive sdb as md127[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]I'm not able to mount the existing sdb/md127 , not sure what I need to put in the /etc/fstab for [/COLOR][/COLOR][COLOR=#000000][COLOR=#000000]uuid= 5273d21d-.....[/COLOR][/COLOR]
[COLOR=#000000]drive info:[/COLOR]
[COLOR=#000000][COLOR=#000000]fdisk the drive is a 1TB[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]/dev/sdb linux raid[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]/dev/md127[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]blkid[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]/dev/md127 ext4[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]df[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]drive does not show up[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]lsblk[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]sdb[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]sdb1 disk part[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]md127 raid1[/COLOR][/COLOR]


[COLOR=#000000][COLOR=#000000]not 100% sure what i need to add to fstab[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]not sure of the correct format for the line to add[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]uuid=572... /dev/md127 ext4[/COLOR][/COLOR]


[COLOR=#000000][COLOR=#000000]TIA[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]T Ross[/COLOR][/COLOR]

---

### Post by tross9 on 2022-11-14
addition info 


adding to fstab
  uuid=527....   /media  ext4  defaults 0 3
or
   uuid=527....   /media/sdb1  ext4  defaults 0 3
or
  uuid=527....   /media/md127  ext4  defaults 0 3
boots the system into emergency mode


but 

uuid=527....   /  ext4  defaults 0 3


boots the system ok but i do not see the drive or [COLOR=#000000]the folders.[/COLOR]

---

### Post by darkod on 2022-11-14
Trying to reinstall 16.04? Why that old, why not something newer? You should be able to use any new version, even 22.04 and it should recognize the raid.

Now back to your problem. Either from the new installation or from live mode, did you activate the raid, can you see it in the output of mdstat?
```
cat /proc/mdstat
```

Post the output here and we will know more.

---

### Post by tross9 on 2022-11-14
18. was giving me grief,  16.04 , the install was more familiar.

cat Info

  md127 : active (auto-read-only) raid1 sdb1(0) 
    976...  blocks super 1.2 [2/1] [u_]
    bitmap 6/8 pages [24kb] , 65536kb chunk 

unused devices: (none)

---

### Post by tross9 on 2022-11-14
after running the Cat command , i think I need to undo the read only,
  I ran mdadm  with  -a -r    which i found while trying to edit fstab

---

### Post by tross9 on 2022-11-15
Looks like I got the Raid drive to auto mount.

i could mount the drive manually   with CMD   mount /dev/md127  /media/raid        or    mount /dev/md127  /mnt/raid

but  using the UUID in **fstab** does not work 
      [COLOR=#000000]uuid=527.... /mnt/raid ext4 defaults 0 3     * (boots to emergency mode)*

what did work was in fstab was
        /dev/md127  /mnt/raid  ext4 defaults 0 3     ( [/COLOR][I][COLOR=#000000]boots ok and folders and data is visible in /mnt/raid)

[/COLOR][/I][COLOR=#000000]Thanks for the help.

my next step, upgrade then
I need to add users, check the raid drive that samba access is ok and check the database  

Again thanks

[/COLOR]

---

### Post by tross9 on 2022-11-15
I spoke too soon,

  after I ran apt-get update    and apt-get upgrade ,

now never fstab   command  will mount the raid drive.

---

### Post by darkod on 2022-11-15
Post the output (the full output) of the following and try to put it in CODE tags for easier reading:
```
sudo mdadm -D /dev/md127
sudo blkid
cat /etc/mdadm/mdadm.conf
```

You might be missing declaring the array in mdadm.conf so that it assembles correctly on boot.

---

### Post by tross9 on 2022-11-15
1) i reinstalled 16.04  ( upgraded to 18.04 then none of the Mdadm commands worked  -- errors superblock not found)
      so none of the previous mdadm commands, listed above, have been executed.


also here is the info you requested.  ( based on the uuid in the mdadm list maybe i need to point to sdb1?)

sudo mdadm -D /dev/md127


/dev/md127:
        Version : 1.2
  Creation Time : Sun Jan 10 11:47:32 2021
     Raid Level : raid1
     Array Size : 976630464 (931.39 GiB 1000.07 GB)
  Used Dev Size : 976630464 (931.39 GiB 1000.07 GB)
   Raid Devices : 2
  Total Devices : 1
    Persistence : Superblock is persistent


  Intent Bitmap : Internal


    Update Time : Tue Nov 15 13:27:43 2022
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0


           Name : serverclanross:0  (local to host serverclanross)
           UUID : 9f8bf34d:cec9426b:a9982750:0f71e4cd
         Events : 7017


    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       2       0        0        2      removed
	   
	   
 sudo blkid
/dev/sdb1: UUID="9f8bf34d-cec9-426b-a998-27500f71e4cd" UUID_SUB="16228b34-4992-e487-8dd5-f9f1616a0a68" LABEL="serverclanross:0" TYPE="linux_raid_member" PARTUUID="cbaa9abf-01"
/dev/sda1: UUID="9701b326-1f63-40d7-8b26-a2c53692f4dd" TYPE="ext2" PARTUUID="4d07e89a-01"
/dev/sda5: UUID="1kgC2D-xZ6E-TAhU-OoiZ-XmvX-UT2P-JLniZY" TYPE="LVM2_member" PARTUUID="4d07e89a-05"
/dev/md127: UUID="5723d21d-844a-4016-bf11-331608a50d7b" TYPE="ext4"
/dev/mapper/serverclanross--vg-root: UUID="bc839c25-c715-4eb9-9eef-fd3865eeeec3" TYPE="ext4"
/dev/mapper/serverclanross--vg-swap_1: UUID="8c964b59-db11-4a31-90f7-bc3a17aeb05c" TYPE="swap"




 cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#


# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers


# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes


# automatically tag new arrays as belonging to the local system
HOMEHOST <system>


# instruct the monitoring daemon where to send mail alerts
MAILADDR root


# definitions of existing MD arrays


# This file was auto-generated on Tue, 15 Nov 2022 13:48:10 -0500
# by mkconf $Id$

---

### Post by darkod on 2022-11-16
Like I said, you have no definition of the array in mdadm.conf. Edit mdadm.conf and in the section 'difinition of existing arrays' add the following line:
```
ARRAY /dev/md0 metadata=1.2 UUID=9f8bf34d:cec9426b:a9982750:0f71e4cd
```

Save the changes and reboot. After reboot check again with:
```
cat /proc/mdstat
```

You should see assembled array named md0. You can also check the UUID of the ext4 filesystem on it. According to above results it should be 5723d21d-844a-4016-bf11-331608a50d7b.

So now that you have made the array to auto-assemble on boot, in fstab you can use either the ext4 UUID or /dev/md0 and it should work to auto-mount.

And related to upgrade to 18.04, the only way not to recognize mdadm commands is if the mdadm package was not installed. On the other hand if it has mdadm commands but does not detect the array at all, you need to investigate what is going on and solve it. You can't keep 16.04 forever, it is already out of support.

---

### Post by tross9 on 2022-11-16
darkod, 
That work with one exception,   the raid is md127 not md0

Thanks for the help.  -- my next step to to upgrade to 18 before i do anything else.

fyi - not sure why this worked but the system booted with the following typo     mdo   (not zero) in the mdadm.conf    ( it may have been read-only when it booted with the typo)

ARRAY /dev/mdo   metadata=1.2 UUID=9f8bf34d:cec9426b:a9982750:0f71e4cd
   and 
in fstab   -   would not boot with md0 in fstab
# mount raid drive
   /dev/md127   /mnt/raid   ext4 defaults 0  3



i've corrected the mdadm.config to 
ARRAY /dev/md127 metadata=1.2 UUID=9f8bf34d:cec9426b:a9982750:0f71e4cd

---

### Post by tross9 on 2022-11-16
darkod,
That work with one exception, the raid is md127 not md0

Thanks for the help. -- my next step to to upgrade to 18 before i do anything else.

fyi - not sure why this worked but the system booted with the following typo mdo (not zero) in the mdadm.conf ( it may have been read-only when it booted with the typo)

ARRAY /dev/mdo metadata=1.2 UUID=9f8bf34d:cec9426b:a9982750:0f71e4cd
and
in fstab - would not boot with md0 in fstab
# mount raid drive
/dev/md127 /mnt/raid ext4 defaults 0 3



i've corrected the mdadm.config to
ARRAY /dev/md127 metadata=1.2 UUID=9f8bf34d:cec9426b:a9982750:0f71e4cd

---

### Post by darkod on 2022-11-16
The md name is just a name, it doesn't matter which one is it as long as you use it correctly in all needed places. Ubuntu uses md127 after failures and to reassemble sometimes.

I always prefer fixating it to md0, md1, md2, in mdadm.conf and like that it stays with that fixed name. But if you want you can leave it as md127.

Glad it worked out.

---


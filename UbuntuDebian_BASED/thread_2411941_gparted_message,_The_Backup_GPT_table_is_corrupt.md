---
title: "gparted message, The Backup GPT table is corrupt"
date: 2019-02-05
forum: Ubuntu/Debian BASED
---

### Post by grahamadgo on 2019-02-05
Hi 

My O/S is Elementary 0.4.1 Loki and my knowledge of Linux is pretty poor. I predominantly use GUI's and can use command line if i have too (but my knowledge of the text that i'm typing is virtually non existent) 

I have been given a 2tb external hard drive which is outrageously slow to transfer data  2-4 mb/s so was looking to format it using gparted 

A warning repeatedly comes up saying "The Backup GPT table is corrupt, but the primary appears OK, so that will be used."  I have searched the threads and found a few that seem to be of a similar description but do not have the knowledge to know if the solutions are applicable to me.

Now firstly, is it possible that this problem is causing the slow transfer rate? and secondly is it worth me trying with my limited knowledge to try to correct this, if possible?

Many thanks

---

### Post by oldos2er on 2019-02-05
Thread moved to Ubuntu/Debian BASED.

---

### Post by oldfred on 2019-02-05
You should just be able to run gdisk.
But if data is at all valuable make sure you have good backups before any changes or repairs.

       repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html) 
            Use gdisk and verify partitions are correct with p, or v to review issues,  and use w to write the partition table. If not correct just use q to quit. That should update primary, backup & protective MBR. 
See also:
[https://askubuntu.com/questions/386752/fixing-corrupt-backup-gpt-table/386802#386802](https://askubuntu.com/questions/386752/fixing-corrupt-backup-gpt-table/386802#386802)

---

### Post by grahamadgo on 2019-02-06
Thanks for the advice

I looked through the threads but must admit that although i could gleam some information I was quickly lost on all three.

I did however use gdisk (hopefully correctly) using p, v and then w and got the readout below

After re-booting and running gparted again I still get the 'backup GPT table is corrupt' warning

There is mention in the text of using the Recovery and Options menu but I note that it says (experts only) a description that definitely doesn't describe me, so I didn't go down that route.

  	 	 	 	   ~$ sudo gdisk /dev/sdd
 [sudo] password for agg:        
 GPT fdisk (gdisk) version 1.0.4
 
 
 Caution: invalid backup GPT header, but valid main header; regenerating
 backup header from main header.
 
 
 Warning! Main and backup partition tables differ! Use the 'c' and 'e' options
 on the recovery & transformation menu to examine the two tables.
 
 
 Warning! One or more CRCs don't match. You should repair the disk!
 Main header: OK
 Backup header: ERROR
 Main partition table: OK
 Backup partition table: ERROR
 
 
 Partition table scan:
   MBR: protective
   BSD: not present
   APM: not present
   GPT: damaged
 
 
 ****************************************************************************
 Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
 verification and recovery are STRONGLY recommended.
 ****************************************************************************
 
 
 Command (? for help): ?
 b	back up GPT data to a file
 c	change a partition's name
 d	delete a partition
 i	show detailed information on a partition
 l	list known partition types
 n	add a new partition
 o	create a new empty GUID partition table (GPT)
 p	print the partition table
 q	quit without saving changes
 r	recovery and transformation options (experts only)
 s	sort partitions
 t	change a partition's type code
 v	verify disk
 w	write table to disk and exit
 x	extra functionality (experts only)
 ?	print this menu
 
 
 Command (? for help): v
 
 
 Caution: The CRC for the backup partition table is invalid. This table may
 be corrupt. This program will automatically create a new backup partition
 table when you save your partitions.
 
 
 Identified 1 problems!
 
 
 Command (? for help): p
 Disk /dev/sdd: 3912499200 sectors, 1.8 TiB
 Model: Flash Disk       
 Sector size (logical/physical): 512/512 bytes
 Disk identifier (GUID): 00000000-0000-0000-0000-000000000000
 Partition table holds up to 128 entries
 Main partition table begins at sector 2 and ends at sector 33
 First usable sector is 34, last usable sector is 3912499166
 Partitions will be aligned on 2048-sector boundaries
 Total free space is 4029 sectors (2.0 MiB)
 
 
 Number  Start (sector)    End (sector)  Size       Code  Name
    1            2048      3912497151   1.8 TiB     0700   
 
 
 Command (? for help): w
 
 
 Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
 PARTITIONS!!
 
 
 Do you want to proceed? (Y/N): y
 OK; writing new GUID partition table (GPT) to /dev/sdd.
 Warning: The kernel is still using the old partition table.
 The new table will be used at the next reboot or after you
 run partprobe(8) or kpartx(8)
 The operation has completed successfully.

---

### Post by oldfred on 2019-02-06
I have never used the r repair & recovery menu.
But if it says use it and the c or e commands, it sounds like that is what you need to do.

You can go into a menu & print commands to be sure what they do.
And you always can exit.

---

### Post by grahamadgo on 2019-02-07
Hi

I tried the c and e commands under the recovery and options menu and got the following response. They both refer to rebuilding from disk - is this correct?

```
$ sudo gdisk /dev/sdd
[sudo] password for agg:       
GPT fdisk (gdisk) version 1.0.4

Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.

Warning! Main and backup partition tables differ! Use the 'c' and 'e' options
on the recovery & transformation menu to examine the two tables.

Warning! One or more CRCs don't match. You should repair the disk!
Main header: OK
Backup header: ERROR
Main partition table: OK
Backup partition table: ERROR

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************

Command (? for help): ?
b    back up GPT data to a file
c    change a partition's name
d    delete a partition
i    show detailed information on a partition
l    list known partition types
n    add a new partition
o    create a new empty GUID partition table (GPT)
p    print the partition table
q    quit without saving changes
r    recovery and transformation options (experts only)
s    sort partitions
t    change a partition's type code
v    verify disk
w    write table to disk and exit
x    extra functionality (experts only)
?    print this menu

Command (? for help): r

Recovery/transformation command (? for help): c
Warning! This will probably do weird things if you've converted an MBR to
GPT form and haven't yet saved the GPT! Proceed? (Y/N): y
Caution! After loading partitions, the CRC doesn't check out!

Recovery/transformation command (? for help): e
Warning! This will probably do weird things if you've converted an MBR to
GPT form and haven't yet saved the GPT! Proceed? (Y/N): y

Recovery/transformation command (? for help): ?
b    use backup GPT header (rebuilding main)
c    load backup partition table from disk (rebuilding main)
d    use main GPT header (rebuilding backup)
e    load main partition table from disk (rebuilding backup)
f    load MBR and build fresh GPT from it
g    convert GPT into MBR and exit
h    make hybrid MBR
i    show detailed information on a partition
l    load partition data from a backup file
m    return to main menu
o    print protective MBR data
p    print the partition table
q    quit without saving changes
t    transform BSD disklabel partition
v    verify disk
w    write table to disk and exit
x    extra functionality (experts only)
?    print this menu

Recovery/transformation command (? for help): v

No problems found. 4029 free sectors (2.0 MiB) available in 2
segments, the largest of which is 2015 (1007.5 KiB) in size.

Recovery/transformation command (? for help): i
Using 1
Partition GUID code: EBD0A0A2-B9E5-4433-87C0-68B6B72699C7 (Microsoft basic data)
Partition unique GUID: 08D9F23D-6A62-445D-8DE4-384D9B056B12
First sector: 2048 (at 1024.0 KiB)
Last sector: 3912497151 (at 1.8 TiB)
Partition size: 3912495104 sectors (1.8 TiB)
Attribute flags: 0000000000000000
Partition name: ''

Recovery/transformation command (? for help): o

Disk size is 3912499200 sectors (1.8 TiB)
MBR disk identifier: 0x00000000
MBR partitions:

Number  Boot  Start Sector   End Sector   Status      Code
   1                     1   3912499199   primary     0xEE

Recovery/transformation command (? for help): p
Disk /dev/sdd: 3912499200 sectors, 1.8 TiB
Model: Flash Disk      
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): 00000000-0000-0000-0000-000000000000
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 3912499166
Partitions will be aligned on 2048-sector boundaries
Total free space is 4029 sectors (2.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048      3912497151   1.8 TiB     0700  

Recovery/transformation command (? for help):
```

---


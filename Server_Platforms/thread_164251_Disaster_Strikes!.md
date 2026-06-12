---
title: "Disaster Strikes!"
date: 2006-04-22
forum: Server Platforms
---

### Post by elminster13 on 2006-04-22
Hi All,

I hope you can offer me some advice?

One of my hard discs failed about a week ago, im using a highpoint raid controller (no xor function) with 4 x 160gb discs on ubuntu. Wher i have a root filesystem running on a standalone hard disc, and i mount the RAID as a media storage area.

Today I opened my box up removed the faulty hard disc added a new one and booted my system, heres where the good ole case of fat fingers occured.

The system popped up with a box saying Power Off, Destroy, Continue.... I accidently hit destroy! I was on the brink of a blood vessel bursting!

Anyway now im up the stream without a paddle and need some advice. I recreated the array with the 'No Build' option thinking it would keep the filesystem intact, but unfortunately i think the superblock or some RAID filesystem parameters has still been overwritten as when i mount the partition i get:
---------------------------
$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
----------------------------
$ dmesg | tail
[4294716.954000] ide: failed opcode was: 0xec
[4294717.101000] hdb: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[4294717.101000] hdb: drive_cmd: error=0x04 { AbortedCommand }
[4294717.101000] ide: failed opcode was: 0xec
[4341548.929000] ibm_acpi: ec object not found
[4346933.078000] ibm_acpi: ec object not found
[4364836.516000] e100: eth0: e100_watchdog: link down
[4364854.516000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[4365827.564000] EXT3-fs error (device md0): ext3_check_descriptors: Block bitmap for group 1920 not in group (block 0)!
[4365827.602000] EXT3-fs: group descriptors corrupted !
---------------------------------------
Have I gone past the point of no return or is there some recourse for my fat finger syndrome???

Regards

Andrew

---

### Post by imagine on 2006-04-23
Some random ideas, maybe there are of any use:

I guess the RAID controller overwrote the beginning of your virtual disk, with the boot sector, partition table and the superblock of the first partition. At least that what was I had last year. Took me two days to recover most of the data, but the backup was 400 km away...



If I was an A S S (nice censoring here), I'd tell you to simply restore the backup of your master boot record with dd.  If you have written down the exact sizes of your partitions, you could also recreate the partition table manually. Restoring bootloader and the signature should be easy too, so you have your MBR back.

First stage bootloader in the first 446 bytes
Partition table in the next 64 bytes
AA55 signature in the remaining 2 bytes



Other than that, did you try applications like testdisk or gpart to recover the partition table?
Some filesystems store backups of their superblock on certain places, but I can't give you any exact information about that.

---

### Post by elminster13 on 2006-04-26
Thanks for the suggestion of testdisk, I have started it anaylsing /dev/md0 and will hopefully have a result when i get back on friday. I have never used it before so with any luck it will say "click here to repair partition" - hmmm i can but hope.

Please correct me but do i need a MBR? is that only used if i was booting from the array? Which im not. I am mounting it post boot.

Bearing this in mind is the structure you described still applicable? But then this doesn't really matter becuase this is just a home array with media on it. I did not back it up because it was already in a RAID5.

Granted in hindsight I should have backed up the first portion of the array. But then what information it the RAID control adding here? i know it does not do hardware RAID so does it store any information about the array? is there any point in having it, other than to provide additional ide ports?

---


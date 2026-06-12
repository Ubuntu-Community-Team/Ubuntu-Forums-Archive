---
title: "3tb seagate drive won't GPT"
date: 2013-10-24
forum: Server Platforms
---

### Post by bnut2 on 2013-10-24
Searched and have not been able to identify the problem here.

Trying to install a 3TB drive on a new 12.04.3 build (3.8.0-29-generic #42~precise1-Ubuntu).  The drive is visible in POST.  Motherboard is Asus H61M-A with latest BIOS applied (H61M-A BIOS 0904).

I can see the drive with lshw

```
root@host:~# lshw -class disk
  *-disk
       description: ATA Disk
       product: HDS724040KLSA80
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: KFAO
       serial: KRFS2CRAHPRAED
       size: 372GiB (400GB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=5 guid=c528b63b-fb7e-4499-8967-8721174e60ff
  *-disk
       description: ATA Disk
       product: ST3000DM001
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       version: CC24
       serial: W1F2N8AH
       size: 3950MiB (4142MB)
       configuration: ansiversion=5
root@host:~#

```

I am unable to label gpt with parted
```


root@host:~# parted /dev/sdb
GNU Parted 2.3
Using /dev/sdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) mklabel
New disk label type? gpt
Error: Input/output error during read on /dev/sdb
Retry/Ignore/Cancel? ^C
parted) quit


```

I am unable to label with gdisk
```

root@host:~# gdisk /dev/sdb
GPT fdisk (gdisk) version 0.8.1

Warning! Read error 5; strange behavior now likely!
Warning! Read error 5; strange behavior now likely!
Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.

Command (? for help): o
This option deletes all partitions and creates a new protective MBR.
Proceed? (Y/N): y

Command (? for help): w

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): y
OK; writing new GUID partition table (GPT).
Unable to save backup partition table! Perhaps the 'e' option on the experts'
menu will resolve this problem.
Warning! An error was reported when writing the partition table! This error
MIGHT be harmless, but you may have trashed the disk!

Command (? for help):  quit

```
gdisk -l /dev/sdb
```

root@host:~# gdisk -l /dev/sdb
GPT fdisk (gdisk) version 0.8.1

Warning! Read error 5; strange behavior now likely!
Warning! Read error 5; strange behavior now likely!
Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.
Disk /dev/sdb: 8089950 sectors, 3.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 3B75FD5A-FE5D-46CE-A230-69F987195C18
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 8089916
Partitions will be aligned on 2048-sector boundaries
Total free space is 8089883 sectors (3.9 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
root@host:~#

```


any guidance?

---

### Post by oldfred on 2013-10-25
Is BIOS in AHCI mode not IDE?

It may just be a defective hard drive. Does vendor have any test utilities you can run?

---

### Post by bnut on 2013-10-25
Thanks, oldfred.  

Yes, the BIOS is set to AHCI.  Interestingly, however, it appears that I see the drive in the POST but not in BIOS.  

The drive is obviously recognized at some hardware layer, since I can see it in lshw and it appears in dmesg (albeit with very little usable information).

Still not sure how to proceed.  Perhaps I'll try to swap it out with another 3tb, but more than likely I'll replace it with a 2tb pending any other suggestions.

Cheers.


edit, hey look!  my old account works again!  Thanks SSO!!!  </sarcasm>

---


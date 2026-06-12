---
title: "Restoring Raid after hardware crash"
date: 2016-02-21
forum: Server Platforms
---

### Post by Andrew_Sampson on 2016-02-21
Hi
I wonder if anyone can offer any advice.
I am helping a small non-profit which provides, for free, Education DVD's and equipment, to the developing world on issues relating to health and education in very remote areas.
Two months ago their dedicated server with 1 and 1 had a hard disk crash and the website and contents dissapeared. 
Unfortunately a back up system was not in place to store the contents elsewhere.
However 1&1 has told us that the contenst do exist on a Raid drive and installing this onto the new hard-drive should reinstall everything.
However they do not provide support how to do this. 
So essentially I am wondering if an expert here can help us through the process of transferring the contents.
1&1 have sent us this link
[https://help.1and1.com/servers-c37684/dedicated-server-linux-c37687/rescue-and-recovery-c37690/rebuild-a-software-raid-array-a730894.html](https://help.1and1.com/servers-c37684/dedicated-server-linux-c37687/rescue-and-recovery-c37690/rebuild-a-software-raid-array-a730894.html)
Which supposed explains how to do this - but to a novice it is not easy to know what to and when!
I have spent the day researching and via SSh have gained the following information.
**cat /proc/mdstat **shows the following:
```

- Personalities : [linear] [raid0] [raid1] [raid10] [raid6] [raid5] [raid4] [fault                                                                                                                                                             y]
- md1 : active raid1 sdb1[1]
      4194240 blocks [2/1] [_U]

- md3 : active raid1 sdb3[1]
      482094016 blocks [2/1] [_U]

- unused devices: <none>

```

**fdisk -l **shows this
```

- Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
-Disk /dev/sda doesn't contain a valid partition table

- Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         523     4194304   fd  Linux raid autodetect
Partition 1 does not end on cylinder boundary.
/dev/sdb2             523         784     2097152   82  Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
/dev/sdb3             784       60802   482094104   fd  Linux raid autodetect
Partition 3 does not end on cylinder boundary.

- Disk /dev/md3: 493.6 GB, 493664272384 bytes
2 heads, 4 sectors/track, 120523504 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk /dev/md3 doesn't contain a valid partition table

- Disk /dev/md1: 4294 MB, 4294901760 bytes
2 heads, 4 sectors/track, 1048560 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk /dev/md1 doesn't contain a valid partition table


```

It's at this point we are stuck!

Really appreciate any advice

---

### Post by darkod on 2016-02-21
Post the output of these two commands to start with:
```
sudo parted /dev/sda unit MiB print
sudo parted /dev/sdb unit MiB print
```

---

### Post by darkod on 2016-02-21
While waiting for that, let me comment on something...

Their instructions are basically the standard instructions to replace a failed disk in software mdadm raid. But what I don't understand is why the server would fail if only one disk failed. The point of raid1 is that the machine can continue working when a disk fails. So even without doing this procedure the server should already be online. Is it?

You obviously can access it by ssh. But do the services and websites work?

---

### Post by Andrew_Sampson on 2016-02-21
Thanks so much for the reply darkod
Please forgive me if I sound really stupid and make mistakes - I know about websites - not servers and am out of my comfort zones here!
So:
**sudo parted /dev/sda unit MiB print**

```

Disk geometry for /dev/sdb: 0.000-476940.023 megabytes
Disk label type: msdos
Minor    Start       End     Type      Filesystem  Flags
1          1.000   4097.000  primary   ext3        raid
2       4097.000   6145.000  primary   linux-swap
3       6145.000 476940.023  primary               raid

```

[B]sudo parted /dev/sdb unit MiB print

[/B]```
Disk geometry for /dev/sdb: 0.000-476940.023 megabytes
Disk label type: msdos
Minor    Start       End     Type      Filesystem  Flags
1          1.000   4097.000  primary   ext3        raid
2       4097.000   6145.000  primary   linux-swap
3       6145.000 476940.023  primary               raid

```

---

### Post by Andrew_Sampson on 2016-02-21
Just read this before I answerd the other one
So - what I know is - and I am volunteering to help the charity btw.
So the website went down
They got notified by 1&1 of a hardware error
Told the hardware was going to be replaced and that if the Raid contents were restored the website woudl come back
We have the FTP into the server - which i can provide - but there are no webcontents - just server software of some kind.
I have got involved in this at the tail end because they were getting desperate.
But no - website and contents are not available at all.

Thanks

Andrew

---

### Post by Andrew_Sampson on 2016-02-21
You can see here
tme.org.uk

---

### Post by darkod on 2016-02-21
Did you run those commands correctly? Both outputs seem to show /dev/sdb when the first one should show /dev/sda partitions.

The thing that is still confusing me is that with raid1 if only one disk failed the server should have happily keep running and serving the websites. On the other hand, if both disks failed and there is no backup, where did 1&1 come up with one disk to give you to setup and saying you will have the data back???

Is it possible they gave you one disk with basic default ubuntu installation (not identical disk to the ones the server had) and they expect you to upload the web content yourself again?

---

### Post by Andrew_Sampson on 2016-02-21
So here is the full showing from /sda
The path was **(parted)** and I added **/dev/sda unit MiB print**
**(parted) /dev/sda unit MiB print**
```

  check MINOR                   do a simple check on the filesystem
  cp [FROM-DEVICE] FROM-MINOR TO-MINOR      copy filesystem to another partition
  help [COMMAND]                prints general help, or help on COMMAND
  mklabel LABEL-TYPE            create a new disklabel (partition table)
  mkfs MINOR FS-TYPE            make a filesystem FS-TYPE on partititon MINOR
  mkpart PART-TYPE [FS-TYPE] START END      make a partition
  mkpartfs PART-TYPE FS-TYPE START END      make a partition with a filesystem
  move MINOR START END          move partition MINOR
  name MINOR NAME               name partition MINOR NAME
  print [MINOR]                 display the partition table, or a partition
  quit                          exit program
  rescue START END              rescue a lost partition near START and END
  resize MINOR START END        resize filesystem on partition MINOR
  rm MINOR                      delete partition MINOR
  select DEVICE                 choose the device to edit
  set MINOR FLAG STATE          change a flag on partition MINOR
  check MINOR                   do a simple check on the filesystem
  cp [FROM-DEVICE] FROM-MINOR TO-MINOR      copy filesystem to another partition
  help [COMMAND]                prints general help, or help on COMMAND
  mklabel LABEL-TYPE            create a new disklabel (partition table)
  mkfs MINOR FS-TYPE            make a filesystem FS-TYPE on partititon MINOR
  mkpart PART-TYPE [FS-TYPE] START END      make a partition
  mkpartfs PART-TYPE FS-TYPE START END      make a partition with a filesystem
  move MINOR START END          move partition MINOR
  name MINOR NAME               name partition MINOR NAME
  print [MINOR]                 display the partition table, or a partition
  quit                          exit program
  rescue START END              rescue a lost partition near START and END
  resize MINOR START END        resize filesystem on partition MINOR
  rm MINOR                      delete partition MINOR
  select DEVICE                 choose the device to edit
  set MINOR FLAG STATE          change a flag on partition MINOR
  check MINOR                   do a simple check on the filesystem
  cp [FROM-DEVICE] FROM-MINOR TO-MINOR      copy filesystem to another partition
  help [COMMAND]                prints general help, or help on COMMAND
  mklabel LABEL-TYPE            create a new disklabel (partition table)
  mkfs MINOR FS-TYPE            make a filesystem FS-TYPE on partititon MINOR
  mkpart PART-TYPE [FS-TYPE] START END      make a partition
  mkpartfs PART-TYPE FS-TYPE START END      make a partition with a filesystem
  move MINOR START END          move partition MINOR
  name MINOR NAME               name partition MINOR NAME
  print [MINOR]                 display the partition table, or a partition
  quit                          exit program
  rescue START END              rescue a lost partition near START and END
  resize MINOR START END        resize filesystem on partition MINOR
  rm MINOR                      delete partition MINOR
  select DEVICE                 choose the device to edit
  set MINOR FLAG STATE          change a flag on partition MINOR
Disk geometry for /dev/sdb: 0.000-476940.023 megabytes
Disk label type: ms
Minor    Start       End     Type      Filesystem  Flags
1          1.000   4097.000  primary   ext3        raid
2       4097.000   6145.000  primary   linux-swap
3       6145.000 476940.023  primary               raid

```

For /sdb The path was **(parted)** and I added [B]/dev/sdb unit MiB print
[/B]
```

(parted) /dev/sdb unit MiB print
  check MINOR                   do a simple check on the filesystem
  cp [FROM-DEVICE] FROM-MINOR TO-MINOR      copy filesystem to another partition
  help [COMMAND]                prints general help, or help on COMMAND
  mklabel LABEL-TYPE            create a new disklabel (partition table)
  mkfs MINOR FS-TYPE            make a filesystem FS-TYPE on partititon MINOR
  mkpart PART-TYPE [FS-TYPE] START END      make a partition
  mkpartfs PART-TYPE FS-TYPE START END      make a partition with a filesystem
  move MINOR START END          move partition MINOR
  name MINOR NAME               name partition MINOR NAME
  print [MINOR]                 display the partition table, or a partition
  quit                          exit program
  rescue START END              rescue a lost partition near START and END
  resize MINOR START END        resize filesystem on partition MINOR
  rm MINOR                      delete partition MINOR
  select DEVICE                 choose the device to edit
  set MINOR FLAG STATE          change a flag on partition MINOR
  check MINOR                   do a simple check on the filesystem
  cp [FROM-DEVICE] FROM-MINOR TO-MINOR      copy filesystem to another partition
  help [COMMAND]                prints general help, or help on COMMAND
  mklabel LABEL-TYPE            create a new disklabel (partition table)
  mkfs MINOR FS-TYPE            make a filesystem FS-TYPE on partititon MINOR
  mkpart PART-TYPE [FS-TYPE] START END      make a partition
  mkpartfs PART-TYPE FS-TYPE START END      make a partition with a filesystem
  move MINOR START END          move partition MINOR
  name MINOR NAME               name partition MINOR NAME
  print [MINOR]                 display the partition table, or a partition
  quit                          exit program
  rescue START END              rescue a lost partition near START and END
  resize MINOR START END        resize filesystem on partition MINOR
  rm MINOR                      delete partition MINOR
  select DEVICE                 choose the device to edit
  set MINOR FLAG STATE          change a flag on partition MINOR
  check MINOR                   do a simple check on the filesystem
  cp [FROM-DEVICE] FROM-MINOR TO-MINOR      copy filesystem to another partition
  help [COMMAND]                prints general help, or help on COMMAND
  mklabel LABEL-TYPE            create a new disklabel (partition table)
  mkfs MINOR FS-TYPE            make a filesystem FS-TYPE on partititon MINOR
  mkpart PART-TYPE [FS-TYPE] START END      make a partition
  mkpartfs PART-TYPE FS-TYPE START END      make a partition with a filesystem
  move MINOR START END          move partition MINOR
  name MINOR NAME               name partition MINOR NAME
  print [MINOR]                 display the partition table, or a partition
  quit                          exit program
  rescue START END              rescue a lost partition near START and END
  resize MINOR START END        resize filesystem on partition MINOR
  rm MINOR                      delete partition MINOR
  select DEVICE                 choose the device to edit
  set MINOR FLAG STATE          change a flag on partition MINOR
Disk geometry for /dev/sdb: 0.000-476940.023 megabytes
Disk label type: msdos
Minor    Start       End     Type      Filesystem  Flags
1          1.000   4097.000  primary   ext3        raid
2       4097.000   6145.000  primary   linux-swap
3       6145.000 476940.023  primary               raid
(parted)

```

---

### Post by Andrew_Sampson on 2016-02-21
RE:
> The thing that is still confusing me is that with raid1 if only one disk  failed the server should have happily keep running and serving the  websites. On the other hand, if both disks failed and there is no  backup, where did 1&1 come up with one disk to give you to setup and  saying you will have the data back???
Now, they said that the data should be downloaded but it was a huge amount and impossible to do (on a slow UK broadband connection)

> Is it possible they gave you one disk with basic default ubuntu  installation (not identical disk to the ones the server had) and they  expect you to upload the web content yourself again?
This is what we don't understand - and 1&1 provide 0 support for their dedicated servers it turns out.
The understanding is that all is contained on the Raid..
Otherwise don't understand the point of sending us the Raid install stuff.
As I said in my original post - we do not have the experience of servers to understand everything.
Truth is - The dedicated server was setup by someone else no longer with the NGO - in the belief because there was a lot of content - it was the best way to go. Reality is a managed server with a different customer friendly company would have been better!

Andrew

---

### Post by darkod on 2016-02-21
No, no... The commands I gave you should be run from the standard command prompt, not the parted prompt. That command will simply print the layout, it won't even go into parted prompt.

Please try them again and post it. If you ssh as root leave out the sudo in front too, you don't need sudo as root. If you ssh as another user you do need the sudo.

---

### Post by Andrew_Sampson on 2016-02-21
Ah ok!
We have root entry
So this is what happened
This is the command line prompt (with root login) rescue:~# 
[B]I entered: parted /dev/sda unit MiB print
Result was
```
[/B]
Usage: parted [OPTION]... [DEVICE [COMMAND [PARAMETERS]...]...]
Apply COMMANDs with PARAMETERS to DEVICE.  If no COMMAND(s) are given, runs in
interactive mode.

OPTIONs:
  -h, --help                    displays this help message
  -i, --interactive             where necessary, prompts for user intervention
  -s, --script                  never prompts for user intervention
  -v, --version                 displays the version

COMMANDs:
  check MINOR                   do a simple check on the filesystem
  cp [FROM-DEVICE] FROM-MINOR TO-MINOR      copy filesystem to another partition
  help [COMMAND]                prints general help, or help on COMMAND
  mklabel LABEL-TYPE            create a new disklabel (partition table)
  mkfs MINOR FS-TYPE            make a filesystem FS-TYPE on partititon MINOR
  mkpart PART-TYPE [FS-TYPE] START END      make a partition
  mkpartfs PART-TYPE FS-TYPE START END      make a partition with a filesystem
  move MINOR START END          move partition MINOR
  name MINOR NAME               name partition MINOR NAME
  print [MINOR]                 display the partition table, or a partition
  quit                          exit program
  rescue START END              rescue a lost partition near START and END
  resize MINOR START END        resize filesystem on partition MINOR
  rm MINOR                      delete partition MINOR
  select DEVICE                 choose the device to edit
  set MINOR FLAG STATE          change a flag on partition MINOR
[B]
```
[/B]which seems to be the command options

---

### Post by darkod on 2016-02-21
That's very weird output... This is an ubuntu server right?

Lets try the long version... In that case try entering the parted prompt, change the unit size and print the partition table:
```
parted /dev/sda
unit MiB
print
```

If that worked change the device to /dev/sdb, print it and quit parted:
```
select /dev/sdb
print
quit
```

That should give you the partition layout printed one by one...

---

### Post by Andrew_Sampson on 2016-02-21
Now you have got me thinking
And very embarrassed
I just realised reading 1&1 that maybe they haven't installed Ubuntu on the basic system
[http://www.1and1.co.uk/dedicated-server?__lf=Order-Product](http://www.1and1.co.uk/dedicated-server?__lf=Order-Product)
[http://www.1and1.co.uk/server-configuration?__lf=Order-Product&__sendingdata=1&cart.action=add-bundle&cart.bundle=tariff-ded-server-l-4-bundle&cart.ignoreFlow=true&__jumptopageflow=Order-Tariff](http://www.1and1.co.uk/server-configuration?__lf=Order-Product&__sendingdata=1&cart.action=add-bundle&cart.bundle=tariff-ded-server-l-4-bundle&cart.ignoreFlow=true&__jumptopageflow=Order-Tariff)
In fact they have installed Centos on the hardware they have replaced and also on the raid system
So huge apologies for wasting your time
Andrew

---

### Post by darkod on 2016-02-21
No problem. It's still strange though because parted should act the same...

But if you expect to get ubuntu on the new server too, you better take it up with them if they gave you centos. I have to say quite disappointing from their side, their lack of support. After all it is their HW that failed, they shouldn't make you do this with 0 support. And I'm still wondering how they expect you to get the data back.

Maybe they installed new server for you (with centos instead of ubuntu) and expect you to connect to the old server /disk and copy the data. Or upload your own data. But that approach would be pointless if you don't have a recent copy of the data. And in case they can provide access to the disk of the old machine, you have to ask them how to copy it over their internal network, which would be very fast. As opposed to download and then upload over the internet. They should at least do that for you, offer you how to copy it locally, even if they are not giving you much support.

You need to have a long talk with them mate... This is ridiculous.

---

### Post by Andrew_Sampson on 2016-02-21
Thanks for your understanding!
You are completely right it is ridiculous.
But I just discovered something - searching around I found a command to put in
**dmesg**
and I found out something else - the operating system might be Debian.
But completely in the dark!
```

rescue:~# dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.10.56 (root@ds-kbuildd-amd64) (gcc version 4.3.2 (Debian 4.3.2-1.1) ) #1 SMP Mon Oct 6 11:30:02 UTC 2014
[    0.000000] Command line: console=tty0 console=ttyS0,57600 load_ramdisk=1 prompt_ramdisk=0 ramdisk_size=393216 initrd=linux/rescue64-2.6-sarge.gz pw=$1$kaMw/j3b$rPLF..E9IFmQ5a7r.whL7/ tz=Europe/London root=/dev/ram0 rw BOOT_IMAGE=linux/kernel64-2.6
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009dbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009dc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000d0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000def5ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000def60000-0x00000000def69fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000def6a000-0x00000000def7ffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000def80000-0x00000000dfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fc000000-0x00000000fdffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fff80000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000011fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: FUJITSU SIEMENS D2461-C1                      /D2461-C1, BIOS 6.00 R1.15.2461.C1               10/22/2007
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x120000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E3FFF uncachable
[    0.000000]   E4000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0080000000 mask FFC0000000 write-back
[    0.000000]   2 base 00C0000000 mask FFF0000000 write-back
[    0.000000]   3 base 00D0000000 mask FFF8000000 write-back
[    0.000000]   4 base 00D8000000 mask FFFC000000 write-back
[    0.000000]   5 base 00DC000000 mask FFFE000000 write-back
[    0.000000]   6 base 00DE000000 mask FFFF000000 write-back
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000120000000 aka 4608M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: update [mem 0xdf000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xdef60 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000f7860-0x000f786f] mapped at [ffff8800000f7860]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x020cd000, 0x020cdfff] PGTABLE
[    0.000000] BRK [0x020ce000, 0x020cefff] PGTABLE
[    0.000000] BRK [0x020cf000, 0x020cffff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x11fe00000-0x11fffffff]
[    0.000000]  [mem 0x11fe00000-0x11fffffff] page 2M
[    0.000000] BRK [0x020d0000, 0x020d0fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x11c000000-0x11fdfffff]
[    0.000000]  [mem 0x11c000000-0x11fdfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x100000000-0x11bffffff]
[    0.000000]  [mem 0x100000000-0x11bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xdef5ffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0xdedfffff] page 2M
[    0.000000]  [mem 0xdee00000-0xdef5ffff] page 4k
[    0.000000] RAMDISK: [mem 0x7abe4000-0x7fffffff]
[    0.000000] ACPI: RSDP 00000000000f7830 00014 (v00 PTLTD )
[    0.000000] ACPI: RSDT 00000000def669ee 00038 (v01 PTLTD    RSDT   00060000  LTP 00000000)
[    0.000000] ACPI: FACP 00000000def69c4a 00074 (v01 FSC             00060000      000F4240)
[    0.000000] ACPI: DSDT 00000000def66a26 03224 (v01 FSC    D246x    00060000 MSFT 03000001)
[    0.000000] ACPI: FACS 00000000def6afc0 00040
[    0.000000] ACPI: SSDT 00000000def69cbe 0028A (v01 PTLTD  POWERNOW 00060000  LTP 00000001)
[    0.000000] ACPI: APIC 00000000def69f48 00054 (v01 PTLTD  ? APIC   00060000  LTP 00000000)
[    0.000000] ACPI: MCFG 00000000def69f9c 0003C (v01 PTLTD    MCFG   00060000  LTP 00000000)
[    0.000000] ACPI: BOOT 00000000def69fd8 00028 (v01 PTLTD  $SBFTBL$ 00060000  LTP 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000011fffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x11fffffff]
[    0.000000]   NODE_DATA [mem 0x11fff8000-0x11fffbfff]
[    0.000000]  [ffffea0000000000-ffffea00047fffff] PMD -> [ffff88011b600000-ffff88011f5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x11fffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0xdef5ffff]
[    0.000000]   node   0: [mem 0x100000000-0x11fffffff]
[    0.000000] On node 0 totalpages: 1044220
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14206 pages used for memmap
[    0.000000]   DMA32 zone: 909152 pages, LIFO batch:31
[    0.000000]   Normal zone: 2048 pages used for memmap
[    0.000000]   Normal zone: 131072 pages, LIFO batch:31
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000def60000 - 00000000def6a000
[    0.000000] PM: Registered nosave memory: 00000000def6a000 - 00000000def80000
[    0.000000] PM: Registered nosave memory: 00000000def80000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fe000000
[    0.000000] PM: Registered nosave memory: 00000000fe000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
[    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000fff80000
[    0.000000] PM: Registered nosave memory: 00000000fff80000 - 0000000100000000
[    0.000000] e820: [mem 0xe0000000-0xfbffffff] available for PCI devices
[    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88011fc00000 s80192 r8192 d22208 u1048576
[    0.000000] pcpu-alloc: s80192 r8192 d22208 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1027881
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: console=tty0 console=ttyS0,57600 load_ramdisk=1 prompt_ramdisk=0 ramdisk_size=393216 initrd=linux/rescue64-2.6-sarge.gz pw=$1$kaMw/j3b$rPLF..E9IFmQ5a7r.whL7/ tz=Europe/London root=/dev/ram0 rw BOOT_IMAGE=linux/kernel64-2.6
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 7ca000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ d4000000
[    0.000000] PM: Registered nosave memory: 00000000d4000000 - 00000000d8000000
[    0.000000] Memory: 3876000k/4718592k available (9853k kernel code, 541712k absent, 300880k reserved, 5322k data, 988k init)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]  RCU restricting CPUs from NR_CPUS=64 to nr_cpu_ids=2.
[    0.000000] NR_IRQS:4352 nr_irqs:512 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] console [ttyS0] enabled
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2611.952 MHz processor
[    0.000000] tsc: Marking TSC unstable due to TSCs unsynchronized
[    0.020000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5223.90 BogoMIPS (lpj=10447808)
[    0.024002] pid_max: default: 32768 minimum: 301
[    0.028029] Security Framework initialized
[    0.032268] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.041146] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.048556] Mount-cache hash table entries: 256
[    0.052198] Initializing cgroup subsys freezer
[    0.056025] tseg: 00def80000
[    0.056027] CPU: Physical Processor ID: 0
[    0.060002] CPU: Processor Core ID: 0
[    0.064002] mce: CPU supports 5 MCE banks
[    0.068008] LVT offset 0 assigned for vector 0xf9
[    0.072003] process: using AMD E400 aware idle routine
[    0.076003] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.076003] Last level dTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.076003] tlb_flushall_shift: 4
[    0.080080] Freeing SMP alternatives: 40k freed
[    0.084019] ACPI: Core revision 20130328
[    0.089231] ACPI: All ACPI Tables successfully acquired
[    0.104684] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.149138] smpboot: CPU0: Dual-Core AMD Opteron(tm) Processor 1218 HE (fam: 0f, model: 43, stepping: 03)
[    0.168000] Performance Events: AMD PMU driver.
[    0.172002] ... version:                0
[    0.176000] ... bit width:              48
[    0.180000] ... generic registers:      4
[    0.184000] ... value mask:             0000ffffffffffff
[    0.188000] ... max period:             00007fffffffffff
[    0.192001] ... fixed-purpose events:   0
[    0.196001] ... event mask:             000000000000000f
[    0.200200] MCE: In-kernel MCE decoding enabled.
[    0.204090] smpboot: Booting Node   0, Processors  #1 OK
[    0.300099] Brought up 2 CPUs
[    0.304001] smpboot: Total of 2 processors activated (10448.01 BogoMIPS)
[    0.312352] PM: Registering ACPI NVS region [mem 0xdef6a000-0xdef7ffff] (90112 bytes)
[    0.316037] kworker/u4:0 (17) used greatest stack depth: 5728 bytes left
[    0.316193] xor: measuring software checksum speed
[    0.356002]    prefetch64-sse:  7848.000 MB/sec
[    0.400001]    generic_sse:  7848.000 MB/sec
[    0.404001] xor: using function: generic_sse (7848.000 MB/sec)
[    0.408025] RTC time: 12:39:28, date: 02/18/16
[    0.412036] NET: Registered protocol family 16
[    0.416130] node 0 link 0: io port [1000, fffff]
[    0.416130] TOM: 00000000e0000000 aka 3584M
[    0.424005] node 0 link 0: mmio [fc000000, fdffffff]
[    0.424007] node 0 link 0: mmio [a0000, bffff]
[    0.424009] node 0 link 0: mmio [e0000000, fe0bffff]
[    0.424010] TOM2: 0000000120000000 aka 4608M
[    0.432002] bus: [bus 00-ff] on node 0 link 0
[    0.432004] bus: 00 [io  0x0000-0xffff]
[    0.432005] bus: 00 [mem 0xe0000000-0xffffffff]
[    0.432006] bus: 00 [mem 0x000a0000-0x000bffff]
[    0.432008] bus: 00 [mem 0x120000000-0xfcffffffff]
[    0.436053] ACPI: bus type PCI registered
[    0.444039] PCI: MMCONFIG for domain 0000 [bus 00-03] at [mem 0xfc000000-0xfc3fffff] (base 0xfc000000)
[    0.460009] PCI: MMCONFIG at [mem 0xfc000000-0xfc3fffff] reserved in E820
[    0.476014] PCI: Using configuration type 1 for base access
[    0.500045] bio: create slab <bio-0> at 0
[    0.572018] raid6: sse2x1    3291 MB/s
[    0.644015] raid6: sse2x2    4436 MB/s
[    0.716023] raid6: sse2x4    4638 MB/s
[    0.720005] raid6: using algorithm sse2x4 (4638 MB/s)
[    0.724004] raid6: using intx1 recovery algorithm
[    0.728026] ACPI: Added _OSI(Module Device)
[    0.732005] ACPI: Added _OSI(Processor Device)
[    0.736004] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.740005] ACPI: Added _OSI(Processor Aggregator Device)
[    0.744519] ACPI: EC: Look up EC in DSDT
[    0.746048] ACPI: Interpreter enabled
[    0.748013] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130328/hwxface-568)
[    0.760013] ACPI: (supports S0 S1 S3 S4 S5)
[    0.764005] ACPI: Using IOAPIC for interrupt routing
[    0.768050] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.788090] ACPI: No dock devices found.
[    0.804185] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.816060] acpi PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.816062] acpi PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.816064] acpi PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.816067] acpi PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff] (ignored)
[    0.816069] acpi PNP0A03:00: host bridge window [mem 0xe0000000-0xfebfffff] (ignored)
[    0.816071] acpi PNP0A03:00: host bridge window [mem 0xfed00000-0xfedfffff] (ignored)
[    0.816074] PCI: root bus 00: hardware-probed resources
[    0.816080] acpi PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-03] only partially covers this bridge
[    0.836023] PCI host bridge to bus 0000:00
[    0.844007] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.856002] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
[    0.868002] pci_bus 0000:00: root bus resource [mem 0xe0000000-0xffffffff]
[    0.884002] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.896002] pci_bus 0000:00: root bus resource [mem 0x120000000-0xfcffffffff]
[    0.912012] pci 0000:00:00.0: [10de:02f0] type 00 class 0x050000
[    0.912087] pci 0000:00:00.1: [10de:02fa] type 00 class 0x050000
[    0.912087] pci 0000:00:00.2: [10de:02fe] type 00 class 0x050000
[    0.912089] pci 0000:00:00.3: [10de:02f8] type 00 class 0x050000
[    0.912091] pci 0000:00:00.4: [10de:02f9] type 00 class 0x050000
[    0.912091] pci 0000:00:00.5: [10de:02ff] type 00 class 0x050000
[    0.912091] pci 0000:00:00.6: [10de:027f] type 00 class 0x050000
[    0.912091] pci 0000:00:00.7: [10de:027e] type 00 class 0x050000
[    0.912091] pci 0000:00:02.0: [10de:02fc] type 01 class 0x060400
[    0.912091] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.912091] pci 0000:00:02.0: System wakeup disabled by ACPI
[    0.924040] pci 0000:00:03.0: [10de:02fd] type 01 class 0x060400
[    0.924049] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.924077] pci 0000:00:03.0: System wakeup disabled by ACPI
[    0.936029] pci 0000:00:05.0: [10de:0241] type 00 class 0x030000
[    0.936033] pci 0000:00:05.0: reg 10: [mem 0xf1000000-0xf1ffffff]
[    0.936038] pci 0000:00:05.0: reg 14: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.936043] pci 0000:00:05.0: reg 1c: [mem 0xf0000000-0xf0ffffff 64bit]
[    0.936049] pci 0000:00:05.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.936098] pci 0000:00:09.0: [10de:0270] type 00 class 0x050000
[    0.936261] pci 0000:00:0a.0: [10de:0260] type 00 class 0x060100
[    0.936261] pci 0000:00:0a.0: reg 10: [io  0x8800-0x887f]
[    0.936261] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.948052] pci 0000:00:0a.1: [10de:0264] type 00 class 0x0c0500
[    0.948063] pci 0000:00:0a.1: reg 20: [io  0x88c0-0x88ff]
[    0.948070] pci 0000:00:0a.1: reg 24: [io  0x8880-0x88bf]
[    0.948105] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.948157] pci 0000:00:0b.0: [10de:026d] type 00 class 0x0c0310
[    0.948157] pci 0000:00:0b.0: reg 10: [mem 0xf2200000-0xf2200fff]
[    0.948157] pci 0000:00:0b.0: supports D1 D2
[    0.948157] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.948157] pci 0000:00:0b.0: System wakeup disabled by ACPI
[    0.960029] pci 0000:00:0b.1: [10de:026e] type 00 class 0x0c0320
[    0.960040] pci 0000:00:0b.1: reg 10: [mem 0xf2204000-0xf22040ff]
[    0.960083] pci 0000:00:0b.1: supports D1 D2
[    0.960085] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.960113] pci 0000:00:0b.1: System wakeup disabled by ACPI
[    0.972051] pci 0000:00:0d.0: [10de:0265] type 00 class 0x01018a
[    0.972059] pci 0000:00:0d.0: reg 20: [io  0x8c00-0x8c0f]
[    0.972120] pci 0000:00:0e.0: [10de:0266] type 00 class 0x010185
[    0.972120] pci 0000:00:0e.0: reg 10: [io  0x8c40-0x8c47]
[    0.972120] pci 0000:00:0e.0: reg 14: [io  0x8c34-0x8c37]
[    0.972120] pci 0000:00:0e.0: reg 18: [io  0x8c38-0x8c3f]
[    0.972120] pci 0000:00:0e.0: reg 1c: [io  0x8c30-0x8c33]
[    0.972120] pci 0000:00:0e.0: reg 20: [io  0x8c10-0x8c1f]
[    0.972120] pci 0000:00:0e.0: reg 24: [mem 0xf2201000-0xf2201fff]
[    0.972136] pci 0000:00:0f.0: [10de:0267] type 00 class 0x010185
[    0.972136] pci 0000:00:0f.0: reg 10: [io  0x8c58-0x8c5f]
[    0.972136] pci 0000:00:0f.0: reg 14: [io  0x8c4c-0x8c4f]
[    0.972136] pci 0000:00:0f.0: reg 18: [io  0x8c50-0x8c57]
[    0.972136] pci 0000:00:0f.0: reg 1c: [io  0x8c48-0x8c4b]
[    0.972136] pci 0000:00:0f.0: reg 20: [io  0x8c20-0x8c2f]
[    0.972136] pci 0000:00:0f.0: reg 24: [mem 0xf2202000-0xf2202fff]
[    0.972145] pci 0000:00:10.0: [10de:026f] type 01 class 0x060401
[    0.972145] pci 0000:00:10.0: System wakeup disabled by ACPI
[    0.984036] pci 0000:00:14.0: [10de:0268] type 00 class 0x020000
[    0.984046] pci 0000:00:14.0: reg 10: [mem 0xf2203000-0xf2203fff]
[    0.984051] pci 0000:00:14.0: reg 14: [io  0x8c60-0x8c67]
[    0.984083] pci 0000:00:14.0: supports D1 D2
[    0.984085] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.984112] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.996032] pci 0000:00:18.0: [1022:1100] type 00 class 0x060000
[    0.996075] pci 0000:00:18.1: [1022:1101] type 00 class 0x060000
[    0.996075] pci 0000:00:18.2: [1022:1102] type 00 class 0x060000
[    0.996075] pci 0000:00:18.3: [1022:1103] type 00 class 0x060000
[    0.996075] pci 0000:00:02.0: PCI bridge to [bus 01]
[    1.004037] pci 0000:00:03.0: PCI bridge to [bus 02]
[    1.016048] pci 0000:00:10.0: PCI bridge to [bus 04] (subtractive decode)
[    1.028007] pci 0000:00:10.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    1.028010] pci 0000:00:10.0:   bridge window [mem 0xe0000000-0xffffffff] (subtractive decode)
[    1.028012] pci 0000:00:10.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    1.028014] pci 0000:00:10.0:   bridge window [mem 0x120000000-0xfcffffffff] (subtractive decode)
[    1.028024] acpi PNP0A03:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    1.044016] acpi PNP0A03:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    1.060208] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 7 10 11 14 15) *0, disabled.
[    1.079122] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7 10 11 14 15) *0, disabled.
[    1.092540] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 7 10 11 14 15) *0, disabled.
[    1.108540] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 10 11 14 15) *0, disabled.
[    1.124540] ACPI: PCI Interrupt Link [LNKE] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    1.140539] ACPI: PCI Interrupt Link [LNKF] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    1.158570] ACPI: PCI Interrupt Link [LNKG] (IRQs 16 17 18 19 20 21 22 23) *11
[    1.173558] ACPI: PCI Interrupt Link [LNKH] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    1.188538] ACPI: PCI Interrupt Link [LNKI] (IRQs 16 17 18 19 20 21 22 23) *7
[    1.205091] ACPI: PCI Interrupt Link [LNKJ] (IRQs 16 17 18 19 20 21 22 23) *11
[    1.220076] ACPI: PCI Interrupt Link [LNKK] (IRQs 16 17 18 19 20 21 22 23) *10
[    1.234655] ACPI: PCI Interrupt Link [LNKL] (IRQs 16 17 18 19 20 21 22 23) *10
[    1.250107] ACPI: PCI Interrupt Link [LNKM] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    1.266568] ACPI: PCI Interrupt Link [LNKN] (IRQs 16 17 18 19 20 21 22 23) *5
[    1.281301] ACPI: PCI Interrupt Link [LNKO] (IRQs 16 17 18 19 20 21 22 23) *10
[    1.296545] ACPI: PCI Interrupt Link [LNKP] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    1.312766] ACPI: Enabled 1 GPEs in block 00 to 1F
[    1.320011] acpi root: \_SB_.PCI0 notify handler is installed
[    1.320040] Found 1 acpi root devices
[    1.320064] vgaarb: device added: PCI:0000:00:05.0,decodes=io+mem,owns=io+mem,locks=none
[    1.336006] vgaarb: loaded
[    1.344007] vgaarb: bridge control possible 0000:00:05.0
[    1.356062] SCSI subsystem initialized
[    1.360004] ACPI: bus type ATA registered
[    1.372028] libata version 3.00 loaded.
[    1.372032] ACPI: bus type USB registered
[    1.376040] usbcore: registered new interface driver usbfs
[    1.380019] usbcore: registered new interface driver hub
[    1.384019] usbcore: registered new device driver usb
[    1.388033] pps_core: LinuxPPS API ver. 1 registered
[    1.392003] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    1.396018] PTP clock support registered
[    1.400040] wmi: Mapper loaded
[    1.404014] PCI: Using ACPI for IRQ routing
[    1.408030] PCI: pci_cache_line_size set to 64 bytes
[    1.408068] e820: reserve RAM buffer [mem 0x0009dc00-0x0009ffff]
[    1.408070] e820: reserve RAM buffer [mem 0xdef60000-0xdfffffff]
[    1.412057] NetLabel: Initializing
[    1.416002] NetLabel:  domain hash size = 128
[    1.424000] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.436012] NetLabel:  unlabeled traffic allowed by default
[    1.448106] Switching to clocksource refined-jiffies
[    1.463759] FS-Cache: Loaded
[    1.468048] pnp: PnP ACPI init
[    1.472015] ACPI: bus type PNP registered
[    1.484365] system 00:00: [io  0x04d0-0x04d1] has been reserved
[    1.496012] system 00:00: [io  0x1000-0x107f] has been reserved
[    1.508006] system 00:00: [io  0x0600-0x067f] has been reserved
[    1.520006] system 00:00: [io  0xfe00] has been reserved
[    1.528007] system 00:00: [mem 0xfc000000-0xfdffffff] has been reserved
[    1.544008] system 00:00: [mem 0xfec00000-0xfecfffff] could not be reserved
[    1.556008] system 00:00: [mem 0xfee00000-0xfeefffff] could not be reserved
[    1.572011] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.572023] pnp 00:01: [dma 4]
[    1.572042] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.572072] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.572072] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.572072] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    1.572072] pnp 00:05: Plug and Play ACPI device, IDs PNP0103 (disabled)
[    1.572074] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    1.572096] pnp 00:07: Plug and Play ACPI device, IDs PNP0f13 (active)
[    1.572283] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
[    1.572283] pnp: PnP ACPI: found 9 devices
[    1.580016] ACPI: bus type PNP unregistered
[    1.597739] Switching to clocksource acpi_pm
[    1.604216] pci 0000:00:05.0: BAR 6: assigned [mem 0xf2000000-0xf201ffff pref]
[    1.618859] pci 0000:00:02.0: PCI bridge to [bus 01]
[    1.628870] pci 0000:00:03.0: PCI bridge to [bus 02]
[    1.638880] pci 0000:00:10.0: PCI bridge to [bus 04]
[    1.648901] pci 0000:00:10.0: setting latency timer to 64
[    1.648904] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    1.648906] pci_bus 0000:00: resource 5 [mem 0xe0000000-0xffffffff]
[    1.648908] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.648911] pci_bus 0000:00: resource 7 [mem 0x120000000-0xfcffffffff]
[    1.648914] pci_bus 0000:04: resource 4 [io  0x0000-0xffff]
[    1.648916] pci_bus 0000:04: resource 5 [mem 0xe0000000-0xffffffff]
[    1.648918] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    1.648920] pci_bus 0000:04: resource 7 [mem 0x120000000-0xfcffffffff]
[    1.648954] NET: Registered protocol family 2
[    1.657948] TCP established hash table entries: 32768 (order: 7, 524288 bytes)
[    1.672804] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    1.686353] TCP: Hash tables configured (established 32768 bind 32768)
[    1.699561] TCP: reno registered
[    1.706121] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    1.718258] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    1.731330] NET: Registered protocol family 1
[    1.740238] RPC: Registered named UNIX socket transport module.
[    1.752172] RPC: Registered udp transport module.
[    1.761686] RPC: Registered tcp transport module.
[    1.771182] RPC: Registered tcp NFSv4.1 backchannel transport module.
[    1.784172] pci 0000:00:00.0: Found disabled HT MSI Mapping
[    1.795401] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.805620] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    1.816689] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    1.827746] pci 0000:00:05.0: Boot video device
[    1.827945] ACPI: PCI Interrupt Link [LNKJ] enabled at IRQ 23
[    2.096210] ACPI: PCI Interrupt Link [LNKI] enabled at IRQ 22
[    2.107876] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    2.118972] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    2.130070] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    2.141131] PCI: CLS 64 bytes, default 64
[    2.141170] Trying to unpack rootfs image as initramfs...
[    2.152207] rootfs image is not initramfs (no cpio magic); looks like an initrd
[    2.235211] Freeing initrd memory: 86128k freed
[    2.288317] PCI-DMA: Disabling AGP.
[    2.295459] PCI-DMA: aperture base @ d4000000 size 65536 KB
[    2.306683] PCI-DMA: using GART IOMMU.
[    2.314266] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    2.330440] Simple Boot Flag at 0x36 set to 0x1
[    2.340176] microcode: AMD CPU family 0xf not supported
[    2.350725] Scanning for low memory corruption every 60 seconds
[    2.363180] sha1_ssse3: Neither AVX nor SSSE3 is available/usable.
[    2.375626] sha256_ssse3: Neither AVX nor SSSE3 is available/usable.
[    2.388411] sha512_ssse3: Neither AVX nor SSSE3 is available/usable.
[    2.401567] audit: initializing netlink socket (disabled)
[    2.412460] type=2000 audit(1455799167.411:1): initialized
[    2.428637] VFS: Disk quotas dquot_6.5.2
[    2.436674] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.451103] NFS: Registering the id_resolver key type
[    2.461317] Key type id_resolver registered
[    2.469776] Key type id_legacy registered
[    2.478088] NTFS driver 2.1.30 [Flags: R/W DEBUG].
[    2.487991] fuse init (API version 7.22)
[    2.496315] JFS: nTxBlock = 8192, nTxLock = 65536
[    2.509135] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[    2.529486] bio: create slab <bio-1> at 1
[    2.537929] Running btrfs free space cache tests
[    2.547256] Running extent only tests
[    2.554683] Running bitmap only tests
[    2.562101] Running bitmap and extent tests
[    2.570556] Free space cache tests finished
[    2.579004] Btrfs loaded
[    2.584165] msgmni has been set to 7867
[    2.593387] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 251)
[    2.608397] io scheduler noop registered
[    2.616328] io scheduler deadline registered
[    2.624955] io scheduler cfq registered (default)
[    2.634577] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    2.634688] pcieport 0000:00:03.0: irq 41 for MSI/MSI-X
[    2.634968] ipmi message handler version 39.2
[    2.643819] ipmi device interface
[    2.650652] IPMI System Interface driver.
[    2.658891] ipmi_si: Adding default-specified kcs state machine
[    2.670846] ipmi_si: Trying default-specified kcs state machine at i/o address 0xca2, slave address 0x0, irq 0
[    2.691006] ipmi_si: Interface detection failed
[    2.716032] ipmi_si: Adding default-specified smic state machine
[    2.728167] ipmi_si: Trying default-specified smic state machine at i/o address 0xca9, slave address 0x0, irq 0
[    2.751815] ipmi_si: Interface detection failed
[    2.780017] ipmi_si: Adding default-specified bt state machine
[    2.791785] ipmi_si: Trying default-specified bt state machine at i/o address 0xe4, slave address 0x0, irq 0
[    2.811589] ipmi_si: Interface detection failed
[    2.852185] ipmi_si: Unable to find any System Interface(s)
[    2.863412] IPMI Watchdog: driver initialized
[    2.872212] Copyright (C) 2004 MontaVista Software - IPMI Powerdown via sys_reboot.
[    2.887863] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    2.904386] ACPI: Power Button [PWRB]
[    2.911898] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    2.926853] ACPI: Power Button [PWRF]
[    2.964476] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    2.997574] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.009596] hpet_acpi_add: no address or irqs in _CRS
[    3.019915] Non-volatile memory driver v1.3
[    3.028474] Hangcheck: starting hangcheck timer 0.9.1 (tick is 180 seconds, margin is 60 seconds).
[    3.046565] Hangcheck: Using getrawmonotonic().
[    3.058109] brd: module loaded
[    3.065671] loop: module loaded
[    3.072827] Adaptec aacraid driver 1.2-0[30200]-ms
[    3.082570] isci: Intel(R) C600 SAS Controller Driver - version 1.1.0
[    3.095657] megaraid cmm: 2.20.2.7 (Release Date: Sun Jul 16 00:01:03 EST 2006)
[    3.110539] megaraid: 2.20.5.1 (Release Date: Thu Nov 16 15:32:35 EST 2006)
[    3.124593] megasas: 06.506.00.00-rc1 Sat. Feb. 9 17:00:00 PDT 2013
[    3.137267] mpt2sas version 14.100.00.00 loaded
[    3.146530] 3ware Storage Controller device driver for Linux v1.26.02.003.
[    3.160430] 3ware 9000 Storage Controller device driver for Linux v2.26.02.014.
[    3.175273] LSI 3ware SAS/SATA-RAID Controller device driver for Linux v3.26.02.000.
[    3.191366] sata_nv 0000:00:0e.0: version 3.5
[    3.191539] ACPI: PCI Interrupt Link [LNKN] enabled at IRQ 21
[    3.203130] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    3.212842] sata_nv 0000:00:0e.0: setting latency timer to 64
[    3.213392] scsi0 : sata_nv
[    3.219279] scsi1 : sata_nv
[    3.225125] ata1: SATA max UDMA/133 cmd 0x8c40 ctl 0x8c34 bmdma 0x8c10 irq 21
[    3.239477] ata2: SATA max UDMA/133 cmd 0x8c38 ctl 0x8c30 bmdma 0x8c18 irq 21
[    3.253955] ACPI: PCI Interrupt Link [LNKO] enabled at IRQ 20
[    3.265544] sata_nv 0000:00:0f.0: Using SWNCQ mode
[    3.275267] sata_nv 0000:00:0f.0: setting latency timer to 64
[    3.275816] scsi2 : sata_nv
[    3.281671] scsi3 : sata_nv
[    3.287507] ata3: SATA max UDMA/133 cmd 0x8c58 ctl 0x8c4c bmdma 0x8c20 irq 20
[    3.301862] ata4: SATA max UDMA/133 cmd 0x8c50 ctl 0x8c48 bmdma 0x8c28 irq 20
[    3.318334] cnic: Broadcom NetXtreme II CNIC Driver cnic v2.5.16 (Dec 05, 2012)
[    3.333253] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    3.345524] e100: Copyright(c) 1999-2006 Intel Corporation
[    3.356638] e1000: Intel(R) PRO/1000 Network Driver - version 7.3.21-k8-NAPI
[    3.370834] e1000: Copyright (c) 1999-2006 Intel Corporation.
[    3.382462] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    3.394203] e1000e: Copyright(c) 1999 - 2013 Intel Corporation.
[    3.406184] igb: Intel(R) Gigabit Ethernet Network Driver - version 5.0.3-k
[    3.420179] igb: Copyright (c) 2007-2013 Intel Corporation.
[    3.431460] ixgbe: Intel(R) 10 Gigabit PCI Express Network Driver - version 3.13.10-k
[    3.447279] ixgbe: Copyright (c) 1999-2013 Intel Corporation.
[    3.458917] ixgbevf: Intel(R) 10 Gigabit PCI Express Virtual Function Network Driver - version 2.7.12-k
[    3.477862] ixgbevf: Copyright (c) 2009 - 2012 Intel Corporation.
[    3.490179] ixgb: Intel(R) PRO/10GbE Network Driver - version 1.0.135-k2-NAPI
[    3.504523] ixgb: Copyright (c) 1999-2008 Intel Corporation.
[    3.516016] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    3.530952] ACPI: PCI Interrupt Link [LNKL] enabled at IRQ 19
[    3.542534] forcedeth 0000:00:14.0: setting latency timer to 64
[    3.628028] ata3: SATA link down (SStatus 0 SControl 300)
[    3.720042] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.766234] ata1.00: ATA-8: ST3500410AS, CC34, max UDMA/133
[    3.777456] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.846210] ata1.00: configured for UDMA/133
[    3.854981] scsi 0:0:0:0: Direct-Access     ATA      ST3500410AS      CC34 PQ: 0 ANSI: 5
[    3.871610] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    3.871681] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.897570] sd 0:0:0:0: [sda] Write Protect is off
[    3.907235] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.907286] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.947279]  sda: unknown partition table
[    3.955703] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.065008] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:19:99:23:92:02
[    4.081704] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
[    4.095243] Fusion MPT base driver 3.04.20
[    4.103531] Copyright (c) 1999-2008 LSI Corporation
[    4.113386] Fusion MPT SAS Host driver 3.04.20
[    4.122475] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.135615] ehci_hcd: block sizes: qh 112 qtd 96 itd 192 sitd 96
[    4.135619] ehci-pci: EHCI PCI platform driver
[    4.144643] ehci-pci 0000:00:0b.1: setting latency timer to 64
[    4.144661] ehci-pci 0000:00:0b.1: EHCI Host Controller
[    4.155201] ehci-pci 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    4.170162] ehci-pci 0000:00:0b.1: debug port 1
[    4.179308] ehci-pci 0000:00:0b.1: reset hcs_params 0x101888 dbg=1 cc=1 pcc=8 !ppc ports=8
[    4.179316] ehci-pci 0000:00:0b.1: reset portroute 0 0 0 0 0 0 0 0
[    4.179319] ehci-pci 0000:00:0b.1: reset hcc_params a086 caching frame 256/512/1024 park
[    4.179333] ehci-pci 0000:00:0b.1: park 0
[    4.179340] ehci-pci 0000:00:0b.1: reset command 0080b32  park=3 ithresh=8 Async Periodic period=1024 Reset HALT
[    4.179347] ehci-pci 0000:00:0b.1: cache line size of 64 is not supported
[    4.179348] ehci-pci 0000:00:0b.1: supports USB remote wakeup
[    4.179373] ehci-pci 0000:00:0b.1: irq 22, io mem 0xf2204000
[    4.190769] ehci-pci 0000:00:0b.1: init command 0010005 (park)=0 ithresh=1 period=512 RUN
[    4.200036] ehci-pci 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    4.211625] usb usb1: default language 0x0409
[    4.211632] usb usb1: udev 1, busnum 1, minor = 0
[    4.211634] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    4.225283] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.239888] usb usb1: Product: EHCI Host Controller
[    4.249730] usb usb1: Manufacturer: Linux 3.10.56 ehci_hcd
[    4.260777] usb usb1: SerialNumber: 0000:00:0b.1
[    4.270196] usb usb1: usb_probe_device
[    4.270199] usb usb1: configuration #1 chosen from 1 choice
[    4.270206] usb usb1: adding 1-0:1.0 (config #1, interface 0)
[    4.270278] hub 1-0:1.0: usb_probe_interface
[    4.270280] hub 1-0:1.0: usb_probe_interface - got id
[    4.270283] hub 1-0:1.0: USB hub found
[    4.277877] hub 1-0:1.0: 8 ports detected
[    4.285985] hub 1-0:1.0: standalone hub
[    4.285987] hub 1-0:1.0: no power switching (usb 1.0)
[    4.285988] hub 1-0:1.0: individual port over-current protection
[    4.285991] hub 1-0:1.0: power on to power good time: 20ms
[    4.285995] hub 1-0:1.0: local power source is good
[    4.286040] hub 1-0:1.0: trying to enable port power on non-switchable hub
[    4.286149] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.298586] ohci_hcd: block sizes: ed 80 td 96
[    4.298632] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    4.298635] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    4.309175] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    4.324151] ohci_hcd 0000:00:0b.0: created debug files
[    4.324153] ohci_hcd 0000:00:0b.0: supports USB remote wakeup
[    4.324172] ohci_hcd 0000:00:0b.0: irq 23, io mem 0xf2200000
[    4.348041] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.368427] ata2.00: ATA-8: ST3500413AS, JC4B, max UDMA/133
[    4.379650] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    4.384059] hub 1-0:1.0: state 7 ports 8 chg 0000 evt 0000
[    4.398013] ohci_hcd 0000:00:0b.0: OHCI controller state
[    4.398016] ohci_hcd 0000:00:0b.0: OHCI 1.0, NO legacy support registers, rh state running
[    4.398020] ohci_hcd 0000:00:0b.0: control 0x683 RWE RWC HCFS=operational CBSR=3
[    4.398022] ohci_hcd 0000:00:0b.0: cmdstatus 0x00000 SOC=0
[    4.398026] ohci_hcd 0000:00:0b.0: intrstatus 0x00000004 SF
[    4.398029] ohci_hcd 0000:00:0b.0: intrenable 0x8000004a MIE RHSC RD WDH
[    4.398035] ohci_hcd 0000:00:0b.0: hcca frame #0003
[    4.398039] ohci_hcd 0000:00:0b.0: roothub.a 01000208 POTPGT=1 NPS NDP=8(8)
[    4.398042] ohci_hcd 0000:00:0b.0: roothub.b 00000000 PPCM=0000 DR=0000
[    4.398046] ohci_hcd 0000:00:0b.0: roothub.status 00008000 DRWE
[    4.398050] ohci_hcd 0000:00:0b.0: roothub.portstatus [0] 0x00000100 PPS
[    4.398053] ohci_hcd 0000:00:0b.0: roothub.portstatus [1] 0x00000100 PPS
[    4.398057] ohci_hcd 0000:00:0b.0: roothub.portstatus [2] 0x00000100 PPS
[    4.398060] ohci_hcd 0000:00:0b.0: roothub.portstatus [3] 0x00000100 PPS
[    4.398064] ohci_hcd 0000:00:0b.0: roothub.portstatus [4] 0x00000100 PPS
[    4.398067] ohci_hcd 0000:00:0b.0: roothub.portstatus [5] 0x00000100 PPS
[    4.398071] ohci_hcd 0000:00:0b.0: roothub.portstatus [6] 0x00000100 PPS
[    4.398074] ohci_hcd 0000:00:0b.0: roothub.portstatus [7] 0x00000100 PPS
[    4.398081] usb usb2: default language 0x0409
[    4.398087] usb usb2: udev 1, busnum 2, minor = 128
[    4.398089] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    4.408575] ata2.00: configured for UDMA/133
[    4.408656] scsi 1:0:0:0: Direct-Access     ATA      ST3500413AS      JC4B PQ: 0 ANSI: 5
[    4.408843] sd 1:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    4.408905] sd 1:0:0:0: [sdb] Write Protect is off
[    4.408907] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.408933] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.409269] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    4.421813]  sdb: sdb1 sdb2 sdb3
[    4.422130] sd 1:0:0:0: [sdb] Attached SCSI disk
[    4.506232] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.520839] usb usb2: Product: OHCI Host Controller
[    4.530675] usb usb2: Manufacturer: Linux 3.10.56 ohci_hcd
[    4.541724] usb usb2: SerialNumber: 0000:00:0b.0
[    4.551130] usb usb2: usb_probe_device
[    4.551133] usb usb2: configuration #1 chosen from 1 choice
[    4.551140] usb usb2: adding 2-0:1.0 (config #1, interface 0)
[    4.551202] hub 2-0:1.0: usb_probe_interface
[    4.551204] hub 2-0:1.0: usb_probe_interface - got id
[    4.551206] hub 2-0:1.0: USB hub found
[    4.558793] hub 2-0:1.0: 8 ports detected
[    4.566897] hub 2-0:1.0: standalone hub
[    4.566898] hub 2-0:1.0: no power switching (usb 1.0)
[    4.566900] hub 2-0:1.0: global over-current protection
[    4.566902] hub 2-0:1.0: power on to power good time: 2ms
[    4.566906] hub 2-0:1.0: local power source is good
[    4.566908] hub 2-0:1.0: no over-current condition exists
[    4.566944] hub 2-0:1.0: trying to enable port power on non-switchable hub
[    4.566985] ohci_hcd 0000:00:0b.0: FS/LS companion for 0000:00:0b.1
[    4.567062] uhci_hcd: USB Universal Host Controller Interface driver
[    4.580071] usbcore: registered new interface driver usb-storage
[    4.592285] i8042: PNP: PS/2 Controller [PNP0303:KEYB,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    4.611803] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.621831] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.632153] mousedev: PS/2 mouse device common for all mice
[    4.643579] rtc_cmos 00:02: RTC can wake from S4
[    4.653068] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    4.665365] rtc_cmos 00:02: alarms up to one month, y3k, 114 bytes nvram
[    4.668047] hub 2-0:1.0: state 7 ports 8 chg 0000 evt 0000
[    4.679022] md: linear personality registered for level -1
[    4.690076] md: raid0 personality registered for level 0
[    4.700780] md: raid1 personality registered for level 1
[    4.711483] md: raid10 personality registered for level 10
[    4.722533] md: raid6 personality registered for level 6
[    4.733236] md: raid5 personality registered for level 5
[    4.736033] ata4: SATA link down (SStatus 0 SControl 300)
[    4.754803] md: raid4 personality registered for level 4
[    4.765511] md: faulty personality registered for level -5
[    4.776677] device-mapper: ioctl: 4.24.0-ioctl (2013-01-15) initialised: dm-devel@redhat.com
[    4.793734] device-mapper: raid: Loading target version 1.5.0
[    4.805304] cpuidle: using governor ladder
[    4.813579] cpuidle: using governor menu
[    4.821691] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    4.837101] hidraw: raw HID events driver (C) Jiri Kosina
[    4.848689] usbcore: registered new interface driver usbhid
[    4.859920] usbhid: USB HID core driver
[    4.867707] dell_wmi: No known WMI GUID found
[    4.876609] Netfilter messages via NETLINK v0.30.
[    4.886120] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[    4.898594] ctnetlink v0.93: registering with nfnetlink.
[    4.909457] ip_tables: (C) 2000-2006 Netfilter Core Team
[    4.920206] ipt_CLUSTERIP: ClusterIP Version 0.8 loaded successfully
[    4.933000] arp_tables: (C) 2002 David S. Miller
[    4.942323] TCP: cubic registered
[    4.949041] Initializing XFRM netlink socket
[    4.957959] NET: Registered protocol family 10
[    4.967114] mip6: Mobile IPv6
[    4.973155] ip6_tables: (C) 2000-2006 Netfilter Core Team
[    4.984099] sit: IPv6 over IPv4 tunneling driver
[    4.993912] NET: Registered protocol family 17
[    5.002924] Key type dns_resolver registered
[    5.012107] PM: Hibernation image not present or could not be loaded.
[    5.012114] registered taskstats version 1
[    5.020627]   Magic number: 4:731:683
[    5.031596] console [netcon0] enabled
[    5.039024] netconsole: network logging started
[    5.048273] powernow-k8: fid 0x12 (2600 MHz), vid 0xe
[    5.058465] powernow-k8: fid 0x10 (2400 MHz), vid 0x10
[    5.068819] powernow-k8: fid 0xe (2200 MHz), vid 0x10
[    5.079001] powernow-k8: fid 0xc (2000 MHz), vid 0x10
[    5.089184] powernow-k8: fid 0xa (1800 MHz), vid 0x10
[    5.099367] powernow-k8: fid 0x2 (1000 MHz), vid 0x12
[    5.109567] powernow-k8: Found 1 Dual-Core AMD Opteron(tm) Processor 1218 HE (2 cpu cores) (version 2.20.00)
[    5.129622] md: Waiting for all devices to be available before autodetect
[    5.143279] md: If you don't use raid, use raid=noautodetect
[    5.154913] md: Autodetecting RAID arrays.
[    5.198370] md: Scanned 2 and added 2 devices.
[    5.207352] md: autorun ...
[    5.213032] md: considering sdb3 ...
[    5.220274] md:  adding sdb3 ...
[    5.226822] md: sdb1 has different UUID to sdb3
[    5.236161] md: created md3
[    5.241853] md: bind<sdb3>
[    5.247367] md: running: <sdb3>
[    5.254020] md/raid1:md3: active with 1 out of 2 mirrors
[    5.264755] md3: detected capacity change from 0 to 493664272384
[    5.276909] md: considering sdb1 ...
[    5.284160] md:  adding sdb1 ...
[    5.290865] md: created md1
[    5.296552] md: bind<sdb1>
[    5.302083] md: running: <sdb1>
[    5.308739] md/raid1:md1: active with 1 out of 2 mirrors
[    5.319468] md1: detected capacity change from 0 to 4294901760
[    5.331274] md: ... autorun DONE.
[    5.338034] RAMDISK: gzip image found at block 0
[    7.330715] VFS: Mounted root (ext2 filesystem) on device 1:0.
[    7.343129] Freeing unused kernel memory: 988k freed
[    7.353521] Write protecting the kernel read-only data: 14336k
[    7.366204] Freeing unused kernel memory: 376k freed
[    7.378628] Freeing unused kernel memory: 976k freed
[    7.419139] uname (1569) used greatest stack depth: 4880 bytes left
[    7.434261] touch (1572) used greatest stack depth: 4384 bytes left
[    7.640230]  md3: unknown partition table
[    7.710138]  md1: unknown partition table
[    7.791762] vgscan (1785) used greatest stack depth: 3728 bytes left
[   10.322469] rcS (1567) used greatest stack depth: 3392 bytes left
[   63.271506] nf_conntrack: automatic helper assignment is deprecated and it will be removed soon. Use the iptables CT target to attach helpers instead.
[273305.016296] program parted is using a deprecated SCSI ioctl, please convert it to SG_IO
[273305.035661] program parted is using a deprecated SCSI ioctl, please convert it to SG_IO

```
Thanks anyway mate!
Really appreciate it

Andrew

---


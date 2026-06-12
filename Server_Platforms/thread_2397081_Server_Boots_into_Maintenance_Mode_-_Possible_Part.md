---
title: "Server Boots into Maintenance Mode - Possible Partition Code Error"
date: 2018-07-25
forum: Server Platforms
---

### Post by m-dw on 2018-07-25
My (headless) server has recently started to come up in maintenance mode after a reboot. I can issue Ctrl-D via the IPMI KVM and this allows the boot to complete. I've also found that "reboot", or "systemctl reboot" will generally result in a clean restart to the default run-level. The first time this happened was following a kernel update, but there have been other kernel updates since then, and the problem persists. I am not convinced that the kernel update caused the issue, but haven't ruled it out yet

The system disk has a GPT partition table, but the system is configured to boot in legacy BIOS mode. While looking (considering a switch to UEFI mode) I noticed that the root partition is flagged as an EFI system partition. I'm not sure if this has changed, or is normal.

```

 sudo gdisk -l /dev/sde
GPT fdisk (gdisk) version 1.0.3

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sde: 976773168 sectors, 465.8 GiB
Model: ST500LX025-1U717
Sector size (logical/physical): 512/4096 bytes
Disk identifier (GUID): 4CA55405-7A93-4F43-9D6E-1ED7E568F34F
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 2048-sector boundaries
Total free space is 634978285 sectors (302.8 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048       146485247   69.8 GiB    EF00  
   2       146485248       341796863   93.1 GiB    8300

```

parted shows that the partition has both boot and esp flags:

```

sudo parted /dev/sde
GNU Parted 3.2
Using /dev/sde
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print
Model: ATA ST500LX025-1U717 (scsi)
Disk /dev/sde: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  75.0GB  75.0GB  ext4               boot, esp
 2      75.0GB  175GB   100GB   ext4


```

Does the partition table look normal, or should root be listed marked as a Linux partition (code 8300) like /home?
Could this be the reason the system isn't booting fully?
What else do I need to look at?

---


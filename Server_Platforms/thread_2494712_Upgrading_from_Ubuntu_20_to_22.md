---
title: "Upgrading from Ubuntu 20 to 22"
date: 2024-01-24
forum: Server Platforms
---

### Post by sedberg1 on 2024-01-24
Running 20.04 on a physical server.  Ran do-release-upgrade and eventually got this:

EFI System Partition (ESP) not usable


Your EFI System Partition (ESP) is not mounted at /boot/efi. Please
ensure that it is properly configured and try again.

So I cancelled the upgrade.  And in looking at /etc/fstab:

# /boot/efi was on /dev/md126p1 during curtin installation
/dev/disk/by-id/md-uuid-40b533a3:c2adde52:2f037f32:62351b0f-part1 /boot/efi vfat defaults 0 1

There is an entry for /boot/efi.  However, there is no /boot/efi folder.  So I made a /boot/efi folder and tried mount /boot/efi.  Then got this error:

root@server1:/boot# mount /boot/efi
mount: /boot/efi: special device /dev/disk/by-id/md-uuid-40b533a3:c2adde52:2f037f32:62351b0f-part1 does not exist.

Not quite sure what to do here.  Any suggestions are welcome please.

---

### Post by oldfred on 2024-01-24
The ESP - EFI system partition must be FAT32 with boot,esp flags.
I do not think UEFI can read into LVM nor RAID, so ESP must be a partition.

---

### Post by sedberg1 on 2024-01-24
How do I fix that?

---

### Post by coffeecat on 2024-01-24
Support, not chat. *Thread moved to **Server Platforms**.*

---

### Post by kevdog on 2024-01-25
What are the partitions you currently have on the disk now?

---

### Post by MAFoElffen on 2024-01-25
I would run either the boot-info script or the system-info script and post the URLs of where the report of either uploads to. Probably best for what our problem currently is to use the Boot-Repair disk, and run the report without trying to do any repairs.

We rae going to have to find your EFI partition to be able to edit where it is in your fstab...

---

### Post by sedberg1 on 2024-05-29
How do I run the boot-info or system-info script?

---

### Post by darkod on 2024-05-29
Are you still having the issue? I am asking because you replied 4 months later.

I am old school and especially if the user is not very experienced with linux my way is stick to the basics.

Get the ubuntu desktop CD or USB and boot the server with it, selecting the Try Ubuntu option. That brigns you to a live session running from the usb/cd.

Open a terminal and give us the output of the following commands:
```
lsblk
sudo parted -l
```

---

### Post by sedberg1 on 2024-05-30
Yeah, still having issue.  Had to work on other things since I originally posted, but yeah, I still run into this with this server.  Ran those 2 commands:

srvcansible@cu-mlearn:~$ lsblk
NAME                      MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
loop0                       7:0    0  61.9M  1 loop  /snap/core20/1328
loop1                       7:1    0  67.2M  1 loop  /snap/lxd/21835
loop2                       7:2    0  43.6M  1 loop  /snap/snapd/14978
sda                         8:0    0 447.1G  0 disk
&#9500;&#9472;sda1                      8:1    0     1M  0 part
&#9500;&#9472;sda2                      8:2    0     2G  0 part
&#9492;&#9472;sda3                      8:3    0 445.1G  0 part
sdb                         8:16   0 447.1G  0 disk
&#9500;&#9472;sdb1                      8:17   0   1.1G  0 part
&#9500;&#9472;sdb2                      8:18   0   1.5G  0 part
&#9492;&#9472;sdb3                      8:19   0 444.6G  0 part
  &#9492;&#9472;ubuntu--vg-ubuntu--lv 253:0    0   100G  0 lvm   /
sdc                         8:32   0   3.7T  0 disk
&#9492;&#9472;md0                       9:0    0   7.3T  0 raid5 /data
sdd                         8:48   0   3.7T  0 disk
&#9492;&#9472;md0                       9:0    0   7.3T  0 raid5 /data
sde                         8:64   0   3.7T  0 disk
&#9492;&#9472;md0                       9:0    0   7.3T  0 raid5 /data
srvcansible@cu-mlearn:~$ sudo parted -l
Model: ATA PNY CS1311 480GB (scsi)
Disk /dev/sda: 480GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2097kB  1049kB                     bios_grub
 2      2097kB  2150MB  2147MB  ext4
 3      2150MB  480GB   478GB




Model: ATA PNY CS1311 480GB (scsi)
Disk /dev/sdb: 480GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  1128MB  1127MB  fat32              boot, esp
 2      1128MB  2739MB  1611MB  ext4
 3      2739MB  480GB   477GB




Error: /dev/sdc: unrecognised disk label
Model: ATA ST4000NM0033-9ZM (scsi)
Disk /dev/sdc: 4001GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:


Error: /dev/sdd: unrecognised disk label
Model: ATA ST4000NM0033-9ZM (scsi)
Disk /dev/sdd: 4001GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:


Error: /dev/sde: unrecognised disk label
Model: ATA ST4000NM0033-9ZM (scsi)
Disk /dev/sde: 4001GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-ubuntu--lv: 107GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags:


Number  Start  End    Size   File system  Flags
 1      0.00B  107GB  107GB  ext4




Model: Linux Software RAID Array (md)
Disk /dev/md0: 8001GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags:


Number  Start  End     Size    File system  Flags
 1      0.00B  8001GB  8001GB  ext4

---

### Post by darkod on 2024-05-30
Well according to the flags sdb1 seems to be an EFI partition. These commands do not show whether there are any files there actually.

But you can try mounting it with something like:
```
sudo mount -t vfat /dev/sdb1 /boot/efi
```

See how that goes and whether there are any files in /boot/efi after that.

There are other strange things in your setup but I guess that is topic for another day. sda and sdb seem to be similar 480GB disks but only sdb seems to be used (sdb3 is in LVM and mounted as /). What is the purpose of sda??

---


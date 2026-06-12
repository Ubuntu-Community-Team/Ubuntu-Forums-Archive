---
title: "Found a dos partition table in /dev/nvme1n1"
date: 2019-02-21
forum: Server Platforms
---

### Post by peter-o-nilsson on 2019-02-21
Hi, 
we have a setup at Amazon where we use the 16.04 LTS AMI. 
Today we planned to change to the newer 18.04 LTS AMI. 
We do this by updating the Cloudformation template with the latest AMI-ID. 
But when running the Cloudformation template we get this error at the backup volume setup, 

  > 2019-02-21 09:25:17,234 P8657 [INFO]    Set up backup volume
  2019-02-21 09:25:17,234 P8657 [INFO]    mke2fs 1.44.1 (24-Mar-2018)
  2019-02-21 09:25:17,234 P8657 [INFO]    Found a dos partition table in
  /dev/nvme1n1 2019-02-21 09:25:17,234 P8657 [INFO]    Proceed anyway?
  (y,N)  2019-02-21 09:25:17,235 P8657 [INFO]
  ------------------------------------------------------------ 2019-02-21 09:25:17,235 P8657 [ERROR] Exited with error code 1 

Doing the same thing with the latest 16.04 LTS AMI is working without any problems. The first thing that I saw was that the mke2fs versions are different, mke2fs 1.42.13 for 16.04 and mke2fs 1.44.1 for 18.04. 
Are there any big differences for the way those versions handles the filesystems? The volumes are already created, we just want them attached again.

Here is some output from the 16.04 LTS installation. 

fdisk output: 
  > Disk /dev/nvme1n1: 1 TiB, 1099511627776 bytes, 2147483648 sectors
  Units: sectors of 1 * 512 = 512 bytes Sector size (logical/physical):
  512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512
  bytes
  
  
  Disk /dev/nvme0n1: 32 GiB, 34359738368 bytes, 67108864 sectors Units:
  sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512
  bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes
  Disklabel type: dos Disk identifier: 0x30c871d7
  
  Device         Boot Start      End  Sectors Size Id Type
  /dev/nvme0n1p1 *     2048 67108830 67106783  32G 83 Linux
  
  
  Disk /dev/nvme2n1: 1000 GiB, 1073741824000 bytes, 2097152000 sectors
  Units: sectors of 1 * 512 = 512 bytes Sector size (logical/physical):
  512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512
  bytes

parted output: 
  > Model: NVMe Device (nvme) Disk /dev/nvme0n1: 34.4GB Sector size
  (logical/physical): 512B/512B Partition Table: msdos Disk Flags: 
  
  Number  Start   End     Size    Type     File system  Flags  1     
  1049kB  34.4GB  34.4GB  primary  ext4         boot
  
  
  Model: NVMe Device (nvme) Disk /dev/nvme1n1: 1100GB Sector size
  (logical/physical): 512B/512B Partition Table: loop Disk Flags: 
  
  Number  Start  End     Size    File system  Flags  1      0.00B 
  1100GB  1100GB  ext4
  
  
  Model: NVMe Device (nvme) Disk /dev/nvme2n1: 1074GB Sector size
  (logical/physical): 512B/512B Partition Table: loop Disk Flags: 
  
  Number  Start  End     Size    File system  Flags  1      0.00B 
  1074GB  1074GB  ext4

fstab output:
  > LABEL=cloudimg-rootfs   /        ext4   defaults,discard        0 0
  /dev/nvme1n1 /backup auto noatime 0 0 
  /dev/nvme2n1 /data auto noatime 0 0

---


---
title: "Unused Space on New Installation"
date: 2022-02-23
forum: Server Platforms
---

### Post by Dii_Reno on 2022-02-23
I have a fresh installation of 20.04 and a 3.7T Partition labeled Linux filesystem I need to mount. Does anyone know a howto that outlines how I can mount it? Simple instructions are welcome as well.

---

### Post by #&amp;thj^% on 2022-02-23
there are several ways - lsblk, fdisk, parted, blkid.
To find the partion:
```
lsblk  --noheadings --raw | awk '{print substr($0,0,4)}' | uniq -c | grep 1 | awk '{print "/dev/"$2}'

```
Example:
```
/dev/sda
/dev/sda1
/dev/sda2
/dev/sda3
/dev/sdb
/dev/sdb1
/dev/sdb2
/dev/sdc
/dev/sdd
/dev/sde
/dev/sde1


```
Or for user friendly output use:
```
sudo blkid -o list
```
Example:
```
device             fs_type   label      mount point            UUID
---------------------------------------------------------------------------------------------------
/dev/nvme0n1p3     ntfs      Windows-SSD (not mounted)         3C6263306262EDD8
/dev/nvme0n1p1     vfat      SYSTEM_DRV (not mounted)          2A62-972E
/dev/nvme0n1p4     ntfs      WINRE_DRV  (not mounted)          A45C638B5C635758
/dev/nvme0n1p2                          (not mounted)          
/dev/sdb2          ext4                 /                      83a67b34-74db-4267-acf9-4748469b3625
/dev/sdb1          vfat      NO_LABEL   /boot/efi              9A36-7777
/dev/sde1          ntfs      Movie_Drive /run/media/me/Movie_Drive 5F05F2BF0F4C1873
/dev/sda2          ntfs      Data       (not mounted)          A2E4464BE4462241
/dev/sda3          ext4                 (not mounted)          9771400b-7788-420b-819a-441e879fa107
/dev/sda1                               (not mounted)          


```

will list all the mounted and unmounted partitions.
```
mount -t type device destination_dir
```

can be used to mount your device/partition.
Last EDIT: mount them one by one, by using xargs like this:

```
xargs -I{} -n1 udisksctl mount -b {}
```
Example:
```
xargs -I{} -n1 udisksctl mount -b {}
### then add yours like below
/dev/nvme0n1p3
Mounted /dev/nvme0n1p3 at /run/media/me/Windows-SSD

```

---

### Post by Bashing-om on 2022-02-23
Dii_Reno; Hello

Several factors affect the answer.
The simple one if you want that partition always mounted at boot:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/AutomaticallyMountPartitions#Systemwide_Mounts](https://help.ubuntu.com/community/AutomaticallyMountPartitions#Systemwide_Mounts)

If the file system is encrypted - gets a bit more complicated.

else for single use case one can make up a mount point and mount the target directly in terminal; As well, there are GUI tools to effect a mount. 

[INDENT]hope this helps
[/INDENT]

---


---
title: "rsynce drive is 12TB but the drives = 11.5 12TB is almost full."
date: 2020-06-10
forum: Server Platforms
---

### Post by Raymond Day on 2020-06-10
Guess when I run the copy script it my not delete old files I deleted off the drives backing up not sure.

Here is the script I run every day with a cron job:

```
#!/bin/bash
rsync -avP /media/4TB-Blue/ /media/12TB-backup/4TB-Blue 
rsync -avP /media/PiDrive1TB/ /media/12TB-backup/PiDrive1TB
rsync -avP /media/VHS-videos/ /media/12TB-backup/VHS-videos
rsync -avP /media/WD-MyDrive-2TB/ /media/12TB-backup/WD-MyDrive-2TB
rsync -avP /media/1TB-WD/ /media/12TB-backup/1TB-WD
rsync -avP /media/500GB-Laptop-HDD/ /media/12TB-backup/500GB-Laptop-HDD
```

All them drives want to back up to the 12TB drive. The VHS-Videos one is s 3TB so can add them up 4+1+3+2+1+.5=11.5 but right now it is saying 94% full.

Here is a df -h to show the drives.

```
Filesystem      Size  Used Avail Use% Mounted on
udev             16G     0   16G   0% /dev
tmpfs           3.2G  3.1M  3.2G   1% /run
/dev/sdb2       1.8T  128G  1.6T   8% /
tmpfs            16G  8.0K   16G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs            16G     0   16G   0% /sys/fs/cgroup
/dev/sda1       916G  272G  598G  32% /media/WD-3D-NAND-Stick
/dev/sdb1       511M  6.1M  505M   2% /boot/efi
/dev/sdi1       9.1T  6.0T  2.6T  70% /media/WD-10TB-3
/dev/sdl1       9.1T  6.0T  2.7T  69% /media/WD-10TB-2
/dev/sde1       9.1T  5.2T  3.5T  60% /media/WD-10TB
/dev/sdf1        11T  9.7T  681G  94% /media/12TB-backup
/dev/sdn1       9.1T  5.3T  3.3T  62% /media/WD-10TB-4
/dev/sdg1       917G  532G  340G  62% /media/PiDrive1TB
/dev/sdm1       916G  867G  2.5G 100% /media/1TB-WD
/dev/sdh1       1.8T   23G  1.7T   2% /media/WD-MyDrive-2TB
/dev/sdk1       2.7T  1.9T  694G  74% /media/3TB_USB
/dev/sdd1       3.6T  2.8T  670G  81% /media/4TB-Blue
/dev/sdc1       2.7T  2.1T  513G  81% /media/VHS-videos
/dev/sdj1       458G  5.2G  429G   2% /media/500GB-3D-NAND
tmpfs           3.2G     0  3.2G   0% /run/user/0
```

Can see they are not all 100% the /media/1TB-WD is full but I am not going to store any more on it.

Maybe I have to tell the **rsync** command some how to delete the files that have been deleted from the source drives? I am not sure. Hope some one can help I don't want to get a 14TB drive just to backup them up when they don't add up over 12TB.

The two 3TB drive I have backing up to other 3TB drives. With 2 commands every day like this:

```
rsync -avP /media/WD-10TB-2/ /media/WD-10TB-3
rsync -avP /media/WD-10TB/ /media/WD-10TB-4
```

source 69% destanashion 70%
source 60% destanashion 62%

They don't = the same all so but not close to full any way.

Should be the same % used but they don't. I guess have to do the rsync command another way?

-Raymond Day

---

### Post by vanadium on 2020-06-10
Use the --delete option to delete files in the destination that do not anymore exist in the source. The data in "human" format may introduce rounding. The space effectively occupied  (i.e. per whole sector) is provided by the "du" command. By default, ext4 formatted devices have 5% space reserved for root. You may recover some gigabytes by reducing that space.

---

### Post by Raymond Day on 2020-06-14
Thank you. I changed it like this:

```
#!/bin/bash
rsync -avP --delete /media/4TB-Blue/ /media/12TB-backup/4TB-Blue 
rsync -avP --delete /media/PiDrive1TB/ /media/12TB-backup/PiDrive1TB
rsync -avP --delete /media/VHS-videos/ /media/12TB-backup/VHS-videos
rsync -avP --delete /media/WD-MyDrive-2TB/ /media/12TB-backup/WD-MyDrive-2TB
rsync -avP --delete /media/1TB-WD/ /media/12TB-backup/1TB-WD
rsync -avP --delete /media/500GB-Laptop-HDD/ /media/12TB-backup/500GB-Laptop-HDD
```

Before it ran the 12TB said it was **94%** full and after it ran says **62%** full. That matches up good to the source drives.

-Raymond Day

---

### Post by Skaperen on 2020-06-14
i always include the -*H* (*--hard-links*) option.  if a regular file has a hard link for any reason, *rsync -H* preserves that hard link.  i also use -*S* (*--sparse*) to minimize storage of binary files with huge runs of zeros.

---


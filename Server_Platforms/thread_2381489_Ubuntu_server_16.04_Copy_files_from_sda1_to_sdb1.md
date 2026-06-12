---
title: "Ubuntu server 16.04 Copy files from sda1 to sdb1"
date: 2018-01-01
forum: Server Platforms
---

### Post by patdundee on 2018-01-01
Hi Guys
after a filed upgrade from 12.04 to 14.04 I have installed 16.04

I have 2 hard drives in use 

16.04 is on sdb1 and 14.04 is on sda1 however i need to copy files, folders & permissions from sda1 over to sdb1

sdb1 is the boot disk

Here is my topology using lsblk I have starred out the partition names

```

NAME                       MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                          8:0    0 465.8G  0 disk
ââsda1                       8:1    0   243M  0 part
ââsda2                       8:2    0     1K  0 part
ââsda5                       8:5    0 465.5G  0 part
  ââ******--vg-root       252:2    0 449.5G  0 lvm
  ââ******--vg-swap_1     252:3    0    16G  0 lvm  [SWAP]
sdb                          8:16   0 465.8G  0 disk
ââsdb1                       8:17   0   487M  0 part /boot
ââsdb2                       8:18   0     1K  0 part
ââsdb5                       8:21   0 465.3G  0 part
  ââ******--vg-root   252:0    0 449.3G  0 lvm  /
  ââ******--vg-swap_1 252:1    0    16G  0 lvm  [SWAP]
sr0                         11:0    1  1024M  0 rom

```

Both versions (14.04 and 16.04) are in my Grub file at startup so i assume both drives are mounted

Any help greatly appreciated
Many thanks
P

---

### Post by howefield on 2018-01-01
Thread moved to the "*Server Platforms*" forum.

---

### Post by ghanson59 on 2018-01-01
Use the CP command to copy each sub-directory you want to send to sdb
Assume the following directory tree:
/sda1 is mounted as sourceHDD
   home/user1
   home/user2
   etc/ssh

/sdb1 is mounted as targetHDD

Use the copy command:
```
sudo cp -a /home targetHDD/homeCopy      # copies everything over including file and sub-directory attributes
sudo cp -a /etc/ssh targetHDD/etc/sshBackup         # copies your ssh files over to a backup sub-dir on the target. You want to be careful about overwriting system files!
```

You could also employ RSYNC using the --progress switch for a progress display:
```
 sudo rsync -ah --progress <source> <target>
```

---

### Post by darkod on 2018-01-01
I see you have LVM on both the old and the new disk. But because you didn't paste the full info we can't see exactly the VG names. One problem might be if you named the new VG the same as the old one. Because to copy data you need to mount both old and new LVs at the same time. And if the VG and LV names are identical, I'm not sure you can mount them at the same time.

Can you post the output of:
```
sudo pvdisplay
sudo vgdisplay
```

---

### Post by patdundee on 2018-01-01
i can confirm that both vg and pg do show different names
The new install of 16.04 was put on sdb with different names for vg and the old system is on sda
On boot up i can choose either 14.04 or 16.04 so i presume thay are both mounted when i select 16.04

```

NAME                       MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                          8:0    0 465.8G  0 disk
ââsda1                       8:1    0   243M  0 part
ââsda2                       8:2    0     1K  0 part
ââsda5                       8:5    0 465.5G  0 part
  ââname1--vg-root       252:2    0 449.5G  0 lvm
  ââname1--vg-swap_1     252:3    0    16G  0 lvm  [SWAP]
sdb                          8:16   0 465.8G  0 disk
ââsdb1                       8:17   0   487M  0 part /boot
ââsdb2                       8:18   0     1K  0 part
ââsdb5                       8:21   0 465.3G  0 part
  ââname2--vg-root   252:0    0 449.3G  0 lvm  /
  ââname2--vg-swap_1 252:1    0    16G  0 lvm  [SWAP]
sr0                         11:0    1  1024M  0 rom

```

The live drive us sdb I need everything from the /home on sda to go to home on sdb
cp and rsync to not seem to be able to see the path for these. I must be typing it wrong

What would the correct path be to rsync (source **sda**) /home/foldername/* to destination **sdb /home/foldername**

---

### Post by ghanson59 on 2018-01-01
Run the following command:
```
df -Th
```

You'll see "Filesystem" and "Mounted on" column headings. Look for the mount points, "/" will be your boot drive and probably shows /dev/sdb1 as the Filesystem. Look for mounted volumes on /dev/sda1.

You can also run:
```
sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
```

This will list a graphical tree and you should see sda with sda1 under it and sdb with sdb1 under it. Look under label for your names. On my system I have something like the following
```
NAME   FSTYPE       SIZE MOUNTPOINT LABEL
sda               931.5G
&#9500;&#9472;sda1 vfat         512M /boot/efi
&#9500;&#9472;sda2 ext4       923.8G /
&#9492;&#9472;sda3 swap         7.2G [SWAP]
sdb                 1.8T
&#9500;&#9472;sdb1 zfs_member   1.8T            his-pool
&#9492;&#9472;sdb9                8M
sdc                 1.8T
&#9500;&#9472;sdc1 zfs_member   1.8T            his-pool
&#9492;&#9472;sdc9                8M
```

Thus, sda2 is the root of my boot drive, so my /home/userName sub-dir is on sda2; this would be sdb1 on your system. I have a zfs pool running across sdb and sdc which is similar to your sda1. But you can't copy to sda1, you need to copy to its mount point. On my system, to copy from the his-pool (your sda1) to / (your sdb1) I would use:
```
cp -a /his-pool/home/foldername /home/foldername
```

You reference the physical drives (sda, sdb, etc.) by their mountpoints. In my example, "/" and "his-pool". Use df or lsblk to determine those mountpoint names.

---

### Post by patdundee on 2018-01-02
Hi Guys
Thanks for help, I have worked around it. It was easier to add a flash drive and mount it. Then rsync files to the flash drive from sda and then move from the flash drive to sdb
Much easier :)
Many thanks
P

---


---
title: "Tyring to install a 4TB hdd, problems."
date: 2020-01-19
forum: Server Platforms
---

### Post by Higgins909 on 2020-01-19
Ok, I have installed HDDs before on ubuntu server.  The biggest I've ever installed were 2 TB.  I'm now trying to install a 4TB hdd that I was using on a windows computer, so it had its FS on it.  I normally use fdisk, but it seems GPT is new and risky or something.  I also use blkid for the UUID in /etc/fstab.  So I decided to use parted after reading around a bit.  I followed ubuntu's "InstallingANewHardDrive" guide.  Say my drive name is /dev/sda , even after formatting it, /dev/sda1 does not exist.  fdisk -l just shows a # 1 partiton.  It's also listed as a Microsoft Basic "Type" ... It's supposed to be ext4.  When I blkid /dev/sda1 I get a UUID, TYPE, PARTLABLE, PARTUUID.  I put the UUID in my /etc/fstab like I normally do and got an error. (Code)  Maybe it's because I did /dev/sda1 and not /dev/sda ?
```

[root@localhost admin-ben]# nano /etc/fstab
[root@localhost admin-ben]# mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.
[root@localhost admin-ben]#


```
Where did I go wrong?

Thanks,
    Higgins909

---

### Post by TheFu on 2020-01-19
Please SHOW the config, don't try to interpret it.  Show the command, all options and relevant output if it is long or all the output if it isn't too long.

---

### Post by SeijiSensei on 2020-01-19
Open the drive with "sudo fdisk /dev/sdb" (my guess is it will be sdb). Use the "d" command repeatedly to delete any existing partitions. Write the results to the drive with the "w" command. Exit fdisk, then open the drive with it again. Use "n" "p" to create a new primary partition, then have it span the entire drive. Write the results to the drive again with "w" and exit fdisk. At the command prompt run "sudo mkfs -t ext4 /dev/sdb1". You should now have an empty ext4 filesystem on the drive that you can mount.

---

### Post by TheFu on 2020-01-19
> **SeijiSensei said:**
> Open the drive with "sudo fdisk /dev/sdb" (my guess is it will be sdb). Use the "d" command repeatedly to delete any existing partitions. Write the results to the drive with the "w" command. Exit fdisk, then open the drive with it again. Use "n" "p" to create a new primary partition, then have it span the entire drive. Write the results to the drive again with "w" and exit fdisk. At the command prompt run "sudo mkfs -t ext4 /dev/sdb1". You should now have an empty ext4 filesystem on the drive that you can mount.

fdisk can certainly be used and mkfs too.
However, gparted is much easier, provided you know the steps, which are the same as described above, just with a point-n-click GUI.

However, running a GUI with sudo needs an extra option to ensure the config file it creates without asking doesn't end up in a normal userid's HOME.
```
 sudo -H gparted
```
Then I'd 
[LIST=1]
[*]select the correct disk from the pull-down in the upper right corner
[*]create a new GPT partition table
[*]create at least 1 new primary partition
[*]right click on that new partition, select format .... ext4
[*]apply
[/LIST]
Should take just a few seconds.

If you want more flexibility and it is taking more than a minute to format with ext4, you could insert some steps to use LVM.  With LVM, the format for ext4 will be seconds - like under 5 sec total.  I did this just a few weeks ago on an 8TB disk.  However, LVM does bring some added complexity for the added capabilities, so be certain you want LVM.

---

### Post by oldfred on 2020-01-19
If using an old copy of fdisk, it is not gpt aware and may make MBR partitions which will limit drive to 2TiB.
 Before you needed to use parted, gparted, or gdisk for gpt.
I used gparted back in 2010 to make gpt partitioned drives and have used gdisk.

---

### Post by TheFu on 2020-01-20
**fdisk** has been GPT aware for a few LTS releases.  Basically, gpt thru fdisk isn't an issue on any release any home user should have installed anymore.

For some reason, I prefer the fdisk interface over parted. Probably just comfort with the commands.  But parted has some new build-in capabilities which can be very handy which fdisk doesn't have.

---

### Post by Higgins909 on 2020-01-21
I set this machine up so long ago and every once in a blue moon, I do something with the HDD's.  It used to have like 40, 80, and 200GB drives.  So it turns out that I misspelled defaults in the fstab and then possibly didn't run "**mkfs -t ext4 /dev/sda1**"  These are the errors it gave in **dmesg**.  After the bad geometry error, I did the **mkfs** code and then **mount -a** again.
```

[ 1341.372887] EXT4-fs (sda1): Unrecognized mount option "defautls" or missing value
[ 2768.384715] EXT4-fs (sda1): Unrecognized mount option "defautls" or missing value
[ 2834.139898] EXT4-fs (sda1): bad geometry: block count 976754385 exceeds size of device (976754176 blocks)
[root@localhost admin-ben]#

```

I followed the parts about using **parted** and** mkfs** in this guide [HTML]https://help.ubuntu.com/community/InstallingANewHardDrive[/HTML]  I decided to go with **parted** after **fdisk -l** showed a warning about GPT being new.

```

[admin-ben@localhost ~]$ df -h
Filesystem           Size  Used Avail Use% Mounted on
/dev/mapper/cl-root   50G  1.5G   49G   3% /
devtmpfs             1.9G     0  1.9G   0% /dev
tmpfs                1.9G     0  1.9G   0% /dev/shm
tmpfs                1.9G  8.6M  1.9G   1% /run
tmpfs                1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/sdd1            1.8T  1.5T  302G  83% /srv/two
/dev/sdc1            1.8T  1.7T  4.3G 100% /srv/three
/dev/sda1            3.6T   89M  3.4T   1% /srv/one
/dev/sdb1           1014M  179M  836M  18% /boot
/dev/mapper/cl-home   65G  5.7G   59G   9% /home
tmpfs                379M     0  379M   0% /run/user/1000
[admin-ben@localhost ~]$

```
I originally went to **parted** because **fdisk -l** showed the same strange to me partition list for **sda**
```

[root@localhost admin-ben]# fdisk -l

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes, 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk label type: dos
Disk identifier: 0xc80cacd6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  3907029167  1953513560   83  Linux

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes, 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk label type: dos
Disk identifier: 0x4ec04b4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048  3907029167  1953513560   83  Linux
WARNING: fdisk GPT support is currently new, and therefore in an experimental phase. Use at your own discretion.

Disk /dev/sda: 4000.8 GB, 4000787030016 bytes, 7814037168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk label type: gpt
Disk identifier: 743A22DC-6234-47B4-8647-8B465ABFC431


#         Start          End    Size  Type            Name
 1         2048   7814035455    3.7T  Microsoft basic primary

Disk /dev/sdb: 128.0 GB, 128035676160 bytes, 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk label type: dos
Disk identifier: 0x0000abc8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048     2099199     1048576   83  Linux
/dev/sdb2         2099200   250068991   123984896   8e  Linux LVM

Disk /dev/mapper/cl-root: 53.7 GB, 53687091200 bytes, 104857600 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/cl-swap: 4160 MB, 4160749568 bytes, 8126464 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/cl-home: 69.1 GB, 69105352704 bytes, 134971392 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

[root@localhost admin-ben]#

```
 /srv/four is supposed to be the new srv/one, but I temporarily changed it to four.
```

#
# /etc/fstab
# Created by anaconda on Fri Aug 31 22:43:34 2018
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
/dev/mapper/cl-root     /                       xfs     defaults        0 0
UUID=47d708f6-0e28-42c0-afa9-147c4c998608 /boot                   xfs     defaults        0 0
/dev/mapper/cl-home     /home                   xfs     defaults        0 0
/dev/mapper/cl-swap     swap                    swap    defaults        0 0
#UUID=ccad8e15-6954-4365-9910-5d0105b12eb4 /srv/one                ext4    defaults        0 0
UUID=2d5311c9-720a-40c7-8eb7-c2f275e39c0e /srv/two                ext4    defaults        0 0
UUID=54818926-5dd7-4265-abaf-1fd99e26effd /srv/three              ext4    defaults        0 0
UUID=4e04535b-4077-4a0b-a66d-53f676c8a50b /srv/four                ext4    defaults        0 0

```

```

[root@localhost admin-ben]# blkid
/dev/sdc1: UUID="54818926-5dd7-4265-abaf-1fd99e26effd" TYPE="ext4"
/dev/sdd1: UUID="2d5311c9-720a-40c7-8eb7-c2f275e39c0e" TYPE="ext4"
/dev/sda1: UUID="4e04535b-4077-4a0b-a66d-53f676c8a50b" TYPE="ext4" PARTLABEL="primary" PARTUUID="8460ab20-63e8-4c10-a575-b49fafbe8e94"
/dev/sdb1: UUID="47d708f6-0e28-42c0-afa9-147c4c998608" TYPE="xfs"
/dev/sdb2: UUID="4l1Yez-nLgQ-5gCw-hOlw-h0o0-9WCd-MNXho2" TYPE="LVM2_member"
/dev/mapper/cl-root: UUID="c4a54ebe-b90c-44ed-a82b-ed367e441e6a" TYPE="xfs"
/dev/mapper/cl-swap: UUID="177ae4c4-6914-4adf-b9c0-c44e234cc123" TYPE="swap"
/dev/mapper/cl-home: UUID="0d5ba4f4-6492-455e-8c62-2bdb368a869e" TYPE="xfs"
[root@localhost admin-ben]#

```
I'm going to combine my Samba thread into this one...  Not sure why I didn't in the first place.  I think they're fairly related.  I can connect to my other drives or shares, just not the new one.  I made a folder in CLI when it was **/srv/one** and then when I switched it to **/srv/four** it was still there.  I don't know if this issues is related to the formatting of the hdd.  I'm pretty sure my Samba config is poorly setup, but it works...

```

  GNU nano 2.3.1                             File: /etc/samba/smb.conf

# See smb.conf.example for a more detailed config file or
# read the smb.conf manpage.
# Run 'testparm' to verify the config is correct after
# you modified it.
#
[global]
        workgroup = WORKGROUP
        security = user
        passdb backend = tdbsam
        printing = cups
        printcap name = cups
        load printers = yes
        cups options = raw

#[homes]
#       comment = Home Directories
#       valid users = %S, %D%w%S
#       browseable = No
#       read only = No
#       inherit acls = Yes
#
#[printers]
#       comment = All Printers
#       path = /var/tmp
#       printable = Yes
#       create mask = 0600
#       browseable = No
#
#[print$]
#       comment = Printer Drivers
#       path = /var/lib/samba/drivers
#       write list = @printadmin root
#       force group = @printadmin
#       create mask = 0664
#       directory mask = 0775

[Drive SSD]
        comment = Drive SSD Comment
        path =  /home/admin-ben
        guest ok = no
        writable = yes
        browsable = yes
        create mask = 0775

[Drive One]
        comment = Drive One Comment
        path =  /srv/one
        guest ok = no
        writable = yes
        browsable = yes
        create mask = 0775

[Drive Two]
        comment = Drive Two Comment
        path =  /srv/two
        guest ok = no
        writable = yes
        browsable = yes
        create mask = 0775

[Drive Three]
        comment = Drive Three Comment
        path =  /srv/three
        guest ok = no
        writable = yes
        browsable = yes
        create mask = 0775


[Drive Four]
        comment = Drive Three Comment
        path =  /srv/four
        guest ok = no
        writable = yes
        browsable = yes
        create mask = 0775

```
mounting points, what is the 4 4 6 6?  **two** and **three** still work.
```

[root@localhost admin-ben]# ls -l /srv/
total 24
drwxr-xr-x. 4 admin-ben admin-ben  4096 Jan 19 17:30 four
drwxr-xr-x. 4 admin-ben admin-ben  4096 Jan 19 17:30 one
drwxr-xr-x. 6 admin-ben admin-ben  4096 Jan 18 16:53 three
drwxr-xr-x. 6 admin-ben admin-ben 12288 Jan 20 17:18 two
[root@localhost admin-ben]#

```

...Hope I didn't forget anything.

---

### Post by TheFu on 2020-01-21
Samba has nothing to do with mounting a disk.  Completely different expertise is needed and client-side knowledge is mandatory.

How old is the OS you are using, exactly?  12.04?  older?

If you did my gparted steps, that would all have been solved. The partitions would have been aligned, and performance wouldn't be bad.
/dev/sda is a 4TB disk and still has NTFS/FAT32 format.  That's a huge issue if you want Linux to use for anything except non-secured data.

---


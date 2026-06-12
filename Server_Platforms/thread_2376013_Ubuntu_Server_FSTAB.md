---
title: "Ubuntu Server FSTAB"
date: 2017-10-29
forum: Server Platforms
---

### Post by johnwesley on 2017-10-29
Hi team
Hope everyone is great.

I am using an orange pi one with ubuntu 16.04 server edition.
I wanted to give next cloud a try.  (I am petty sure I have have my external hard drive permanently mounted prior to installing next clound

I have an old harddisk I was able to mount it from the command line via ssh.

But when I edited the fstab it hung and I had to go into maintenance mode and put the # before my entry.
I did make the folder in /media

below is the Fstab file:
UID=d62953c7-6b7f-499b-bb6f-87a0f9374d34 / ext4 defaults,noatime,nodiratime,com$
tmpfs /tmp tmpfs defaults,nosuid 0 0
/var/swap none swap sw 0 0

#/dev/sda1   /media/media/exusbhd   ext2   user,fmask=0111,dmask=0000   0   0


fdisk -l does this
jwp1@orangepione:~$ sudo fdisk -l
[sudo] password for jwp1:
Disk /dev/mmcblk0: 14.9 GiB, 15931539456 bytes, 31116288 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x6aedbc6b

Device         Boot Start      End  Sectors  Size Id Type
/dev/mmcblk0p1       8192 30805119 30796928 14.7G 83 Linux


Disk /dev/sda: 149.1 GiB, 160041885696 bytes, 312581808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000ca773

Device     Boot Start       End   Sectors   Size Id Type
/dev/sda1        2048 312580095 312578048 149.1G 83 Linux

and df -T shows this after I mount it

jwp1@orangepione:/media$ df -T
Filesystem     Type     1K-blocks    Used Available Use% Mounted on
udev           devtmpfs    168784       0    168784   0% /dev
tmpfs          tmpfs        50680    1152     49528   3% /run
/dev/mmcblk0p1 ext4      15175128 1423284  13584696  10% /
tmpfs          tmpfs       253384       0    253384   0% /dev/shm
tmpfs          tmpfs         5120       4      5116   1% /run/lock
tmpfs          tmpfs       253384       0    253384   0% /sys/fs/cgroup
tmpfs          tmpfs       253384       0    253384   0% /tmp
tmpfs          tmpfs        50680       0     50680   0% /run/user/1000
/dev/sda1      ext2     153835556   60868 145960240   1% /media/exusbhd

Thanks

---

### Post by darkod on 2017-10-29
What is the mount point, is it /media/media/exusbhd or /media/exusbhd? There is big difference between those two paths. You have to use the correct one in fstab.

---

### Post by Morbius1 on 2017-10-30
In addition:
>  #/dev/sda1   /media/media/exusbhd   ext2   user,[COLOR=#0000cd]**fmask=0111,dmask=0000**[/COLOR]   0   0
fmask and dmask are for setting file and directory permissions on an ntfs or fat32 partition. They have no meaning for ext2. NTFS permissions are set at mount time and ext2 permissions are set after it's mounted with a chmod for example.

---

### Post by johnwesley on 2017-11-01
Hi I used an example from the web I found.  I guess it was windows.  Some time ago I made the drive an ext2.
Thank you the example worked you gave.

UUID=d62953c7-6b7f-499b-bb6f-87a0f9374d34 / ext4 defaults,noatime,nodiratime,commit=600,errors=remount-ro 0 1
tmpfs /tmp tmpfs defaults,nosuid 0 0
/var/swap none swap sw 0 0

/dev/sda1   /media/exusbhd   ext2     defaults 0 0
# /dev/sda1        2048 312580095 312578048 149.1G 83 Linux

---


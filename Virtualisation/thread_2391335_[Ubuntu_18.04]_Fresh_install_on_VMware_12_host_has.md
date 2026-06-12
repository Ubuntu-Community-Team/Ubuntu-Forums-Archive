---
title: "[Ubuntu 18.04] Fresh install on VMware 12 host has timeout during boot"
date: 2018-05-08
forum: Virtualisation
---

### Post by masta-killa on 2018-05-08
Hi all,

I've recently downloaded Ubuntu 18.04 and tried to install it on VMware 12.5.7 (my CPU is not supported by VMware 14.x) running on a Win10 host.
During the installation, the only thing non-default is that I've chosen LVM (as I've more experience with LVM from work and I like how it works).

After the OS installation completed, the only thing I've done is install open-vm-tools (as recommended by Canonical) and not VMware Tools.

As you see, I haven't done much yet ;) so it should be quite reproducible :)

When I boot my VM there is 34 second timeout happening before "Gave up waiting for suspend/resume device".
[IMG]https://preview.ibb.co/etX9M7/ubuntu_18.jpg[/IMG]

After going down the rabbit hole, I managed to get a "set -x" and some echos just before the timeout, with the following result:
[IMG]https://preview.ibb.co/hMMVZS/set_x.jpg[/IMG]
This was done by editing:
/usr/share/initramfs-tools/scripts/local-premount/resume
which calls a function local_device_setup() in:
/usr/share/initramfs-tools/scripts/local
followed by running
```
update-initramfs -u
```

It seems like my swap is causing the issue
```
root@UbuntuVM:~# blkid
/dev/sda1: UUID="o2JaE4-1g3P-irfJ-9wAK-2fgt-no8P-8OnuRZ" TYPE="LVM2_member" PARTUUID="3063a1a1-01"
/dev/mapper/ubuntu--vg-root: UUID="121d8985-139d-4027-9716-3434e3e592ba" TYPE="ext4"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/mapper/ubuntu--vg-swap_1: UUID="2c893b15-9a8a-491e-8493-4504aa63e602" TYPE="swap"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"

root@UbuntuVM:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
UUID="121d8985-139d-4027-9716-3434e3e592ba" /               ext4    errors=remount-ro 0       1
UUID="2c893b15-9a8a-491e-8493-4504aa63e602" none            swap    sw              0       0

root@UbuntuVM:~# lsblk
NAME                  MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
loop0                   7:0    0 86,6M  1 loop /snap/core/4486
loop1                   7:1    0 12,2M  1 loop /snap/gnome-characters/69
loop2                   7:2    0  4,9M  1 loop /snap/canonical-livepatch/39
loop3                   7:3    0 45,6M  1 loop /snap/notepad-plus-plus/34
loop4                   7:4    0  1,6M  1 loop /snap/gnome-calculator/154
loop5                   7:5    0   21M  1 loop /snap/gnome-logs/25
loop6                   7:6    0  3,3M  1 loop /snap/gnome-system-monitor/36
loop7                   7:7    0  140M  1 loop /snap/gnome-3-26-1604/59
loop8                   7:8    0  3,7M  1 loop /snap/gnome-system-monitor/39
loop9                   7:9    0  2,3M  1 loop /snap/gnome-calculator/167
loop10                  7:10   0 21,6M  1 loop /snap/gnome-logs/31
loop11                  7:11   0 46,6M  1 loop /snap/notepad-plus-plus/37
loop12                  7:12   0   13M  1 loop /snap/gnome-characters/86
loop13                  7:13   0  140M  1 loop /snap/gnome-3-26-1604/62
sda                     8:0    0   30G  0 disk 
&#9492;&#9472;sda1                  8:1    0   30G  0 part 
  &#9500;&#9472;ubuntu--vg-root   253:0    0   29G  0 lvm  /
  &#9492;&#9472;ubuntu--vg-swap_1 253:1    0  976M  0 lvm  [SWAP]
sr0                    11:0    1 1024M  0 rom  

root@UbuntuVM:~# cat /proc/swaps
Filename                Type        Size    Used    Priority
/dev/dm-1                               partition    999420    1036    -2

root@UbuntuVM:~# swapon
NAME      TYPE      SIZE USED PRIO
/dev/dm-1 partition 976M   1M   -2
```

I already tried inserting UUIDs in /etc/fstab, but this did not help.
Even commenting out the swap in /etc/fstab (as a test) didn't help.

Can someone instruct me what else I can try?

Thanks!

---

### Post by masta-killa on 2018-05-10
Anyone?

Can I provide more info somehow? Should I report this as a bug?

---

### Post by masta-killa on 2018-05-16
Is this the wrong place to ask questions like this? Any suggestion on where I might get an answer on this question?

---

### Post by howefield on 2018-05-16
Thread moved to the "*Virtualisation*" forum, possibly a more appropriate forum.

---

### Post by LHammonds on 2018-05-16
Oh!  I remember reading somewhere that swap partitions should go away and only use swap files.  I'll need to research this and update my install dox if this is the case.  I also use VMware.

From what I remember, v17 was 1st to implement the swap file in such a way that there was no speed difference between using a partition or file...but files are extremely flexible and much less painful to adjust after install.

I use LVM for everything but /boot so I'm not sure if there there is a difference between LVM and non-LVM system regarding which swap method to use.

LHammonds

---

### Post by sp40140 on 2018-05-19
The swap partition to file change was just default install behavior. You can have swap partition if you really want. The install allows for it.

As to original issue, What are the hardware specs of host and allocated resources to guest?
I am assuming your CPU is at least 8-9 years old.

---

### Post by masta-killa on 2018-05-25
The host is:
Intel Core i7 920 @ 3.8Ghz (4 cores / 8 threads)
12GB RAM
Win10x64

The client is:
2 CPUs
2GB RAM
Ubuntu 18.04

Will try to change to a swap file now, but can't really find decent instructions for it when using LVM...

---

### Post by LHammonds on 2018-05-25
> **masta-killa said:**
> can't really find decent instructions for it when using LVM...

The creation of a swap file should be the same regardless if you use LVM  or not.  You just do not want to use on top of a btrfs type of file  system.

You can see what swaps you have available right now by typing the following:

```
swapon --summary
```

If you do not have enough RAM, processes might get swapped out of RAM and you can see this with the following command:
```
free
```

A  good-running server will have enough RAM on a normal basis to not make  use of the existing swap file.  It should only be there to handle  unexpected emergencies.  If you see it making use of the swap, then add  more RAM if possible.

Here are the commands to create a swap file (/mnt/swapfile) that is 2GB in size (assuming you have 2GB free on /mnt):

```

## Allocate space to the file.
fallocate --length 2G /mnt/swapfile2g

## Set root as owner of the file.
chown root:root /mnt/swapfile2g

## Set permissions to root user only.
chmod 600 /mnt/swapfile2g

## Set up a swap area in the file.
mkswap /mnt/swapfile2g

## Enable file for paging and swaping.
swapon /mnt/swapfile2g

## Display  swap  usage  summary  by  device.  You should see the swapfile in the list.
swapon --summary

```

To make this stick the next time you reboot, add it to /etc/fstab

```

/mnt/swapfile2g swap swap defaults 0 0

```

If you want to remove the swap you just added, follow these steps:

```

swapoff /mnt/swapfile2g
rm /mnt/swapfile2g

```
Make sure to remove the entry in /etc/fstab.

LHammonds

---

### Post by masta-killa on 2018-05-25
Ok, I am getting closer now...

First I created a swapfile /swapfile and configured Ubuntu to use that instead:
```
dd if=/dev/zero of=/swapfile bs=1024 count=1024k
mkswap /swapfile
chmod 600 /swapfile
swapon /swapfile
vi /etc/fstab (replaced the swap partition with the swap file)
swapoff /dev/dm-1
lvremove /dev/ubuntu-vg/swap_1
lvextend -l +100%FREE /dev/ubuntu-vg/root
update-initramfs -u

```

However, this still didn't solve my timeout, it was still freezing on the UUID of the removed swap partition, which was hardcoded somewhere.
After some searching, I found it in the /etc/initramfs-tools/conf.d/resume file. This had "RESUME=UUID=<UUID-of-the-removed-swap-partition>". I couldn't find what to put in there when using a swap file instead of a swap partition. I guessed it might be the following: "RESUME=/swapfile", but I'm not sure if this is correct / working...
```
vi /etc/initramfs-tools/conf.d/resume (replaced "RESUME=UUID=<UUID-of-the-removed-swap-partition>" by "RESUME=/swapfile")
update-initramfs -u
```

After this it finally boots without the timeout! I am not sure however that my resume will work if I use enough RAM to start actually using my swapfile.

Next I loaded a snapshot of Ubuntu just after the install (so with the issue and no fixes or verbose changes applied).
There I tried to see if this alone fixed the issue:
```
root@UbuntuVM:~# vi /etc/initramfs-tools/conf.d/resume (removed the UUID completely, didn't replace it with anything)
root@UbuntuVM:~# update-initramfs -u
update-initramfs: Generating /boot/initrd.img-4.15.0-20-generic
I: The initramfs will attempt to resume from /dev/dm-1
I: (UUID=2c893b15-9a8a-491e-8493-4504aa63e602)
I: Set the RESUME variable to override this.
root@UbuntuVM:~#
```
This didn't solve the issue, because when you leave "RESUME=" empty, it still defaults to the UUID swap partition for resuming:

But when doing
```
root@UbuntuVM:~# vi /etc/initramfs-tools/conf.d/resume (removed the UUID completely, didn't replace it with anything)
root@UbuntuVM:~# swapoff /dev/dm-1
root@UbuntuVM:~# update-initramfs -u
update-initramfs: Generating /boot/initrd.img-4.15.0-20-generic
root@UbuntuVM:~# 
```
Then it doesn't default to the swap partition (which is temporary turned off at that point)

and then the timeout is gone!

so....... it really doesn't like my swap partition for resuming it seems... Anyone have an idea why?
Or should I just use the /swapfile? But then what should be in /etc/initramfs-tools/conf.d/resume? Should I leave it empty (perhaps it defaults to the /swapfile then?) or put in "RESUME=/swapfile"? Or perhaps even something else?

---

### Post by ajgreeny on 2018-06-01
If you have not yet solved this problem try the following to get rid of the delay and the "gave up waiting for suspend/resume device" error.

To disable this modify this file:

 /etc/initramfs-tools/conf.d/resume

In this file, edit the line to **RESUME=none** instead of the UUID that was probably there; it will hopefully disable waiting for a resume device.

---


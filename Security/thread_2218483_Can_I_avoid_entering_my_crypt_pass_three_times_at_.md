---
title: "Can I avoid entering my crypt pass three times at boot?"
date: 2014-04-20
forum: Security
---

### Post by Dáire Fagan on 2014-04-20
Hi

Before installing I highlighted (LVM) /dev/mapper/system-ubuntu--home and chose ‘physical volume  for encryption’, entered a password, and checked on ‘overwrite empty  disk space’ before pressing OK. This brings up the timer for another  minute and then returns the following warning (error?):

```

Device in use

No modifications can be made to the LVM VG system, LV ubuntu-home for the following reason:

In use as a physical volume for encrypted volume system-ubuntu--home_crypt.

```

I selected the new entry /dev/mapper/system-ubuntu--home_crypt and  pressed change. From there I chose Ext4 and /home as the mount point.

Same for /dev/mapper/system-ubuntu--root and /dev/mapper/system-ubuntu--root_crypt, same warning afterwards, set to mount on /, formatted, and Ext4.

Same for /dev/mapper/system-swap only /dev/mapper/system-swap_crypt is set to swap area

I encrypted /dev/mapper/system-shared and received the same warning as  above but I did not press ‘change’ on it as I do not need to assign it a  mount point and it is already Ext4.

1) Unfortunately I have to enter my  crypt passphrase 3 times on boot for each of the partitions, and then  again to login. Is there no more efficient way to encrypt? I could have  checked on 'Encrypt my home folder' before installing but should swap  and / not also be encrypted?

2) I am also not able to save any files to the shared data partition I  set up? I am asked for my password and I can access it fine but I can  save any files or create any folders etc.

I read in an old  thread, and it was suggested to me in #ubuntu’s IRC channel, that if I  encrypt just the LVM’s physical volume as all of the logical volumes are  contained within it I should only have to enter my passphrase once at  boot.

What I have tried:

1) I created the  partitions and set up LVM just as in my original post. In the installer I  leave all the /dev/mapper entries alone, instead I highlight /dev/sda6,  click change, select physical volume for encrypton, enter my new  passphrase, check overwrite empty disk space, and click okay. The cursor  turns into the timer for a few seconds before the following error  appears:

Configuration of encrypted volumes failed.

An error occurred while configuring encrypted volumes

The configuration has been aborted

Even so sda6 was  still marked crypto so I assigned the boot partiion, and then / and home  to the logical volumes and installed. Ubuntu boots but it first outputs  the following:
```

error: diskfilter writes are not support

```
And after I log in nothing is encrypted.

2) GParted would  not let me deactivate the lvm on sda6 so I rebooted, deactivated it, and  deleted it. This time I just created the physical volume with the  following command:


```
sudo pvcreate /dev/sda6 -ff


```
Next, in the  installer I selected /dev/sda6 as a physical volume for encryption which  created a new volume: /dev/mapper/sda6_crypt

When I try to create the volume group:

```
ubuntu@ubuntu:~$ sudo vgcreate system /dev/sda6

  No physical volume label read from /dev/sda6
  Can't open /dev/sda6 exclusively.  Mounted filesystem?
  Unable to add physical volume '/dev/sda6' to volume group 'system'.

ubuntu@ubuntu:~$ umount /dev/sda6
umount: /dev/sda6 is not mounted (according to mtab)

ubuntu@ubuntu:~$ umount /dev/mapper/sda6_crypt
umount: /dev/mapper/sda6_crypt is not mounted (according to mtab)


```
Unable to create the volume group I stop here.

3) I first try to  delete the lvm partition from my last attempt but GParted gives an  unspecified error while applying the operations. I rebooted and deleted  the crypt-luks partition in GParted.

```
ubuntu@ubuntu:~$ sudo pvcreate /dev/sda6

  Device /dev/sda6 not found (or ignored by filtering).

```
Created sda6 Ext4 from GParted with the remaining space.
```

ubuntu@ubuntu:~$ sudo pvcreate /dev/sda6
  Physical volume "/dev/sda6" successfully created
ubuntu@ubuntu:~$ sudo vgcreate system /dev/sda6
  Volume group "system" successfully created

```
In the installer I select /dev/sda6 as a physical volume for encryption and it creates a new /dev/mapper/sda6_crypt. 

Unfortunately when I try to create any logical volume:

```
ubuntu@ubuntu:~$ sudo lvcreate -L 8.5G -n swap system

  Volume group "system" not found

```

The following is how I have encrypted the /root, /home, and swap  partitions on a disk already containing Windows 8.1 and only require a  single passphrase entry on boot:

Create 500 MiB ext4 sda5 partition that will later be assigned as /boot

```
ubuntu@ubuntu:~$ sudo dd if=/dev/urandom of=/dev/sda6
```

12 hours elapse.

```
dd: writing to ‘/dev/sda6’: No space left on device
660092929+0 records in
660092928+0 records out
337967579136 bytes (338 GB) copied, 39571.4 s, 8.5 MB/s
```

```
ubuntu@ubuntu:~$ modprobe dm-crypt
ubuntu@ubuntu:~$ modprobe aes-x86_64
ubuntu@ubuntu:~$ sudo modprobe sha256
```

When I do this over I will run crptysetup benchmark first to see which aes and sha works best for my system.

```
ubuntu@ubuntu:~$ sudo cryptsetup luksFormat /dev/sda6

WARNING!
========
This will overwrite data on /dev/sda6 irrevocably.

Are you sure? (Type uppercase yes): YES
Enter passphrase:
Verify passphrase:
ubuntu@ubuntu:~$ sudo cryptsetup luksOpen /dev/sda6 enc-pv
Enter passphrase for /dev/sda6:

ubuntu@ubuntu:~$ sudo pvcreate /dev/mapper/enc-pv
  Physical volume "/dev/mapper/enc-pv" successfully created
ubuntu@ubuntu:~$ sudo vgcreate vg /dev/mapper/enc-pv
  Volume group "vg" successfully created
ubuntu@ubuntu:~$ sudo lvcreate -L 8.5G -n swap vg
  Logical volume "swap" created
ubuntu@ubuntu:~$ sudo lvcreate -L 20G -n ubuntu-root vg
  Logical volume "ubuntu-root" created
ubuntu@ubuntu:~$ sudo lvcreate -L 50G -n ubuntu-home vg
  Logical volume "ubuntu-home" created
ubuntu@ubuntu:~$ sudo lvcreate -L 140G -n shared vg
  Logical volume "shared" created

ubuntu@ubuntu:~$ sudo lvdisplay
  --- Logical volume ---
  LV Path                /dev/vg/swap
  LV Name                swap
  VG Name                vg
  LV UUID                EMSdc1-yTSS-FF9W-5vcv-jEwF-OeF7-5oOoEI
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2014-04-23 12:57:17 +0000
  LV Status              available
  # open                 0
  LV Size                8.50 GiB
  Current LE             2176
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1

  --- Logical volume ---
  LV Path                /dev/vg/ubuntu-root
  LV Name                ubuntu-root
  VG Name                vg
  LV UUID                TCPIIE-fGv0-3tz8-XP3R-1c9Z-E18R-XTbcOd
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2014-04-23 12:58:41 +0000
  LV Status              available
  # open                 0
  LV Size                20.00 GiB
  Current LE             5120
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2

  --- Logical volume ---
  LV Path                /dev/vg/shared
  LV Name                shared
  VG Name                vg
  LV UUID                dPHDeT-52zj-7bAx-xjzP-p4yC-kXoo-aw7Eac
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2014-04-23 12:59:50 +0000
  LV Status              available
  # open                 0
  LV Size                140.00 GiB
  Current LE             35840
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:4

  --- Logical volume ---
  LV Path                /dev/vg/ubuntu-home
  LV Name                ubuntu-home
  VG Name                vg
  LV UUID                pWFs3D-MXrh-bMez-68r0-4yPc-zMTo-MGhNF1
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2014-04-23 13:06:11 +0000
  LV Status              available
  # open                 0
  LV Size                50.00 GiB
  Current LE             12800
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:3

ubuntu@ubuntu:~$ sudo vgdisplay | grep -i free
  Free  PE / Size       24641 / 96.25 GiB
```

```
ubuntu@ubuntu:~$ sudo mkfs.ext4 /dev/mapper/vg-shared

mke2fs 1.42.9 (4-Feb-2014)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
9175040 inodes, 36700160 blocks
1835008 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
1120 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
    4096000, 7962624, 11239424, 20480000, 23887872

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done     

```

There was similar output for:

```
ubuntu@ubuntu:~$ sudo mkfs.ext4 /dev/mapper/vg-ubuntu-root
ubuntu@ubuntu:~$ sudo mkfs.ext4 /dev/mapper/vg-ubuntu-home
```

I may have needed to add an extra hyphen, like vg-ubuntu--root

Next I opened the Ubuntu 14.04 installer and selected 'something else'. I  assigned /boot to the 500 MiB partition on sda5 and then /root, /home,  and swap to the logical /dev/mapper/vg volumes. 

After Ubuntu installs, before rebooting from the live USB I entered the following:

```
ubuntu@ubuntu:~$ sudo cryptsetup luksOpen /dev/sda6 enc-pv
Enter passphrase for /dev/sda6:
ubuntu@ubuntu:~$ sudo mount /dev/vg/ubuntu-root /mnt
ubuntu@ubuntu:~$ sudo chroot /mnt mount /proc
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo chroot /mnt mount /boot
ubuntu@ubuntu:~$ sudo echo "enc-pv UUID=`sudo blkid -s UUID -o value /dev/sda6` none luks" | sudo tee -a /mnt/etc/crypttab
enc-pv UUID=ad8b8a32-95ea-4add-abe6-326d151e30fa none luks
ubuntu@ubuntu:~$ sudo chroot /mnt update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.13.0-24-generic
ubuntu@ubuntu:~$ sudo umount /mnt/proc /mnt/dev /mnt/boot /mnt
```

On reboot Ubuntu boots asking for only one entry of the passphrase instead of three, one for each encrypted volume.

==================================================================

The only problem remaining now is that although the  /dev/mapper/vg-shared volume appears like any other partitionin  /media/dusf/, and although I can open it without having to enter the  passphrase again, I cannot create files on it.

I have tried replacing the command 'sudo mount /dev/vg/ubuntu-root /mnt'  with 'sudo mount /dev/vg/shared /mnt' but then when i go onto the next  command 'sudo chroot /mnt mount /proc' it gives me the error 'chroot:  failed to run command ‘mount’: No such file or directory'. 

Can anyone tell me how I should edit the following commands so that  /dev/vg/-shared not only mounts at boot, but I can also write to it?

```
ubuntu@ubuntu:~$ sudo cryptsetup luksOpen /dev/sda6 enc-pv
Enter passphrase for /dev/sda6:
ubuntu@ubuntu:~$ sudo mount /dev/vg/ubuntu-root /mnt
ubuntu@ubuntu:~$ sudo chroot /mnt mount /proc
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo chroot /mnt mount /boot
ubuntu@ubuntu:~$ sudo echo "enc-pv UUID=`sudo blkid -s UUID -o value /dev/sda6` none luks" | sudo tee -a /mnt/etc/crypttab
enc-pv UUID=ad8b8a32-95ea-4add-abe6-326d151e30fa none luks
ubuntu@ubuntu:~$ sudo chroot /mnt update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.13.0-24-generic
ubuntu@ubuntu:~$ sudo umount /mnt/proc /mnt/dev /mnt/boot /mnt
```

---


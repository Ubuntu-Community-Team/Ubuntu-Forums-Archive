---
title: "Install with bcache + LUKS + btrfs fails when I use raid1"
date: 2015-10-08
forum: Server Platforms
---

### Post by ch6574 on 2015-10-08
Hi,

I have a machine with 2 HDD and 1 SSD. I want to use the SSD to cache the HDD (bcache), I also wish to encrypt (LUKS) and then use RAID1 on top of that at the filesystem level (btrfs). It all works fine until I activate RAID1 in the filesystem.

Wondering if I have **(a)** done this correctly, and **(b)** what have I missed!

Thanks.


Without btrfs raid, the storage is as follows:

```
$ lsblk -f
NAME        FSTYPE      LABEL UUID                                 MOUNTPOINT
sda                                                                
&#9500;&#9472;sda1                                                             
&#9500;&#9472;sda2      ext2              df8dcc50-fade-4cd0-ba13-94ccec449832 /boot
&#9492;&#9472;sda3      bcache            42dec1ad-a407-4f6e-8b27-062f718bc768 
  &#9500;&#9472;bcache0 crypto_LUKS       6c540992-3652-4fd8-89aa-d21cb8fbeffe 
  &#9474; &#9492;&#9472;enc0  btrfs       vol1  7e8ce42a-0ed4-49b1-ae73-87d7733b861b /
  &#9492;&#9472;bcache1 crypto_LUKS       e2e82483-f3cc-4b1f-b6b3-e657c0e51dcb 
    &#9492;&#9472;enc1  btrfs       vol2  afa2bbfc-8b4e-484c-aa31-e6aba8415759
sdb                                                                
&#9500;&#9472;sdb1      ext4              eebe5ed0-41f2-4553-a7cc-4891705b94d6 
&#9492;&#9472;sdb2      bcache            45531122-45f4-4d15-8e8a-47aae91309e6 
  &#9492;&#9472;bcache0 crypto_LUKS       6c540992-3652-4fd8-89aa-d21cb8fbeffe 
    &#9492;&#9472;enc0  btrfs       vol1  7e8ce42a-0ed4-49b1-ae73-87d7733b861b /
sdc                                                                
&#9500;&#9472;sdc1      swap              a3ba2bf1-0609-401f-b79a-60ecd2fa56e5 [SWAP]
&#9492;&#9472;sdc2      bcache            85cb5e80-6985-446b-801c-b36bbb3405fa 
  &#9492;&#9472;bcache1 crypto_LUKS       e2e82483-f3cc-4b1f-b6b3-e657c0e51dcb 
    &#9492;&#9472;enc1  btrfs       vol2  afa2bbfc-8b4e-484c-aa31-e6aba8415759
sr0
```

Where sda is the SSD, and sdb/sdc are the regular disks.

To get here I ran:

```
# I've done a regular Ubuntu 15.10 install to sda2 (/boot) and sdb1 (/).

# 1. Bcache is then enabled on sdb2 and sdc2 with sda3 as cache
$ wipefs -a /dev/sda3 /dev/sdb2 /dev/sdc2
$ make-bcache -C /dev/sda3 -B /dev/sdb2 /dev/sdc2
$ echo writeback > /sys/block/bcache0/bcache/cache_mode
$ echo writeback > /sys/block/bcache1/bcache/cache_mode

# 2. Encrypted the two bcache block devices next
$ cryptsetup luksFormat /dev/bcache0
$ cryptsetup luksFormat /dev/bcache1
$ cryptsetup luksOpen /dev/bcache0 enc0
$ cryptsetup luksOpen /dev/bcache1 enc1
$ cryptsetup luksHeaderBackup /dev/bcache0 --header-backup-file /boot/bcache0.img
$ cryptsetup luksHeaderBackup /dev/bcache1 --header-backup-file /boot/bcache1.img
$ echo "enc0 UUID=$(blkid -o value /dev/bcache0|head -1) none luks" >> /etc/crypttab
$ echo "enc1 UUID=$(blkid -o value /dev/bcache1|head -1) none luks" >> /etc/crypttab

# 3. Next put a filesystem on the encrypted block devices, and mount one of them.
$ mkfs.btrfs -L vol1 /dev/mapper/enc0
$ mkfs.btrfs -L vol2 /dev/mapper/enc1
$ btrfs device scan
$ echo "/dev/mapper/enc0 /mnt/NEW btrfs defaults,compress 0 1" >> /etc/fstab
$ mkdir /mnt/NEW
$ mount /mnt/NEW

# 4. Now I give it a reboot, and I get prompted for the password to unlock the encrypted devices. Everything mounts up as expected, and the following reports everything is enabled.
$ cat /sys/block/bcache0/bcache/state
$ cat /sys/block/bcache1/bcache/state
$ cryptsetup luksDump /dev/bcache0
$ cryptsetup luksDump /dev/bcache1

# 5. I now copy over the existing system onto the encrypted filesystem, chroot into it, and update the machine to use that as root
$ mkdir /mnt/OLD
$ mount /dev/sdb1 /mnt/OLD
$ rsync -a /mnt/OLD/ /mnt/NEW/
$ mount /dev/sda2          /mnt/NEW/boot
$ mount -o bind /dev       /mnt/NEW/dev
$ mount -t proc none       /mnt/NEW/proc
$ mount -t sysfs none      /mnt/NEW/sys
$ chroot /mnt/NEW

# I then edit /etc/fstab to have
   /dev/mapper/enc0 / btrfs defaults,compress 0 1

#And for /etc/default/grub
  GRUB_CMDLINE_LINUX="root=/dev/mapper/enc0"

#Then update everything
$ grub-mkconfig
$ update-grub
$ update-initramfs -u -k all
$ exit
$ shutdown -r now
```

And the machine prompts for password to unlock the encrypted device, then boots. So far so good.

Now the final part. I bring in the remaining encrypted device for RAID1 at the filesystem level.

```
$ btrfs device add -f /dev/mapper/enc1 /
$ btrfs filesystem balance start -dconvert=raid1 -mconvert=raid1 /
$ btrfs filesystem show
Label: 'vol1'  uuid: 7e8ce42a-0ed4-49b1-ae73-87d7733b861b
	Total devices 2 FS bytes used 1.83GiB
	devid    1 size 24.18GiB used 2.28GiB path /dev/mapper/enc0
	devid    2 size 24.18GiB used 2.28GiB path /dev/mapper/enc1

```

However now when I reboot, I get prompted for the LUKS password and then dropped at an initramfs prompt. :frown:

Querying at the prompt shows that /dev/mapper/enc1 is not available. I can however manually open it, and at that point the btrfs mount is complete and available.

I think I'm missing something in one of the following 3 places:

[LIST=1]
[*]/etc/default/grub
[*]/etc/fstab
[*]/etc/crypttab
[/LIST]

Any thoughts?

N.B. Encrypted swap is next, finishing off with the deletion of the initial install on sdb1.

---

### Post by darkod on 2015-10-09
Did you encrypt the partitions first and then trying to mirror them in raid1? Because it usually goes the other way. First you create the raid1 array and then you encrypt that md device.

---

### Post by ch6574 on 2015-10-09
At the block level, I'm putting bcache on the raw disks, then encryption on that, finally a filesystem. Only at the filesystem level I'm introducing raid as that offers more flexibility.

My problem is I cannot get grub to unlock both encrypted devices, and hence mount the root filesystem for booting.

---

### Post by darkod on 2015-10-10
Sorry, I can't help much especially since I have never worked with btrfs. I do raid with mdadm which works in different way because the filesystem goes on top of the md device, it's not created before the array.

You could probably make things work that way, but you start with mdadm in that case.

---

### Post by ch6574 on 2015-10-11
Thanks, I think I'll give up on the btrfs raid, and instead create /dev/md0 on the spinning disks instead.

i.e. build as

```
+-------------------------------------------------+
|                     btrfs..                     |
| +---------------------------------------------+ |
| |           /dev/mapper/enc0 (LUKS)           | |
| | +-----------------------------------------+ | |
| | |          /dev/bcache0 (bcache)          | | |
| | |             +-------------------------+ | | |
| | |             |    /dev/md0 (raid1)     | | | |
| | | +---------+ | +---------+ +---------+ | | | |
| | | |/dev/sda3| | |/dev/sdb2| |/dev/sdc2| | | | |
| | | |   SSD   | | |   HDD   | |   HDD   | | | | |
| | | +---------+ | +---------+ +---------+ | | | |
| | |             +-------------------------+ | | |
| | +-----------------------------------------+ | |
| +---------------------------------------------+ |
+-------------------------------------------------+
```

Instead of what I was trying to do, i.e.

```
+-------------------------------------------------+
|                     btrfs..                     |
| +-------------------+     +-------------------+ |
| | /dev/mapper/enc0  |     |  /dev/mapper/enc1 | |
| | +---------------+ |     | +---------------+ | |
| | | /dev/bcache0  | |     | |  /dev/bcache1 | | |
| | | +---------+ +-+-+-----+-+-+ +---------+ | | |
| | | |/dev/sdb2| |  /dev/sda3  | |/dev/sdc2| | | |
| | | |   HDD   | |     SSD     | |   HDD   | | | |
| | | +---------+ +---+-----+---+ +---------+ | | |
| | +---------------| |     | |---------------+ | |
| +-------------------+     +-------------------+ |
+-------------------------------------------------+
```

---


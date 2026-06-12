---
title: "Add RAID to existing install"
date: 2011-07-25
forum: Server Platforms
---

### Post by Chrus on 2011-07-25
I've got an Ubuntu 8.04 server currently running on 1x 320GB drive. Im planning on adding a second 320GB drive and running RAID1.
 
Is it possibly to convert my current setup over to RAID without having to reinstall ubuntu?

---

### Post by SeaKing on 2011-07-26
No not really, because if you create the raid in the Bios all data will be erased. What might be possible is grabbing an image of the actual installation using dd - command and then use a live cd to format the newly created raid and to copy the image on the raid. You might editing fstab. 
This solution  needs 320gb of available space anywhere (external haddrive or network share).

---

### Post by trundlenut on 2011-07-26
Do you have hardware raid or were you planning to use software raid instead?

---

### Post by disabledaccount on 2011-07-26
> **Chrus said:**
> I've got an Ubuntu 8.10 server currently running  on 1x 320GB drive. Im planning on adding a second 320GB drive and  running RAID1.

Is it possibly to convert my current setup over to RAID without having to reinstall ubuntu?
There are many tricks that can be used, but it depends on partition layout and what bootloader You are using. This is also possible to create partition-based Raid1 (or 10) and provide prtection only for data, not the OS. But again - it depends on Your current setup.


> **SeaKing said:**
> No not really, because if you create the raid in the Bios all data will be erased. Not necessarily - OS can be started from degraded Raid1 (single drive)

---

### Post by Chrus on 2011-07-26
> **SeaKing said:**
> No not really, because if you create the raid in the Bios all data will be erased. What might be possible is grabbing an image of the actual installation using dd - command and then use a live cd to format the newly created raid and to copy the image on the raid. You might editing fstab. 
This solution  needs 320gb of available space anywhere (external haddrive or network share).

Would I be correct in assuming that would not be possible on a software RAID?

> **trundlenut said:**
> Do you have hardware raid or were you planning to use software raid instead?

I should of mentioned it's going to be software RAID. I knew there was something important I was forgetting.


> **tomazzi said:**
> There are many tricks that can be used, but it depends on partition layout and what bootloader You are using.

Theres a 260GB /data partition and / is just short of 60GB (whatever was left). Both are ext3. And the bootloader is grub.

---

### Post by psusi on 2011-07-26
8.10 has been obsolete and unsupported since april 2010; you need to upgrade.  Running an unsupported release means you have not been getting fixes for the security vulnerabilities found.

---

### Post by Chrus on 2011-07-26
> **psusi said:**
> 8.10 has been obsolete and unsupported since april 2010; you need to upgrade.  Running an unsupported release means you have not been getting fixes for the security vulnerabilities found.

Sorry... my mistake. Its 8.04 LTS. Was just having one of those days yesterday.

---

### Post by rubylaser on 2011-07-26
mdadm can support converting from a single disk to a RAID1, although you are going to be running a very old version of mdadm (2.6.3) on Hardy.

---

### Post by Chrus on 2011-07-26
> **rubylaser said:**
> mdadm can support converting from a single disk to a RAID1, although you are going to be running a very old version of mdadm (2.6.3) on Hardy.

That looks like what i need Ruby. I found [this article]("https://wiki.archlinux.org/index.php/Convert_a_single_drive_system_to_RAID") on converting. Seems kinda logical now that i've read that. Create a RAID with one drive, copy the data over, then add the first drive to the RAID.

Thanks everyone for all the suggestions. Ill let you know how it goes.

---

### Post by bakegoodz on 2011-07-26
Use a Desktop disk (Live CD) of your Ubuntu version.
Install mdadm inside Live Enviroment

sudo apt-get update
sudo apt-get install mdadm
sudo modprobe md_mod
sudo modprobe raid1


# Assuming your your root partition is /dev/sda1.

mkdir /media/root
mount /dev/sda1 /media/root

# If you have separate partition for /home or etc mount them at this point.

example: mount /dev/sda2 /media/root/home

sudo mount --bind /dev/ /media/root/dev
chroot /media/root
mount -t proc none /proc
mount -t sysfs none /sys
mount -t devpts none /dev/pts

# Install mdadm in chroot
apt-get update
apt-get install mdadm
mdadm -v --create /dev/md0 --level=raid1 /dev/sda missing
sudo mdadm --assemble --scan
sudo mdadm --add /dev/md0 /dev/sdb
You can watch the process of resyncing the drives with:
watch cat /proc/mdstat

update-grub
update-initramfs -u 
exit
grub-install --root-directory=/media/root/ --no-floppy --recheck /dev/sda

If have have to start over, remember the raid config is special place on each drive called a superblock. It will still be there even if you do a clean reinstall of mdadm, less you wipe the superblock
mdadm --zero-superblock /dev/sda # Destroys the md superblock

---

### Post by Chrus on 2011-07-26
That looks a whole lot easier than what I was planning on doing.

Thanks Bakegoodz

---

### Post by bakegoodz on 2011-07-27
Disclaimer: This hasn't been tested. Backup first

---

### Post by thomasjohansen on 2012-01-13
@chrus

How did the conversion go?

succeed?

---


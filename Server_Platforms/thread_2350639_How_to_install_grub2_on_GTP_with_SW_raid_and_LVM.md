---
title: "How to install grub2 on GTP with SW raid and LVM"
date: 2017-01-26
forum: Server Platforms
---

### Post by s-braendlin on 2017-01-26
Hey guys,
I am currently successfully running ubuntu server 16.04 LTS on a SW RAID1. But as two WD 20EARS died, I have bought 3 new Seagate IronWolfs that from now on should serve as system disks.

**Background**
My new drives require GTP as partitioning scheme, as they are bigger than 2,4 TB. I want to RAID5 them (I know there are better raid levels), and move my current installation on the new raid. But I cannot get my system booted properly.

**Setup**
I want to have LVM on RAID5. Possibly all system partions as logical volume. I want grub2 to be installed on all drives to be safe in case of booting. The drives should be bootable in older computers without EFI.

**Problem**
Grub2 does not boot my "raided" LVM root partition.

**Solution attempts**
I have added a BIOS boot partition (1MB) on all drives. Installed grub2 on all drives. I have also tried to move the boot partition out of LVM on raid directly. There are several guides out there, but somehow I did not understand how the boot procedere would work with GPT, grub2, LVM and RAID5 on EFI and Non-EFI.

Can somebody help? Where to install grub2? What to configure in BIOS/EFI? I use a virtualbox machine to test my testup. I could provide the machine.

---

### Post by oldfred on 2017-01-26
Moving to Server sub-forum where those who know RAID & LVM may be able to help.

Do not know RAID nor LVM.

But with gpt you must have either an ESP - efi system partition (FAT32) for UEFI boot or a bios_grub partition(unformatted) for grub to correctly install.
I believe those would be outside the RAID & LVM, but am not sure. And then UEFI/BIOS must be configured to boot in the same mode you have installed grub.

Ubuntu's default install uses a separate /boot (and ESP if UEFI) outside the LVM, but that is not RAID.
The desktop installer does not fully support RAID, particularly the install of grub.

The type of RAID can make a difference on where grub gets installed. Most install like desktops to drive like /dev/sda, but FakeRAID or BIOS RAID installs to the root of the RAID, like /dev/mapper. But LVM also uses /dev/mapper as Boot-Repair has to ask which it is when it finds a /dev/mapper configuration.

Boot-Repair adds the lvm2 & mdadm drivers. Use Ubuntu's desktop version that matches your server install, not the older Boot-Repair ISO.
But you may have to make sure it correctly mounted all your LVM partitions, so report fully sees system.
 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by tech-j on 2017-01-26
Just out of curiosity, why do you want to LVM a RAID?
You are actually adding overhead and slowing down the system by putting a "Software RAID" on top of a Physical RAID.

Typically you just use your RAID controller to create your RAID-5 Volume (or volumes if you want to slice up the RAID into multiple LUNS, but you are reducing performance again.)
Once you have your RAID-5 Volume, The Ubuntu Installer will detect it as s single disk.
If the size is larger than 2TB, then it will automatically force the GPT Partition table since MSDOS tables cannot "see" greater than 2TB.
During the install, select "Manual" Disk configuration.
Select the Volume and select "Add" Partition.
Typically I create a 1GB /boot partition (To hold all the Kernels and Grub Files) for a non-UEFI boot system, and format that ext2 (Readable by any OS is why I do this.)

Then I create the "Swap" partition.
The rule of thumb for a desktop is 4GB to 8GB for the swap partition. (If your machine has more than 16GB of RAM then you can use 4GB, if it only has 8GB then use 8GB for swap as well.

Then finally create your "/" Partiton and tell it to use the rest of the remaining disk space available and format this for ext4.
(Or you can manually create all the partitions for /etc /var /home /usr and then "/" if you want, but if you just set the last partition to "/" it will put all of the required directories on that mount point.)
This allows you to grow / resize this partition if you add additional disks /storage to the RAID Volume later on.

Save the configuration and "Write Changes to Disk".
Near the end of the installation process it will ask you where you want Grub to be installed.
On a non-UEFI boot system you will point it to the base Volume (Usually /dev/sda if you are following the instructions above.) and you don't have to worry about installing it to ANY of the partitions you created then.
Let the install complete and reboot and start using the machine!
Have fun.
-Tech-J

---

### Post by darkod on 2017-01-26
For gpt disks the bios_grub partition should be outside of the SW raid and outside of the LVM. It should be a simple 1MiB partition (for example at the start of the disks) and with no filesystem (just create the partition, do not format it).

For example parted allows you to easily create partition without formatting them. Just create it, set the bios_grub flag on it, and leave it like that. Grub2 will use it automatically on install. I have LVM over mdadm raid on gpt disks and it works without any issues. But don't forget, the 1MiB partition is simple partition, it doesn't go into the raid or into the LVM.

Also think about using raid1 for the root partition and raid5 for the data partition. I'm not sure the system files can be on raid5 because that splits files and they might not like to be split. You can try in any case.

---

### Post by s-braendlin on 2017-02-10
> **tech-j said:**
> Just out of curiosity, why do you want to LVM a RAID?
You are actually adding overhead and slowing down the system by putting a "Software RAID" on top of a Physical RAID.
Till now I only use mdadm software RAID. In the web, LVM and MDADM is announced as reliable solution. I did not read much about performance problems, except wrong alignment.

> **darkod said:**
> For gpt disks the bios_grub partition should be outside of the SW raid and outside of the LVM. It should be a simple 1MiB partition (for example at the start of the disks) and with no filesystem (just create the partition, do not format it).

For example parted allows you to easily create partition without formatting them. Just create it, set the bios_grub flag on it, and leave it like that. Grub2 will use it automatically on install. I have LVM over mdadm raid on gpt disks and it works without any issues. But don't forget, the 1MiB partition is simple partition, it doesn't go into the raid or into the LVM.
I have excatly done this, including the flag, outside the RAID and therefore also outside LVM. Its a pitty that I cannot use fdisk or lsbsk during setup. Maybe I could attach a screenshot of the partition wizard in Ubuntu server setup. Is it possible to install grub2 on all disks? Such that I could boot with every disk?

> **darkod said:**
> Also think about using raid1 for the root partition and raid5 for the data partition. I'm not sure the system files can be on raid5 because that splits files and they might not like to be split. You can try in any case.
This might be a good point. But the problem during start is not the boot partition, it seems the root on LVM is not mountable. Could this be related to GRUB2?

---

### Post by darkod on 2017-02-10
I thought you have issues installing grub. It's one thing to be able (or not) to install the grub bootloader, and it's different thing whether it will boot the OS or not.

Your issue might actually be the root being on raid5 without separate /boot. If you use separate /boot on raid1, the boot files are there and then it doesn't matter if / is on raid5. You can try that too...

As for boot type, I would use legacy boot, not UEFI. With UEFI you also need the EFI system partition on the disks, not just the small bios_grub.

---

### Post by s-braendlin on 2017-02-11
You were totally right. Changing RAID5 to RAID1 made the trick. Boot was successful. Notice: Grub2 automatically detected the devices on which it needs to be installed...really great! And yes, I agree, the bios_grub partition is the easiest and most flexible way to go.

Thank you very much. I am free now to go on with server migration :)

---


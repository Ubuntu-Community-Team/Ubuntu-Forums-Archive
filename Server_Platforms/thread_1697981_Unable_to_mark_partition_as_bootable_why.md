---
title: "Unable to mark partition as bootable why?"
date: 2011-03-01
forum: Server Platforms
---

### Post by putz3000 on 2011-03-01
I am following the very basic Software RAID instructions associated with 10.04.  I am installing using 64 bit Ubuntu 10.04.1 as well as 10.04.2.  Hardware is an HP ProLiant ML110 G6.  A couple months back I installed on another ML110 G6 using the 10.04.1 install and was able to successfully install a more complicated RAID install.  On that system I ran with three partitions. The swap & boot partition was setup as RAID 1 and the third partition was setup as RAID 5.  This system had four 1 TB drives installed.  That system boots to OS and at this time seems to be just fine.

I am trying a new install on another ML110 G6 but this time using two 2 TB drives under software RAID 1.  Following the very basic instructions I am trying to create two partitions per drive.  The first one as RAID 1 Swap and the second partition is also RAID 1 but should be marked bootable.  This is where I am having problems.  I am not allowed to mark the partition as bootable.  The only way that flag seems to be changeable is if I leave the partition set to ext4.  But once I change it to physical volume for RAID I lose the ability to change the boot flag.  

I have tried both 10.04.2 as well as 10.04.2 install media thinking that was the problem but no go.  The SATA mode setting is set to compatible which is what the working ML110 G6 is set to as well.

I am currently at a loss.  Since the instructions are so simplistic, I am thinking this must be a hardware issue some how.  Does any one have any idea's or suggestions?

Thanks

---

### Post by disabledaccount on 2011-03-02
First of all: which version of ubnuntu You are using? - alternate, server or desktop?
Have you turned on Expert Mode?
What is Your partition table type MBR or GPT?
have you tried to set flags in fdisk/gdisk?

can you show >fdisk -ul /dev/sd[ab] (partition tables of those two HDD's)

Besides, You don't have to use installer for preparing Raid setup - You can use live distro (CD/USB) to do everything. Installer should detect off-line array and allow to set root mount point for md. In Fact this is best approach, as it offers possibility to fully manage all md and filesystem settings *before* installation.

---

### Post by srs5694 on 2011-03-02
Given your symptoms, I strongly suspect you're using a GUID Partition Table (GPT). On GPT, most OSes don't use a "boot flag," and this concept is both pretty obscure and not presented correctly by most libparted-based tools (such as GParted and GNU Parted). Unfortunately, libparted-based tools imperfectly map Master Boot Record (MBR) concepts and terms onto GPT disks. Specifically, when you set the "boot flag" on a GPT partition, it changes its type code to the type code for an EFI System Partition. On both MBR and GPT disks, a RAID partition has a specific partition type code. Thus, you cannot use a libparted-based tool to "set the boot flag" on a RAID partition -- or if you can, it would no longer be marked as a RAID partition. This is the symptom you're seeing, which is what makes me think you've got a GPT disk.

Note also that if the disk is an MBR disk, you can certainly use fdisk to modify its boot flag, as tomazzi suggests. If you use gdisk on a GPT disk, you'll see no exactly equivalent option; however, you can set the "legacy BIOS bootable" attribute, which is the closest concept that GPT supports. AFAIK, this attribute is used by just one boot loader (Syslinux), and I'm not sure if you should even set it on a RAID partition (my guess is you shouldn't do so).

---

### Post by putz3000 on 2011-04-08
How can I turn off the GUID partition table? I have seen nothing that says this is what it is or is not.  I simply purchased these drives, stuck the in the case and powered it up. I see nothing for jumpers and nothing in the Bios...that I am aware of.  Where should I be looking?

---

### Post by putz3000 on 2011-04-08
this is a note to admin's.  I recently opened another post on the same subject ([http://ubuntuforums.org/showthread.php?t=1722471](http://ubuntuforums.org/showthread.php?t=1722471)). I had not realized at the time that I had this one still open.  The problem is the same although there might be info a little different between the two of them.  If you want to cancel this and combine I am fine with that.

Sorry for the second post.  If not I am monitoring both posts for answers and will update both if I ever get it figured out.

---


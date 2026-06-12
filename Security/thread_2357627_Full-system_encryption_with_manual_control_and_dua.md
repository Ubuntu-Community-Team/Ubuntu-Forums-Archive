---
title: "Full-system encryption with manual control and dual-booting"
date: 2017-04-04
forum: Security
---

### Post by Paddy Landau on 2017-04-04
Are you interested in full-system encryption with the following features?

[LIST]
[*]LUKS
[*]LVM
[*]encrypted Boot
[*]manual partitioning
[/LIST]
and optionally any of these features…

[LIST]
[*]dual-booting
[*]encrypted hibernation
[*]hybrid suspend
[*]multi-disk installation
[/LIST]
If so, look at the documentation for [manual full-system encryption]("https://help.ubuntu.com/community/ManualFullSystemEncryption"). I would love to hear feedback from testers.

---

### Post by hmarius on 2017-07-01
I followed your very detailed instructions. Thanks for all your effort on the guide. After completing all the steps, however, I am unable to boot. After POST and selecting my start up device from the device list, I just get a blank screen. The backlight on the monitor is on, but nothing is displayed: no grub, no curser, nothing. I follwed the troubleshooting steps to refresh grub and the script runs without errors, but on reboot again nothing. My hardware is old, so it might be that it's just incompatible. I did try updating bios followed by a complete reinstall and grub refresh, no dice. Any ideas?

-Version-
Kernel        : Linux 4.8.0-36-generic (x86_64)
Distribution        : Ubuntu 16.04.2 LTS
Desktop Environment        : LXDE (Lubuntu)

Hardware:
product: OptiPlex 790
vendor: Dell Inc.
-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A19
description: CPU
          product: Intel(R) Core(TM) i7-2600 CPU @ 3.40GHz

---

### Post by Paddy Landau on 2017-07-01
@hmarius, thanks for your testing, and I'm sorry that you have this problem.

The first thing that comes to mind is your comment, "My hardware is old". So, please check that (1) you are using 64-bit (EDIT: I see that you are using 64-bit), and (2) your computer supports UEFI. The instructions don't work for 32-bit and non-UEFI. (If I didn't make this clear, please let me know and I'll fix it.)

Is this a stand-alone installation, or do you have any other operating systems (e.g. Windows 10) on the machine?

Another possibility is that there is something wrong with the EFI partition, in which case a reinstallation would be needed. Using a Live CD, can you check how full the EFI partition is? There should be at least several Mb free &#8212; I forget exactly how much.

Yet another possibility is that the [fix for Grub]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessFixBrokenPieces#Set_default_Grub") didn't take. You must have [FONT=courier new]GRUB_HIDDEN_TIMEOUT_QUIET=false[/FONT], and regenerate Grub if that wasn't the case. This solves a bug that leads to the blank screen.

Unfortunately, I shan't be at my computer for at least 12 hours, so I can't look at this until then, but any extra information from you would be valuable.

---

### Post by hmarius on 2017-07-01
I am using 64-bit, and the computer does support UEFI; I can boot the live disk I used for install in UEFI. ```
lubuntu@lubuntu:~$ dmesg | grep EFI
``` gives ```
[    0.000000] efi: EFI v2.00 by American Megatrends
```. It is a standalone OS, no need to dual boot. The EFI partition shows free space:
```
 Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       549M   13M  537M   3% 

```

I've gone through a complete reinstall from the live disk 3 or 4 times now. I checked /etc/default/grub and [FONT=courier new]it still has GRUB_HIDDEN_TIMEOUT_QUIET=false and [/FONT]GRUB_HIDDEN_TIMEOUT=0 is commented out. Scratching my head! Thanks for your help.

---

### Post by Paddy Landau on 2017-07-02
> **hmarius said:**
> Scratching my head!
I'm also scratching my head! It appears that you have been thorough.

There are only a few other things that I can think of, unfortunately.

Please boot from a Live CD, open a terminal, and enter this command ([from the instructions]("https://help.ubuntu.com/community/ManualFullSystemEncryption/BasicsEFI#Linux")):
```
[[ -e /sys/firmware/efi ]] && echo EFI || echo BIOS
```
It should respond with EFI. If it instead shows BIOS, you might have installed a non-EFI version. I'm grasping at straws here, though :(

When I tested with Lubuntu, I chose to install the third-party software. I am guessing that you did, too?

Something to test is to do a straight default installation from the Live CD (because you have nothing else on the computer), but select the default option to use the entire disk, and to both encrypt and use LVM. See the attached screenshot for Lubuntu. This uses both LUKS and LVM using Ubuntu's defaults.
[LIST]
[*]If it works, it means that something is wrong with my instructions. It also means that your job is done, except that [FONT=courier new]/boot[/FONT] is unencrypted; if you don't mind that, you can live with it.
[*]If it doesn't work, post back with the error to see if we can make it work.
[/LIST]
I look forward to your response…

---

### Post by hmarius on 2017-07-04
```
lubuntu@lubuntu:~$ [[ -e /sys/firmware/efi ]] && echo EFI || echo BIOS
EFI
```

I'll try the default options for erase/encrypt from the livecd and report back shortly.

EDIT: I did also choose to install third party software.

---

### Post by hmarius on 2017-07-04
Choosing the default installation option to erase and encrypt the disk worked. I get the grub menu on boot and then prompted to enter the decryption password. Everything boots up fine. The only drawback is that the default installer doesn't provide an option to use a different encrypted drive for home and/or swap. My primary partition is a small SSD, which is why I was trying to find a solution to reduce r/w on that drive and move home and swap to other drives.

---

### Post by Paddy Landau on 2017-07-04
> **hmarius said:**
> Choosing the default installation option to erase and encrypt the disk worked. I get the grub menu on boot and then prompted to enter the decryption password. Everything boots up fine.
Thank you. That means that there is something wrong with my instructions. But now, to figure out what! Therein lies my difficulty.

You have tried my instructions three times, so I it is unlikely that you made the same mistake three times.

Can I confirm that, following my instructions, you get the POST, i.e. the hardware boot-up screen, and then absolutely nothing else?

Please let me know your RAM size.

I'm going to run through my instructions again to test, in case I have accidentally edited something incorrectly. This is most frustrating! It doesn't help that I'm not a technical expert.

> **hmarius said:**
> The only drawback is that the default installer doesn't provide an option to use a different encrypted drive for home and/or swap. My primary partition is a small SSD, which is why I was trying to find a solution to reduce r/w on that drive and move home and swap to other drives.
There is yet one more idea that I have. Given that you have one smaller SSD and (I presume) one larger HDD, you can take your working setup and use LUKS and LVM to extend your working area.

Here is what I propose. The links indicate how to go about it, but please take great care about choosing the drives and locations. You can do the following from your regular boot; you don't need a Live CD.

If you follow these instructions, the swap and root will remain on your SSD, while your home will move to your HDD. If that's not what you want, please let me know what you do want, and we can change these instructions accordingly.

**WARNING: I am assuming that you don't have any valuable data yet on your machine; there is the possibility that I've made some fatal mistake in these instructions. Please be careful and check everything as you go along, bearing in mind that I *do* make mistakes.**

[LIST=1]
[*]Use LUKS to encrypt your HDD — that's your data partition. Remember to perform these tasks only on your HDD, because your SSD is already formatted and fully set up.
[LIST]
[*][Set up the data partition]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessPartitionFormatEncrypt#Create_the_data_partition")
[*][Encrypt your data partition]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessPartitionFormatEncrypt#Encrypt_your_data_partition") — you can use a new, different passphrase for this
[*][Unlock your (data) partition]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessPartitionFormatEncrypt#Unlock_your_partition")
[/LIST]

[*]Set up LVM — **for your data partition only**.
[LIST]
[*][Set up the (data) partition for LVM]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessSetUpLVM#Set_up_partitions_for_LVM")
[*][Partition the (data) partition]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessSetUpLVM#Partition_the_partition")
[*][Format the (data) partition]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessSetUpLVM#Format_the_partitions")
[/LIST]

[*]Set up the data partition for automatic decryption when you boot. Remove [FONT=courier new]/mnt/root[/FONT] from all paths where present.
[LIST]
[*][Create a (data) key file]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessFixBrokenPieces#Create_key_files")
[*][Find the (data) UUID]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessFixBrokenPieces#Find_the_system_and_data_UUIDs")
[*][Set up crypttab]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessFixBrokenPieces#Set_crypttab"), but only for your data partition (the system one should be already in order)
[*][Do the extra security]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessFixBrokenPieces#For_extra_security")
[/LIST]

[*]Create a mount point for your data partition (this will be modified later).
[LIST]
[*]Create a new folder in root called testhome:
```
sudo mkdir /testhome
```
[*]Edit fstab, and add the following line to the end (you can increase or reduce whitespace if you wish).
```
/dev/mapper/data-home    /testhome    ext4    defaults    0    2
```
[/LIST]
[/LIST]
Now, reboot your machine and check that the data partition is correctly and automatically decrypted and mounted on [FONT=courier new]/testhome[/FONT]. Once everything is working correctly, continue.

[LIST=1]
[*]Edit /etc/fstab and change testhome to just home:
```
/dev/mapper/data-home    /home    ext4    defaults    0    2
```
[*]Boot from a Live CD (you cannot continue with your usual boot).
[*]Decrypt your partitions:
[LIST]
[*]Decrypt your partitions. Remember to change sdA5 and sdB1 to the correct partitions (you'll get a non-destructive error if you get it wrong).
```
sudo cryptsetup luksOpen /dev/sdA5 root
```
[/LIST]

[*]Mount your partitions. You need worry *only* about root and data; you do *not* need to mount EFI and boot. N.B. The name of the root partition might be different from what I have given. Please list [FONT=courier new]/dev/mapper[/FONT] to see its correct name, and fix the mount command accordingly.
[LIST]
[*]```
sudo mkdir /mnt/root
sudo mkdir /mnt/newhome
sudo mount /dev/mapper/lubuntu-vg-root /mnt/root
sudo mount /dev/mapper/data-home /mnt/newhome
```
[/LIST]

[*]Check that:
[LIST]
[*][FONT=courier new]/mnt/root[/FONT] is your correct root
[*][FONT=courier new]/mnt/root/home[/FONT] is your correct home
[*][FONT=courier new]/mnt/newhome[/FONT] is your new desired home, i.e. the HDD
[/LIST]

[*]Copy your current home to your new desired home.
[LIST]
[*]```
shopt -s dotglob
sudo cp --archive --target-directory=/mnt/newhome /mnt/root/home/*
```
[/LIST]

[*]Remove the current (old) home.
[LIST]
[*]```
shopt -s dotglob
sudo rm --recursive /mnt/root/home/*
```
[/LIST]
[/LIST]
Reboot into your machine and check that it's all in order. If everything is OK, you can remove the test folder:
```
sudo rm /testhome
```

---

### Post by hmarius on 2017-07-04
That worked!! For lubuntu, the root partition was named lubuntu--vg-root. Also, in step 7 I think there was an error, it should be ```
sudo rm --recursive /mnt/**root**/home/*
```

I only had to enter the password for my system partition at boot up, I wasn't prompted for the data partition password. If I understand this correctly, it's because I generated a key that unlocks the data partition, but the key is saved to the system partition, so unless the system partition is decrypted, the key is not visible. Is that right? Otherwise the only difference for this set up from your original instructions is that the boot and swap partitions are unencrypted (I just turned swap off, I think it won't make a big difference).

I've been trying to better understand LUKS and LVM, and your tutorial and these instructions have been a huge help, so thanks very much!

---

### Post by LostFarmer on 2017-07-04
Paddy Landau--Decided to give Mint a try.  With some command modifications to [https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessSetUpBoot](https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessSetUpBoot)  steps 3,4,and 5 it worked.  Had to add sudo and change the path on each chmod command.  example: ```
sudo chmod +x /mnt/root/lib/cryptsetup/scripts/getinitramfskey.sh
``` and change the last command to sudo /mnt/root/usr/local/sbin/refreshgrub

Also just to say, live mint uses xed vice gedit. 

Installed on an USB hdd with the efi partition.

added: no separate /home only boot,root,swap with no hibernate at this time.

---

### Post by Paddy Landau on 2017-07-05
> **hmarius said:**
> That worked!! For lubuntu, the root partition was named lubuntu--vg-root. Also, in step 7 I think there was an error, it should be ```
sudo rm --recursive /mnt/**root**/home/*
```
Thank you. I've corrected my post.
> **hmarius said:**
> I only had to enter the password for my system partition at boot up, I wasn't prompted for the data partition password. If I understand this correctly, it's because I generated a key that unlocks the data partition, but the key is saved to the system partition, so unless the system partition is decrypted, the key is not visible. Is that right?
Yes, that's correct.
> **hmarius said:**
> Otherwise the only difference for this set up from your original instructions is that the boot and swap partitions are unencrypted (I just turned swap off, I think it won't make a big difference).
Ah, I didn't realise that swap was unencrypted. It should have been automatically encrypted by the default installation — is it not included in [FONT=courier new]/etc/crypttab[/FONT]? Let me know; if not, it's easy to add in. Ask if you want it. Without swap, you will hit problems if you use "large" apps; e.g. my 4Gb machine crashes without swap if I'm simultaneously using Chrome with several tabs, and LibreOffice with a huge document containing many images.
> **hmarius said:**
> I've been trying to better understand LUKS and LVM, and your tutorial and these instructions have been a huge help, so thanks very much!
Pleasure!
> **LostFarmer said:**
> Decided to give Mint a try. With some command modifications … it worked.
Installed on an USB hdd with the efi partition.
added: no separate /home only boot,root,swap with no hibernate at this time.
Thank you for this. I had tested on Mint, but I don't remember what modifications that I had to make. I tested 18.1. Which version did you install?

---

### Post by Paddy Landau on 2017-07-05
> **LostFarmer said:**
> &#8230; no hibernate at this time.
Heads up! I had missed out an important step for hibernation in the instructions, sorry.

Please see the new step 5, [Repair hibernation resume]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessSetUpBoot#Repair_hibernation_resume"). You can retrofit it into your running system as follows (a simple [FONT=courier new]sudo[/FONT] on the original command won't work because of the redirection).
```
echo RESUME=/dev/mapper/system-swap | sudo tee /etc/initramfs-tools/conf.d/resume
```
Of course, if your hibernation already works, please don't do this!

---

### Post by LostFarmer on 2017-07-05
[QUOTE=Paddy Landau;13662684 Which version did you install?[/QUOTE]
Used 18.1
 
[https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessPartitionFormatEncrypt](https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessPartitionFormatEncrypt) step 4. Create the system partition has an error for MInt 18.1 on useing 'gparted'  it does not have "**partition name**" option in making a partition.

On setting up the LVM, my opinion it would be best to use the label 'system-vg' to keep the standard of naming and not confuse a user in the label 'system' for the LVM.  Of course it works as is.

To restate the errors on the 'Set up boot' page.  sudo may not be needed in ubuntu but the path I am sure will be wrong no matter what linux is in use.  You have at step #3  
```
sudo -H gedit /mnt/root/lib/cryptsetup/scripts/getinitramfskey.sh
```  to create and save the file then later 
```
chmod +x /lib/cryptsetup/scripts/getinitramfskey.sh
```  the path MUST be the same, I would think.

This is only my messing around and did not try hibernate section.  Might retry with ubuntu 16.04 if the iso will loop boot or/and debian.

Thanks for making the How-to

---

### Post by Paddy Landau on 2017-07-05
> **LostFarmer said:**
> Used 18.1
Strange that we had different results! Unless, of course, I am misremembering something, which is entirely possible.
 > **LostFarmer said:**
> [https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessPartitionFormatEncrypt](https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessPartitionFormatEncrypt) step 4. Create the system partition has an error for MInt 18.1 on useing 'gparted'  it does not have "**partition name**" option in making a partition.
Oh, OK.
> **LostFarmer said:**
> On setting up the LVM, my opinion it would be best to use the label 'system-vg' to keep the standard of naming and not confuse a user in the label 'system' for the LVM.  Of course it works as is.
I thought long and hard when trying to choose standards on creating this tutorial. I don't remember why I ended up with the standard that I did, but it's absolutely fine if you choose to use a different standard.
> **LostFarmer said:**
> You have at step #3  
```
sudo -H gedit /mnt/root/lib/cryptsetup/scripts/getinitramfskey.sh
```  to create and save the file then later 
```
chmod +x /lib/cryptsetup/scripts/getinitramfskey.sh
```  the path MUST be the same, I would think.
No, they are deliberately different, because the first command is instructed to run through Alt+F2, whereas the second is within chroot in the terminal. Using the second path in the first command would edit the wrong file, whereas using the first path in the second command would give an error. Perhaps you used the first command from the chroot?
> **LostFarmer said:**
> Might retry with ubuntu 16.04 if the iso will loop boot or/and debian.
I haven't the faintest idea how to use a loop boot!
> **LostFarmer said:**
> Thanks for making the How-to
No problem. It was really for me, but I wanted to share with the world :)

---


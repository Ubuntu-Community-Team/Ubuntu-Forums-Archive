---
title: "Grub Config Changes with  LMDE6 Install / Changes Boot Order of Debian and Slackware:"
date: 2023-12-17
forum: Ubuntu/Debian BASED
---

### Post by UltimateCat on 2023-12-17
Upon installing LMDE6 I've had unusual behavior with Grub and other unexplained issues on a friend's custom built desktop as well.

After installing LMDE6 on my bf's desktop and removing the installation media the first boot lead to only having the grub rescue> prompt.
I used a Debian 12 Live USB to re-install Grub and rebooted. Still had the 'grub rescue> prompt' and the funny thing was all of my friends partitions were still in place and the boot info. script confirmed that
Grub was installed to all 3 of his HDD's.

Having the thought to look into the BIOS I discovered that the boot order that I originally set was switched around completely.
I helped my friend to get his drives back into the order in which they originally were with /dev/sda  (SSD) first, /dev/sdb (Hitichi) second, and /dev/sdc (WD) last in the boot order.
Rebooting was a success and he had Grub.

Since installing LMDE6 to the Samsung nvme on my triple booted Asus desktop I've had unusual behavior with Grub as well.
The first fresh boot after the LMDE6 installation the Debian 12 , /dev/sda/ installation to my 1 TB HDD and my Slackware 15, /dev/sdb/ install on the WD were switched around.

A few days ago there was a upgrade to the kernel on the LMDE6 install, so I allowed the update for the new kernel and rebooted.
Upon rebooting Debian 12 and Slackware 15 were switched around again.

Yesterday I had to remove old kernels and their headers on my Debian 12 install as the /boot partition was full and there was 0 bytes left of the disk.
Rebooted and updated grub in the LMDE6 installation and shut down for the evening.

The boot order of Debian and Slackware in my Grub Menus has been switched around again!

Before installing LMDE6 this flip flopping of the drives did not occur. Furthermore, there wasn't any other unusual behavior of any kind with Linux Mint 21.1 installed 
to the main drive: the Samsung Evo nvme that's set in the BIOS to be the main device.

Anyone have any ideas as to what is going on?

Any assistance is appreciated, thanks in advance.-:P
  Ultimatecat

---

### Post by oldfred on 2023-12-17
I have multiple Kubuntu installs & occasionally something else.
I use this to know what is where. And save report to my backups.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Typically last install changes boot order so that one is the new default. If you want a different install to be default, you have to change boot order. Often easier to just reinstall grub from preferred install and add a grub entry for newest install. I prefer my own entries in 40_custom over os-prober.

---

### Post by UltimateCat on 2023-12-17
Thanks for the swift reply, Olfred-

I'll have to make a Live USB  of 'Boot Repair' as my desktop does not have a cdrom drive.
Will using the dd command work?

When you make your own 40_custom entries is that done in the /etc/default/grub config or in /etc/ftab/?

---

### Post by UltimateCat on 2023-12-17
Here's the Paste Bin link to the output of the boot info. script:

[https://pastebin.com/gn2FJyVU](https://pastebin.com/gn2FJyVU)

---

### Post by oldfred on 2023-12-17
You show old BIOS boot with both very old MBR (sda) and newer gpt partitioning (sdb & NVMe). 

Report not showing anything about Linux partition on NVMe drive.  I would expect you would want installs on NVMe drive as that greatly improves performance.

Report also did not show Slackware's fstab, see line 657.  Do you have that and report did not show it.
Not sure Boot-Repair has been tested a lot with Slackware.

You show a total of 3 swap partitions. Unless trying to hibernate on 3 different systems, you really only need one swap partition.
But have to make sure a new install does not reformat the unformatted swap and reset its UUID. Then other installs may have issues booting.

I add boot stanzas to /etc/grub.d/40_custom in Ubuntu. I expect Debian to be same, not sure about Slackware.

You have UEFI system,  since you have NVMe drive, so bit surprised your installs are old BIOS/MBR.
I started using gpt in 2010 and have not created nor changed a drive to MBR since. But did not start with UEFI until 2014.

Using 40_custom & Custom menu
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
Lots of discussion & examples. May be best to read first page & jump to last page & work backwards for newest examples.
[https://ubuntuforums.org/showthread.php?t=2076205](https://ubuntuforums.org/showthread.php?t=2076205)

---

### Post by yancek on 2023-12-18
Some curious things I see in your boot repair include Grub version 1.99 installed on both drives?  It also shows Grub looking for its files on sda in partition 92 and on sdb in partition 87 which do not exist.  What is the vfat partition on sda (sda3)?  Was that an EFI partition?  It shows a grub.cfg file there.  sdb1 is a BIOS Boot partition which is used for a Legacy install on a GPT drive.  It shows 2 swap partitions, sdb2 and sdb3.  I see the grub.cfg file on sda contains only Debian entries and the grub.cfg file on sdb only Slackware.  Were these systems being booted from the BIOS firmware?  I see that sdb is shown as a GPT drive but no indication if it is GPT or dos?  Lines 106 and 107 show info on the nvme drive but I see nothing else regarding that drive so what is that supposed to be, the LMDE?

---

### Post by UltimateCat on 2023-12-18
Thank you Olfred for the information you explained. I'll go and read about using 40_custom and custom menu and the other link's you posted.
I can delete one of the swap partitions on the Slackware install in Debian with g-parted.
Do I only need one swap partition for all 3 install's?

---

### Post by UltimateCat on 2023-12-18
Thanks for chiming in yancek.
The vfat partition on sda3 is a 300 MiB partition for the /boot/efi.

No, these were not being booted from the BIOS firmware.
The reason why there is a BIOS boot partition is because the Slackware documentation recommended that I do that in order to have Grub instead of LILO for Slackware.

Here are the instructions I followed for my Slackware install on /dev/sdb : the 500 WD HDD.
[https://docs.slackware.com/howtos:slackware_admin:installing_with_gpt_without_uefi#accessing_the_slackware_install_prior_to_bootloader_installation](https://docs.slackware.com/howtos:slackware_admin:installing_with_gpt_without_uefi#accessing_the_slackware_install_prior_to_bootloader_installation)

[FONT=sans-serif]After the message: &#8220;Installation of Slackware Linux is complete.[/FONT]

Enter the SHELL then run these cmds.[COLOR=#6AB3F3][FONT=&amp]
[/FONT][/COLOR]
[FONT=&amp]# [FONT=Arial]chroot /mnt[/FONT][/FONT]
[COLOR=#6AB3F3][FONT=&amp]
[/FONT][/COLOR]
[FONT=sans-serif]If you want to use Grub 2, make sure you have a 'BIOS boot partition' (partition type EF02 in gdisk  or cgdisk). This can be anywhere on disk though putting it at the start  seems sensible. It is recommended that it be at least 1MiB. Skip the  bootloader (LILO) section during install. After installation is  complete, [enter your local Slackware install]("https://docs.slackware.com/howtos:slackware_admin:installing_with_gpt_without_uefi#accessing_the_slackware_install_prior_to_bootloader_installation"). Finally, issue the following to actually install Grub 2 as your bootloader:
[/FONT]
[FONT=sans-serif]# grub-install --modules=part_gpt /dev/sda
# grub-mkconfig -o /boot/grub/grub.cfg
#exit
#reboot 

Here's informaiton on the nvme: and yes, LMDE6 is installed to the nvme.
[HTMLroot@slackware64:~# fdisk -l
Disk /dev/nvme0n1: 232.89 GiB, 250059350016 bytes, 488397168 sectors
Disk model: Samsung SSD 970 EVO Plus 250GB          
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x7edfcd8f

Device         Boot    Start       End   Sectors   Size Id Type
/dev/nvme0n1p1          4096  17190911  17186816   8.2G 83 Linux
/dev/nvme0n1p2      17192960 488396799 471203840 224.7G 83 Linux
][/HTML]

Should I delete those 2 swaps on my Slackware install?

[/FONT]

---

### Post by oldfred on 2023-12-18
It looks like the instructions you followed for Slackware are for the old BIOS install.
Does Slackware even have UEFI install? Found this:
[http://docs.slackware.com/howtos:slackware_admin:installing_on_uefi_hardware](http://docs.slackware.com/howtos:slackware_admin:installing_on_uefi_hardware)

But you may be able to boot UEFI from your install and then create a boot stanza to directly boot Slackware.
I have an UEFI install on an External drive and booted it with my very old (2006) laptop by adding a BIOS boot stanza to directly boot grub in the install. You may be able to reverse that. The only real difference with UEFI & BIOS is the version of grub. The grub in the install is the same. 

If you delete swap partition(s), make sure you delete fstab entries first or update swap entry with UUID of the one you keep. Otherwise you may have boot issues.

---

### Post by UltimateCat on 2023-12-18
Output form Slackware:
```
root@slackware64:~# cat /etc/fstab
/dev/sdb2        swap             swap        defaults         0   0
/dev/sdb3        swap             swap        defaults         0   0
/dev/sdb4        /                ext4        defaults         1   1
#/dev/cdrom      /mnt/cdrom       auto        noauto,owner,ro,comment=x-gvfs-show 0   0
/dev/fd0         /mnt/floppy      auto        noauto,owner     0   0
devpts           /dev/pts         devpts      gid=5,mode=620   0   0
proc             /proc            proc        defaults         0   0
tmpfs            /dev/shm         tmpfs       nosuid,nodev,noexec 0   0
root@slackware64:~# ls /etc/fstab/
/bin/ls: cannot access '/etc/fstab/': Not a directory
root@slackware64:~# 

```

I don't know if Slackware has UEFI install. I'll have to go to the Slackware documentation.

This is a Asus Tuf Gaming mobo and the BIOS are UEFI.
Custom built desktop approx 3 years ago:-

Which fstab entries should I delete?
The ones on LMDE? Debian 12?

---

### Post by UltimateCat on 2023-12-18
Thanks for the Slackware UEFI link.

You said: "But you may be able to boot UEFI from your install and then create a boot stanza to directly boot Slackware."
I'll have to do some reading as I'm not well versed in this.

---

### Post by oldfred on 2023-12-18
I found UEFI instrutions, see above.

You need to know which swap partition is either by UUID or device/drive/partition.
It looks like Slackware uses the old /dev/sdXY not UUID. With multiple drives that can lead to issues if drives are not found by UEFI/BIOS in exactly same order every time.

I also have motherboards that promote a flash drive from hd3 when pluged in, to hd0 when I reboot. That changes every grub entry not using UUID. I sometimes have to manually edit grub as I boot as grub has wrong drive & does not work.

---

### Post by UltimateCat on 2023-12-18
Grub2 Custom Menus is very helpful-:D
The link: How to have a custom Grub 2 menu that is maintenance I'm reading it now.....thank you!

---

### Post by yancek on 2023-12-19
>  The reason why there is a BIOS boot partition is because the Slackware  documentation recommended that I do that in order to have Grub instead  of LILO for Slackware.


The link you posted was to do a Legacy install on a GPT drive, installing boot code to the MBR  when you should have done an EFI install on the GPT drive.  Not sure why you did that as your other installs are EFI.  If you had booted the Slackware installer in UEFI mode, you would have several options including installing elilo to the selected /boot/efi partition and it would have created an entry in the BIOS for you to select.  If you wanted to use the Debian Grub to boot this, this would have been the option to select.  Or you could have selected to not install either as you would not need Grub on Slackware if you were booting from Debian.  If you installed elilo, you would have been able to select Slackware from the EFI menu on boot from the BIOS should the Debian bootloader fail.  If you did not install a bootloader for Slackware, you would have simply had to run grub-mkconfig as root from Debian to add it to the Debian grub.cfg file.  Some links below on installing Slackware UEFI.



file:///home/don/Downloads/set_up_grub_as_boot_loader_on_uefi_hardware-1.pdf

I installed Slackware UEFI and used elilo to create a boot entry in the BIOS firmware.  I use Grub from Ubuntu to boot both systems and have no problems.  Both are on a GPT disk with UEFI.

---

### Post by UltimateCat on 2023-12-19
Thanks for explaining yancek.
I followed those instructions because I thought it was the correct way to go. I didn't know to install Slackware in UEFI mode. 
The Slackware link says:
   To get Slackware to boot on  UEFI machines, bypass the LILO installation and select ELILO  installation when prompted during the install. 

I'm not sure how I would  use the Debian Grub to boot Slackware.
In the meantime,I'll read the links you posted.

  The .pdf didn't work for me as the file was not found.
Pale Moon can't find the file at /home/don/Downloads/set_up_grub_as_boot_loader_on_uefi_hardware-1.pdf.

Do you recommend that I re-install Slackware?

---

### Post by yancek on 2023-12-20
Bad link on my part so the simplest way to find the Slackware UEFI is to do an online search with slackware documentation 15 uefi and it should be the first link you get.

The method I described in my earlier post is what I used when I installed Slackware, namely to use elilo and it put an entry in the BIOS firmware.  I can then select it to boot Slackware that way.  The way to boot  Slackware from the Debian Grub menu is to have the Slackware drive attached and boot Debian and run the command as root (sudo):

```
sudo grub-mkconfig -o /boot/grub/grub.cfg 
``` 

Or use sudo update-grub which stub might also work on Debian?  This should add Slackware to the Debian grub boot menu.

---

### Post by UltimateCat on 2023-12-20
Slackware is already in my Debian Grub Menu so that's the good news.

Do you recommend that I perform a fresh installation of Slackware 15?

---

### Post by yancek on 2023-12-21
You indicate your problems with this situation began when you installed LMDE.  Are you using the LMDE as the primary bootloader or are you using Debian?  If you are able to boot Slackware from whichever bootloader you are using, no need to reinstall.  Using EFI on GPT drives is usually recommended as well as consistency, meaning all system EFI or all systems Legacy.  As you have seen, booting a Legacy install of a Linux OS from an EFI install of another Linux OS on a separate drive is not a problem.

---

### Post by UltimateCat on 2023-12-21
Yes, I'm using LMDE6 as the primary bootloader. Grub shows LMDE6 at the top, Debian second in the Grub Menu and my Slackware installation third in the Grub Menu list. All 3 distributions boot fine.

***It's baffeling to me why Debian and Slackware switch places in the Grub Menu when LMDE6 get's a new kernel or an update.***

Any idea's yancek why that is happening?

Slackware is missing the /etc/fstab file.....can one be created?

---

### Post by yancek on 2023-12-21
Debian and Slackware are each on separate hard drives, correct?  Are they permanently connected in the same manner, same port when you update grub from LMDE?

You can boot and use the system without fstab.  I'm quite surprised you don't have that file on Slackware.  Yes, you can create the file for Slackware if you want, logged in to a terminal as root.  You can check the fstab file in your other systems for a template or do an online search so you know which parameters you want to use.  Need to use the correct UUID if you are using them as well as the correct drive/partition. I posted my entry for the Slackware partition below which shows it on partition 6 of an SSD drive

>  /dev/nvme0n1p6   /                ext4        defaults         1   1

---

### Post by oldfred on 2023-12-21
Generally when you get a major update to grub, it changes boot order ot make that install the default.
You just then need to manage boot order preference.

You can use efibootmgr to change UEFI boot order.
Or just boot into preferred install & do a "sudo grub-install" which uses all defaults & ESP of entry in fstab.

man efibootmgr
sudo efibootmgr -v # to see current boot order
sudo efibootmgr -o xxxx,yyyy,zzzz #etc to set boot order Some only need one digit, others need all 4.
But HP computers do not seem to work with efibootmgr orfering. Then you have to use HP's system settings.

---

### Post by UltimateCat on 2023-12-23
Yes, Debian and Slackware are each on separate HDD's.
I'll check the fstab files on Debian and LMDE6 for a template. I understand now, to use the correct UUID for the right drive and partition.
Your example is helpful, thank you.

---

### Post by UltimateCat on 2023-12-23
Booted into Debian 12 the output was:
> sudo: efibootmgr: command not found

> man efibootmgr
No manual entry for efibootmgr


When Slackware and Debian get a new kernel I update-grub in LMDE6 and reboot and all distro's boot w/o fail.

So thinking on what you said, it must have been a major update to Grub that made this happen.
By this I mean the switching of the distro's in the Grub Menu.
That makes sense Oldfred: thank you.

The funny things is for the last 5 years Linux Mint on the nvme always stayed at the very top of the Grub Menu, Debian second and Slackware last in the Menu.
I never had this switching until the installation of LMDE6.

When I understand how manage the boot entries like you do with the 40_custom I'll practice that.
You've been very helpful, thanks.

---

### Post by UltimateCat on 2024-01-03
It's been on thing after another since the new year with getting my desktop and all 3 distro's right.

Finally had success with getting Devuan installed where LMDE6 used to be.
Oh, and btw, since installing Devuan there has not been any more flip flopping of my distro's in the Grub Menu.

I'm slowly but surely getting to the articles you linked for me.

Hope everyone's new year is off to a good start!:P

---

### Post by UltimateCat on 2024-02-22
Reading Grub 2 Custom Menu's was very helpful, thanks!

I installed Devuan over LMDE6 and the triple booted system run's fine now.

---


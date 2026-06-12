---
title: "i can't dual boot my windows 10 with elementary os"
date: 2018-10-30
forum: Ubuntu/Debian BASED
---

### Post by adhiessyaprames on 2018-10-30
hello everyone, i'm desperate want it work so bad. long story short, i  used to dual boot my windows 10 with my ubuntu 18.04 L.T.S. then i'm trying to change it's theme to look like elementary os, but in the middle of doing it my ubuntu stop working and need to forced shut down. after that my resolution lock in 800 x 600. since i so desperate want it work with normal resolution. so i decided to re install it with elementary os (juno). but after installing it i have another problem which is boot-up error(i don't know the real name of this error but i look it up on the internet it's called minimal bash like line editing is supported GRUB error) i'm trying to fix it with ubuntu boot repair but it said that i should run it on legacy bios system. i don't understand what happened i'm prety sure intall my windows on uefi bios system, but why it ask me to run it on legacy sytem. since i don't know how to run elementary os cd run on legacy i need your help to fix my problem because i'm not that familiar with ubuntu. thank every help will make me happy so much . [IMG]https://www.tenforums.com/attachments/general-support/210514d1540905639-i-confused-my-bios-mode-its-said-uefi-but-have-legacy-partition-hdgfgfdhfdhg.png[/IMG][FONT=Open Sans Condensed][SIZE=1][COLOR=#333333] 
**maybe this information can help? and for information i install windows 10 and elementary os on disk 1**[/COLOR][/SIZE][/FONT]

---

### Post by oldfred on 2018-10-30
Moved to Other OS since request for support, but not Ubuntu.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please attach link to the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

How you boot live installer UEFI or BIOS is how it installs. It then would also repair in that mode. You do need to always boot in same boot mode.
And best to boot in same boot mode as Windows. Report will show details.

---

### Post by adhiessyaprames on 2018-10-30
thank you so much for the answer i'll move the question to other category.

---

### Post by adhiessyaprames on 2018-10-30
hello everyone, i'm desperate want it work so bad. long story short, i used to dual boot my windows 10 with my ubuntu 18.04 L.T.S. then i'm trying to change it's theme to look like elementary os, but in the middle of doing it my ubuntu stop working and need to forced shut down. after that my resolution lock in 800 x 600. since i so desperate want it work with normal resolution. so i decided to re install it with elementary os (juno). but after installing it i have another problem which is boot-up error(i don't know the real name of this error but i look it up on the internet it's called minimal bash like line editing is supported GRUB error) i'm trying to fix it with ubuntu boot repair but it said that i should run it on legacy bios system. i don't understand what happened i'm prety sure intall my windows on uefi bios system, but why it ask me to run it on legacy sytem. since i don't know how to run elementary os cd run on legacy i need your help to fix my problem because i'm not that familiar with ubuntu. thank every help will make me happy so much . [IMG]https://www.tenforums.com/attachments/general-support/210514d1540905639-i-confused-my-bios-mode-its-said-uefi-but-have-legacy-partition-hdgfgfdhfdhg.png[/IMG]
[SIZE=2]**maybe this information can help? and for information i install windows 10 and elementary os on disk 1**[/SIZE]

---

### Post by oldfred on 2018-10-30
Already moved. 
Post link to Boot-Repair's summary report.

---

### Post by oldfred on 2018-10-30
Merged threads.
Do not post duplicates, you cannot move yourself but always can request a moderator or admin to move a thread using the report post link.
Report post is for any help on a thread, not just reporting SPAM.

---

### Post by adhiessyaprames on 2018-10-30
thank you so much i'm so sorry for breaking so many rules, apparently i managed to solved previous problem, now i can boot to my elmentary os but now my win 10 did't show up after i chose windows boot manager this is the report link [http://paste.ubuntu.com/p/9xpBBfjzpm/](http://paste.ubuntu.com/p/9xpBBfjzpm/)

---

### Post by oldfred on 2018-10-30
It looks like both are installed in UEFI boot mode on sdb which is gpt partitioned.
Your sda has an old grub2 BIOS boot loader and drive is MBR.

Can you boot Windows directly from UEFI?

Grub only boots working Windows. Or Windows that does not have fast start up which is hibernation on, nor if the NTFS needs chkdsk. Then you may be able to directly boot from UEFI and maybe f8 to get into Windows internal repair console. But best to have the Windows repair flash drive.

Try turning UEFI Secure Boot off.

What brand/model system?
Have you installed nVidia driver from Ubuntu repository?  Do not install directly from nVidia.

---

### Post by adhiessyaprames on 2018-10-31
> **oldfred said:**
> It looks like both are installed in UEFI boot mode on sdb which is gpt partitioned.
Your sda has an old grub2 BIOS boot loader and drive is MBR.

Can you boot Windows directly from UEFI?

Grub only boots working Windows. Or Windows that does not have fast start up which is hibernation on, nor if the NTFS needs chkdsk. Then you may be able to directly boot from UEFI and maybe f8 to get into Windows internal repair console. But best to have the Windows repair flash drive.

Try turning UEFI Secure Boot off.

What brand/model system?
Have you installed nVidia driver from Ubuntu repository?  Do not install directly from nVidia.

i don't know how to boot windows directly from uefi, i only know how to change the boot loader order, my system is biostar TA970 with amd fx-8350 and gtx 1050 Ti and i don't know how to turning my uefi secure boot off, i've search it on the internet and couldn't find it. i don't know if i already install the driver or not, how to check it if i already download the driver from repositry?

---

### Post by oldfred on 2018-10-31
The UEFI boot menu is the same as the menu you used to boot the USB flash drive.

       Screen shots of secure boot settings, several models
[http://www.rodsbooks.com/efi-bootloaders/secureboot.html](http://www.rodsbooks.com/efi-bootloaders/secureboot.html) 
Many call it "Windows" or "Other" but fine print then says if installing Windows 7 use "Other". Windows 7 does not support UEFI Secure Boot.

Report said you were using the nouveau driver.

lspci -nnk | grep -iA3 vga
Kernel driver in use: nouveau

# make sure system is up to date
sudo apt-get update
sudo apt-get upgrade
sudo apt-add-repository ppa:graphics-drivers/ppa
sudo apt-get update 
   # should show newest versions available in addition
ubuntu-drivers devices
You then can manually choose any in list, replace XXX with version you want.
sudo apt-get install nvidia-XXX

---

### Post by adhiessyaprames on 2018-11-01
> **oldfred said:**
> The UEFI boot menu is the same as the menu you used to boot the USB flash drive.

       Screen shots of secure boot settings, several models
[http://www.rodsbooks.com/efi-bootloaders/secureboot.html](http://www.rodsbooks.com/efi-bootloaders/secureboot.html) 
Many call it "Windows" or "Other" but fine print then says if installing Windows 7 use "Other". Windows 7 does not support UEFI Secure Boot.

Report said you were using the nouveau driver.

lspci -nnk | grep -iA3 vga
Kernel driver in use: nouveau

# make sure system is up to date
sudo apt-get update
sudo apt-get upgrade
sudo apt-add-repository ppa:graphics-drivers/ppa
sudo apt-get update 
   # should show newest versions available in addition
ubuntu-drivers devices
You then can manually choose any in list, replace XXX with version you want.
sudo apt-get install nvidia-XXX

i already update to the newest driver that terminal recomended, thank you for the information. but as you can see at the image i attach there is no option to secure boot. 
[IMG]https://imgur.com/1crNMHb[/IMG]

---

### Post by oldfred on 2018-11-01
Please attach screen shots, not post in line.
You can easily attach with Forum's advanced editor and its paper clip icon.

What brand & model system?
If UEFI is from 2014, that normally would not be newest available from vendor.

       Legacy BIOS and  UEFI AMI AptioMar 2012 -  20 MIn
[http://www.youtube.com/watch?v=dRMIvY7BiL4](http://www.youtube.com/watch?v=dRMIvY7BiL4)
Video on getting into UEFI - 1 Min Acer but similar to all Windows 8
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI) 
    
       Acer Very latest UEFI/BIOS works, downgrade not required if no trust screens, you must now upgrade:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

### Post by adhiessyaprames on 2018-11-02
> **oldfred said:**
> Please attach screen shots, not post in line.
You can easily attach with Forum's advanced editor and its paper clip icon.

What brand & model system?
If UEFI is from 2014, that normally would not be newest available from vendor.

       Legacy BIOS and  UEFI AMI AptioMar 2012 -  20 MIn
[http://www.youtube.com/watch?v=dRMIvY7BiL4](http://www.youtube.com/watch?v=dRMIvY7BiL4)
Video on getting into UEFI - 1 Min Acer but similar to all Windows 8
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI) 
    
       Acer Very latest UEFI/BIOS works, downgrade not required if no trust screens, you must now upgrade:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
it's biostar TA970 motherboard

---

### Post by oldfred on 2018-11-02
Not familiar with Biostar, but others need iommu settings changed in UEFI and grub boot parameter. 
Microsoft requires vendors to allow users to turn off UEFI Secure Boot. My motherboard for whatever reason has UEFI settings under the CSM settings line in UEFI. And setting is "Windows" or "Other". Fine print say use "Other" for Windows 7 as it does not support UEFI Secure Boot.

       GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0 uses this boot parameter: amd_iommu=on iommu=pt  & UEFI settings
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

---


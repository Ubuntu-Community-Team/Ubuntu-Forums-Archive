---
title: "Grub with multi linux or Windows by itself issue BOOT loader"
date: 2017-04-06
forum: Ubuntu/Debian BASED
---

### Post by droseofc on 2017-04-06
[INDENT]I tried my best to search, read a few lengthy threads, and am posting it here, if it is exactly somewhere or close enough I apologize.[/INDENT]
 Anyways, I have a laptop that is NOT UEFI (I'm 90% sure), but I am able to boot from GPT disks and I believe that would indicate it is EFI capable? 
I have 1TB HDD that I hope to partition at least 20 or so partitions to be able to have different Linux distros for testing, school, work, fun,
 whatever AND a Windows install on the same hard drive.[INDENT]
Currently I have Fedora, Zorin, and Windows 10 and the HDD is gpt. I have partitioned a bios boot or whatever it needs to be in the [/INDENT]
size of 2MB and another behind it that is around 250MB or more. So sda1 is the 2mb, sda 2 is the 250mb, and the OS partitions follow behind it. 
I installed Windows first, then Zorin. Before installing Fedora, I quickly remembered the mbr restrictions on partitioning. I converted the HDD to gpt 
without any loss it seems, booted and Windows option at boot was gone. I expected this, and tried to fix using boot-repair among other things. No avail. 
I installed Fedora hoping it would pick it up, negative.[INDENT]
So, I had Zorin or Fedora to choose from, could still see the windows partitions from gdisk or fdisk or gparted, but couldn’t get it to add to the boot list.[/INDENT]
 Planning to stick with just Windows and one distro, I put in the Windows 10 install disk with the idea of starting over. For the hail mary I thought I might as well 
try the repair option, which I chose the startup repair from the windows disc. After nearly all day, to my surprise, the screen changed from "Attempting Repairs" 
to the Windows login screen. I checked the HDD and still is gpt and the Linux distros are still there, but I have no option as if it were Windows only while booting up. 
So, I now see that my laptop can boot Windows with gpt and it can boot multiple Linux distros on gpt.[INDENT]
How the heck do I get it to do it together rather than one or the other even with the others still on the disc. I have many tools at my disposal, repair disks, familiar [/INDENT]
with the terminal, not afraid of getting technical and actually prefer it, but really any help is greatly appreciated before I do have to start over from a bad choice.

The boot info from boot-repair can be found via my onedrive as I couldn't get it to upload on here, [https://1drv.ms/t/s!AiQHK--zro5_tV9QplvhpwxAkpV4](https://1drv.ms/t/s!AiQHK--zro5_tV9QplvhpwxAkpV4) or if that link looks sketchy heres my Google drive shared link [https://drive.google.com/open?id=0B_ySqznuS1_rbF9nNHZyd0pDeUE](https://drive.google.com/open?id=0B_ySqznuS1_rbF9nNHZyd0pDeUE) the date of the report is way off as I didnt change any of that in the boot-repair disk session

---

### Post by ubfan1 on 2017-04-07
If you'd post the disk-repair report link that would give us more information to help you.  A GPT boot disk does not imply UEFI.  It would however need a 1-2M partition with the grub-bios flag to boot in legacy mode.  Look in the BIOS/UEFI Settings for things like "Secure Boot" or CSM (compatibility) mode.  Windows in UEFI mode requires a GPT disk, and will have an EFI partition of approx 500M for the bootloaders. Some machines will boot either UEFI or legacy, with a preference selection as to which to try first.  You problem does sound like Windows in installed in one mode and the Linuxes in another.

---

### Post by Perfect Storm on 2017-04-07
Moved to Ubuntu/Debian BASED

---

### Post by droseofc on 2017-04-07
Ill get the boot info here in just a min. The laptop being used is a toshiba l875d, i am almost certain it does not have uefi capabilities.  By one mode do you mean that windows is stalled using mbr and Linux with gpt? Or uefi and the other legacy? Uefi should be out of the picture as I am familiar with uefi as I use it with pc and the laptop has nothing similar with the bios settings. 


> **ubfan1 said:**
> If you'd post the disk-repair report link that would give us more information to help you.  A GPT boot disk does not imply UEFI.  It would however need a 1-2M partition with the grub-bios flag to boot in legacy mode.  Look in the BIOS/UEFI Settings for things like "Secure Boot" or CSM (compatibility) mode.  Windows in UEFI mode requires a GPT disk, and will have an EFI partition of approx 500M for the bootloaders. Some machines will boot either UEFI or legacy, with a preference selection as to which to try first.  You problem does sound like Windows in installed in one mode and the Linuxes in another.

---

### Post by droseofc on 2017-04-07
I added links to the bottom of original post with boot info

---

### Post by yancek on 2017-04-07
The general theory is that with windows, if you want to use GPT, you need an EFI install.  If you want GPT with Linux, you can either install EFI or create a BIOS boot partition which you have done. 

The boot repair output shows you have windows code in the MBR of the 1TB drive so you should be able to boot windows.  With this setup,  you would need to copy the code from the IPL of the fedora/zorin boot sectors to a file, then copy that file to the root of the windows partition (C:\), then open the bcdedit as administrator and create an entry for the different Linux systems.  The other option is to install Grub to the MBR of the drive from either Fedora or Zorin, then run grub-mkconfig or update-grub to create a new menu for the different operating systems.  Note that neither the Fedora or Zorin grub.cfg files contain an entry for windows and that would be needed to boot windows from Grub. 

From what I have read about UEFI/GPT, if you want GPT on windows you need to use UEFI.  With Linux, you can either use UEFI and a separate EFI partition or you can create the BIOS boot partition which you have done.  I don't think mixing the two is going to work well for you.  If you want multiple partitions, I believe the maximum with MBR on SATA drives is 15 as long as one of the primary partitions is an Extended partition.

---

### Post by oldfred on 2017-04-07
You must have UEFI system. You would not have an UEFI boot entry otherwise.
> =================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
EFI in dmesg.
[    0.000000] ACPI: UEFI 00000000bfbfd000 000236 (v01 TOSASU TOSASU00 00000001 ACPI 00040000)
[COLOR=#ff0000]SecureBoot maybe enabled[/COLOR].

Make sure Secure boot is off. Many systems call that "Windows" or "Other" but in notes say if Windows 7 use "Other". Win 7 does not support Secure boot.

It looks like you created a hybrid partitioning scheme. You do not want that.
       [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)
Hybrid primarily was used by Mac that were only EFI (before UEFI) and older Windows that were only BIOS from MBR. So Mac booted in EFI from gpt and Windows from MBR with a BIOS boot. But you had to keep partitions in sync.
Windows only boots in BIOS boot mode from primary partitions or sda1 thru sda4.

First decide if you want UEFI or BIOS.
Then if UEFI partition with gpt or if BIOS partition with MBR(msdos).
And if BIOS Windows boot files (or boot partition) of Windows must be in a primary partition. But you can have an unlimited number of logical partitions if you convert one primary to the extended partition.
With gpt you can have 128 partitions all the same or in effect primary.

If using any system (Fedora) that uses LVM by default better to use manual install and standard partitioning, not LVM. LVM is intended as a full drive partitioning system.

 BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference) 

      One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 
    
GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by droseofc on 2017-04-07
I had thought I read somewhere with MBR you could have 4 primary partitions or 3 primary and 1 extended. That was maximum I thought. Which is why I would want gpt. In the past I have had a hard drive with 20-30 different partitions on a gpt hdd that were all linux distros, and the laptop was able to boot it with no issues. With that being said, the laptop should be able to boot a gpt disc. I do think I needed to have the protective mbr for the bios boot though. I read somewhere that Windows bootloader could not boot without uefi but that was just for the Windows bootloader and that others could. The laptop is Toshiba L875D-S7230 and the only related boot settings in bios that is close to uefi is a "fast" or "normal" boot mode that does nothing. What I originally did was use easeus partition program to convert the mbr to gpt.  I then possibly used fdisk or gdisk to create the hybrid but not positive. I tried alot of different things. So, theres no bootloader that can see the protective mbr and give the option to boot Windows as well as see linux distros on the gpt portion? If that is the case I would be limited to 2 or 3 OS on the HDD if windows is one of them. I went to the site you linked and came across DUET. Is it worth considering? I'm going to pop in a live linux cd and see if I can boot to my other linuxes and if thats the case I'll have it as is with the windows to boot and use a usb or live cd to boot to the others. 


> **oldfred said:**
> You must have UEFI system. You would not have an UEFI boot entry otherwise.


Make sure Secure boot is off. Many systems call that "Windows" or "Other" but in notes say if Windows 7 use "Other". Win 7 does not support Secure boot.

It looks like you created a hybrid partitioning scheme. You do not want that.
       [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)
Hybrid primarily was used by Mac that were only EFI (before UEFI) and older Windows that were only BIOS from MBR. So Mac booted in EFI from gpt and Windows from MBR with a BIOS boot. But you had to keep partitions in sync.
Windows only boots in BIOS boot mode from primary partitions or sda1 thru sda4.

First decide if you want UEFI or BIOS.
Then if UEFI partition with gpt or if BIOS partition with MBR(msdos).
And if BIOS Windows boot files (or boot partition) of Windows must be in a primary partition. But you can have an unlimited number of logical partitions if you convert one primary to the extended partition.
With gpt you can have 128 partitions all the same or in effect primary.

If using any system (Fedora) that uses LVM by default better to use manual install and standard partitioning, not LVM. LVM is intended as a full drive partitioning system.

 BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference) 

      One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 
    
GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by oldfred on 2017-04-07
You should not need DUET, that was to allow testing UEFI on BIOS only systems.

You can just use MBR if you must have Windows in BIOS Boot mode. 
It just is that Windows in BIOS mode must be on a primary NTFS partition with boot flag and drive must be MBR(msdos).
The extended partition is one of the 4 allowed primary partitions, but  acts as a container for as many logical partitions as you want.
And Linux installs to logical partitions and boots in BIOS mode then.

Or you can install Windows in UEFI mode on gpt partitioned drive and have any number of Linux installs in UEFI mode. Or even in BIOS mode if you have a bios_grub partition. But then cannot boot installs in other mode than grub is. 
UEFI & BIOS are not compatible. So once you start to boot in one mode you cannot change. Or grub can only boot or chain load to other installs in same boot mode. But you still can dual/multiple boot from UEFI boot menu.

If you really want hybrid, you can boot Windows from BIOS/MBR and Linux from UEFI/gpt but must absolutely keep partitions in sync. Windows then only sees the MBR part and Linux with gpt will see all the partitions. Not sure if then you can read or write into NTFS from Linux without issue.

---

### Post by droseofc on 2017-04-07
is secure boot a windows settings through windows itself or in bios? I do not see anything in the bios that says secure boot or legacy/uefi or cfm etc. the only option is fast/normal boot and that just skips the bios option at boot up going straight to windows, when I hold shift and press the restart option in windows it does not give any option to go to the uefi settings as a uefi would, having a hard time getting to bios now, may take out battery or I believe toshiba has a program that allows access to bios settings through windows. Every bit of me wishes I could do without Windows but Wine and play on linux just too much to do when/if I could have a windows next to the others. Previously when reading, I had seen your username alot with similar issues helping others. Just wanted to say I appreciate and respect all of the time and help you give.

---

### Post by droseofc on 2017-04-07
So, if I were to start over, I would install Windows normally on a partition, say 250GB, and it is a primary partition, with any more partitions limited to 1 more primary and 1 extended.  I think Windows premakes 2 partitions to itself during a normal install, one for system one for recovery/boot or whatever, if thats the case I would let windows get to the point right before install, change the size of the partition that it marked to fill the disk to 250GB, and have roughly 700GB unallocated. After Windows installs or during the install options make another primary partition with a extended partition that fills the remainder of the disk and within the extended partition I install linux distros using logical partitioning inside the extended?

---

### Post by oldfred on 2017-04-07
If you want BIOS/MBR that is the standard ways to install both systems.
You may be able to make the Windows install somewhat smaller & have a larger shared NTFS data partition if you want to share data. Best to set Windows install partition as read only from Linux.
But newer Windows 8 or 10 keeps all NTFS partitions mounted with its fast start up or hibernation. And then the Linux NTFS driver will not write into any mounted NTFS partition. So always make sure fast start up is off. And Windows will keep turning it on with updates. When fast start up on grub will not boot Windows either, so you have to use Windows repair disk or installer's repair console. And when Windows breaks/needs chkdsk only grub also will not boot it and you cannot fix from Linux, only Windows.

With UEFI you can boot Windows directly from UEFI boot menu when grub does not boot Windows. And sometimes f8 works to get into repair console when repairs needed. So somewhat more convenient with UEFI over BIOS.

---

### Post by droseofc on 2017-04-07
I would definitely prefer UEFI as I could use gpt and not have to worry about partitions, a quick way to check if the laptop is uefi is to create a usb bootable disk with Rufus using GPT partition for UEFI setting and trying to boot with it?

---

### Post by yancek on 2017-04-07
I'm not sure what your intentions are but, it is possible to install windows 10 on a single partition if you want.  Did it last year, just set the partition you want to install to as the active/bootable partition and make sure you select the "Custom" installation option.  It should not really be a problem using 2 partitions for windows as you can always create logical partitions on the Extended and install and boot Linux from them.

---

### Post by droseofc on 2017-04-07
I am trying to boot with 25 different linux distros and windows on the same hdd. I just installed super grub2 disk to a usb and booted from the usb and the grub2 disk was able to see all of the OSs including fedora, zorin, and Windows. If this grub2 disk can how can i get that into an actual grub 2

---

### Post by droseofc on 2017-04-07
Not entirely sure if or what I did anything but its working now. I booted with super grub2 disk on a usb, it was able to see all of the OSs on the hdd. I chose Zorin, expecting to have to do the repair option when I went into Windows again. When I booted into Zorin I did an apt update and upgrade. It either updated or installed grub and during the updating grub I seen it listed windows loader. Rebooted just to verify and there they all were. 

So now I should be able to continue installing linux distros on newly made partitions and when they install grub it should also see the windows and the rest? 

And if they dont I can just boot back into zorin and update grub from there?

[[img]https://preview.ibb.co/nxy3vk/20170407_214031.jpg[/img]](https://ibb.co/b16Co5)
[ebay image hosting](https://imgbb.com/)

---

### Post by yancek on 2017-04-08
If you are able to boot from the Grub on Zorin, when you install a new distro, select to install the bootloader to the partition on which you are installing the new OS.  That way you should be able to reboot and select Zorin from the boot menu and run update-grub to add the new OS to the boot menu.  If you install Grub for each new OS, it should show itself as the first boot option and you would then boot it and update grub from it to add the other operating systems.

The 'update-grub' command is specific to Ubuntu so if you are installing other Linux systems, the command is grub-mkconfig.  That is the actual script run to create new boot menus and all the update-grub script does is point to the grub-mkconfig script.

I'm not sure how many partitions you will be able to create.  My understanding was the limit was 16 for SATA drives and the older IDE drives 63 on an MBR.  Doing some googling, I found sites similar to the one below so maybe that isn't actually the case.

  [http://www.linuxquestions.org/questions/linux-newbie-8/max-number-of-logical-partition-754458/](http://www.linuxquestions.org/questions/linux-newbie-8/max-number-of-logical-partition-754458/)

---

### Post by oldfred on 2017-04-08
Do not know about other distributions. 
But Ubuntu can be installed without installing grub.
 This launches the installer program (Ubiquity) with an option (-b) to not install a boot loader from live installer in live mode:
In the Terminal window, type ubiquity -b.  

Some distributions may let you not install grub boot loader.
If grub is installed in Ubuntu, it has a setting on which drive install is in. And on a major update will reinstall into that drive.
      
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short  
    sudo grub-probe -t device /boot/grub 
   #to get grub2 to remember where to reinstall on major updates
sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

To manage a grub menu, you will want to customize it with your own boot stanza.
Ubuntu puts links to most current kernel into / so you can create boot stanza to boot just that link and always boot newest kernel without having to edit grub in main install you boot with.
       
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus) 

 If only wanting to install & test an install, it might be easier to use flash drive(s). I have several flash drives with different versions of Ubuntu as full installs and a couple with just the ISO as repair tools and using grub to directly boot the ISO. I also have several ISO on my hard drives that my regular install of grub is also configured to boot those ISO.
      
 This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

---

### Post by droseofc on 2017-04-09
I have vmware and do run virtual machines to test out new distros I have not tried yet, but so far with distrowatch.com I have burned over 50 different isos and have tried them all, so my list for 20 or more partitions with each having a distro fills up quick. I'm going to partition the rest of the hard drive right now just to make sure I am able to as a normal gpt disk would with 128 partition limit, will not go that high but expecting over 20 at least. And then if that works I am going to install some distros. I'm talking like literally right now so I will be back to report and mark as solved or give up in just a bit.

---

### Post by droseofc on 2017-04-18
So, wasn't right back as planned, apologies, but I went to install UberStudent which is based off Ubuntu I believe, and after installing it Windows would no longer boot and instead would only restart to the grub screen, I checked the commands for the windows option and it had chainloader +1 on the bottom. Not sure if it was the cause, but in the end I have no reinstalled windows 10 successfully on a gpt hard drive and is working normally. Shouldn't I be able to now partition as I like and install as many (up to 128 partitions) Linux distros as I like? Where does the issue come in when doing windows and multiple Linux? When I did just strictly Linux and a bunch of them, alls I had to do was update the grub and being gpt there was no issue with the amount. Now I have windows, gpt should still allow 128 partitions, grub updates and can see the windows but where does that problem occur that windows  will no longer boot because of it? or was it just me?

---

### Post by oldfred on 2017-04-18
Must be just you. :)

Grub only can boot working Windows. 
Or Windows that is not hibernated nor needs chkdsk. So make sure fast start up/hibernation is off in Windows.
You should always be able to directly boot Windows from UEFI boot menu, if grub does not work. And that will happen with resize of NTFS partition or some Windows updates where it turns fast start up back on and makes itself first in UEFI boot order.
If you resize the NTFS partition make sure to only use Windows to resize it and immediately reboot into Windows so it can run chkdsk. Chkdsk fixes the partition as it must have same info on start & size as partition table.

---

### Post by droseofc on 2017-04-18
I'm only familiar with UEFI from my pc, the motherboard is an asrock z170 oc formula. I know that uefi menu and exactly what you are talking about. But on this laptop the only menu i've ever gotten to come up is the regular bios menu or grub. Normally, at least on that asrock, if you hold down shift and click the reboot option in windows it will have an option to go to uefi firmware settings. This laptop does not. so idk what i am in, because i thought with gpt you had to have uefi, or efi. I used diskpart at the installation for windows using shift+f10 for cmd, and cleaned the disk, converted to gpt, and then installed it from the gui. so it has to be gpt, even has the asterisk on diskpart under gpt. But i have no uefi looking bootloader, no uefi options from the windows restart by holding shift. Theres some little connection in this loop of uefi/gpt/efi/mbr/bios that I am not getting and once I do I'll become grasshoppafred and be able to help others lol.

---

### Post by yancek on 2017-04-18
> because i thought with gpt you had to have uefi, or efi. 

Yes, that's true for windows but not necessary with Linux.  You can create a BIOS boot partition and use GPT with an MBR install but only with Linux, AFAIK.

---

### Post by droseofc on 2017-04-18
[[img]https://preview.ibb.co/gwUP5k/Untitled.jpg[/img]](https://ibb.co/b3HoWQ)
[jpg to img](https://imgbb.com/)

It says I am in legacy bios mode, so I have it misunderstood that windows can only boot gpt if its uefi or efi because its gpt and its not uefi or efi.

---

### Post by oldfred on 2017-04-18
Post this, disk label will show if gpt or MBR(msdos):
sudo parted -l
sudo fdisk -lu

---

### Post by droseofc on 2017-04-19
> **oldfred said:**
> Post this, disk label will show if gpt or MBR(msdos):
sudo parted -l
sudo fdisk -lu


[[img]https://preview.ibb.co/ciqmJ5/20170419_003703.jpg[/img]](https://ibb.co/kgDTWQ)
[[img]https://preview.ibb.co/mqurkk/20170419_003825.jpg[/img]](https://ibb.co/mMmhrQ)
[[img]https://preview.ibb.co/ka36J5/20170419_003902.jpg[/img]](https://ibb.co/c7WFBQ)

---

### Post by droseofc on 2017-04-19
Im just going to ctrl+c out of that last question and wait for the experts. Ive seen it say found legacy mbr and gpt but never have been asked which to use or that its mbr only. Although, I do onlynhave windows so far, started fresh and made sure to diskpart clean and convert gpt before installing it.

---

### Post by LostFarmer on 2017-04-19
[http://www.asrock.com/mb/Intel/Z170%20OC%20Formula/](http://www.asrock.com/mb/Intel/Z170%20OC%20Formula/)   is this your motherboard ?

from site> Fast Boot is so fast that it is impossible for users to enter the UEFI  setup utility during POST. Therefore, ASRock Restart to UEFI technology  allows users to easily enter the UEFI setup utility automatically when  turning on the PC next time. It is designed for those who constantly  need to enter the UEFI setup utility

---

### Post by oldfred on 2017-04-19
How you boot install media for both Windows & Linux is then how it installs, either UEFI or BIOS.

And Windows only boots from MBR if BIOS, so you must have booted Windows installer in BIOS boot mode. If Windows 7 DVD, that is only BIOS boot, you have to copy to flash drive & move files around to make it UEFI.

With Ubuntu you can boot in either UEFI or BIOS from gpt if you have correct supporting partitions. You need bios_grub for BIOS or ESP - efi system partition if UEFI. 

UEFI and BIOS are not compatible. Once you start to boot in one mode, you cannot switch. Or once to grub menu, grub can only boot other systems installed in same boot mode. You can dual boot systems in different modes only from UEFI boot menu, often f10 or f12 check manual.

---

### Post by droseofc on 2017-04-22
I used a windows 10 creators update dvd, while in the installation for windows at the storage selection prompt i pressed shift and F10 to bring up a command prompt. I then diskpart, select disk 0, clean, convert gpt, exit. Refreshed the storage selection and it allowed me to select the gpt disk and made it's partitions. I then resized the windows partition so that I had space for future linux installations. Unless its booted in uefi mode for windows installation, it wont install to a gpt disc, right? Or did windows make a mbr partition on a gpt disc, if thats possible?

---

### Post by droseofc on 2017-04-22
That is my motherboard on my pc, I was referring to it only for clarification that I am familiar with uefi boot menu, as it was a pleasant change from what I had been used to before using uefi. The laptop I am having issues with is a toshiba l875d-s7230

---

### Post by oldfred on 2017-04-22
I believe I saw where the newest Windows has tools to convert from MBR to gpt. Do not know details.
But how you boot install media is then how it installs. And install with Windows in UEFI creates lots of partitions.
       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference)

There is such a thing as hybrid MBR/gpt. Primarily used with older Macs with gpt, and installing Windows in BIOS mode to MBR. But have to keep first 4 partitions in sync.

Newer Toshiba have needed work arounds. You actually boot a fallback or hard drive entry.
 Toshiba Satellite - turned Secure boot off in Boot-Repair update & UEFI
[https://ubuntuforums.org/showthread.php?t=2346022](https://ubuntuforums.org/showthread.php?t=2346022)
[http://ubuntuforums.org/showthread.php?t=2317643](http://ubuntuforums.org/showthread.php?t=2317643)
Toshiba satellite z930 copy shimx64.efi to /EFI/Boot/bootx64.efi
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair)

---


---
title: "Deleted Linux partition from dual-boot with Windows 8.1 but can't fix bootloader"
date: 2017-06-14
forum: Windows
---

### Post by woutervw2 on 2017-06-14
So this is a little embarrassing and perhaps not entirely on topic, but I really hope you guys can still help me.

My SSD/HDD hybrid work laptop came with Windows 8.1 preinstalled. Since I wanted to give Linux a go, I asked a colleague to help me set up a dual-boot system with Ubuntu. So he basically did all of the partitioning of my SSD and installed Ubuntu. Due to the exorbitant size of Windows' updates and the modest size of the SSD, I recently decided I had to get rid of the dual-boot. Although I prefer Linux on principle, I've ended up using Windows almost exclusively (barely anyone at work uses Linux). So I wanted to switch to a Windows-only situation. (Pretty much all of my data is on the HDD, by the way.)

Since the person who set up the dual-boot is no longer working where I'm working, I decided to go online and figure out what to do myself. In hindsight this may have been a mistake. While going through the process, I did not take pictures and when I came across a kink I interrupted my attempt, to avoid having an unusable system. In hindsight this may also have been a mistake.

So here's what I did:
0. I created a USB Recovery Drive, using the recovery partition of my laptop.
1. I opened up Windows' Disk Manager.
2. I identified the Linux partition and deleted it, intending to then extend the Windows partition to the whole SSD.
3. To the left of this partition, however, (and to the right of the Windows partition) I found a partition that I could not delete. I believe it said it was a system partition. To the left of the Windows partition I seem to remember a similar partition. I assumed this had something to do with the booting of both OS's, but the website I was following said we would fix the bootloader in the next step, so I didn't worry too much about this, although I did interrupt my attempts at this point since I couldn't really afford to have the laptop become unusable at this time. Since I used to use the Linux bootloader and I had just deleted the Linux partition, I assumed booting was now compromised and I should keep the laptop on at all times until I had time to properly deal with the issue.
4. I think Windows screwed me over by forcing my laptop to restart for updates last night, in any case I woke up to the black "grub minimum bash-line" screen.
5. I've attempted to fix the bootloader by inserting the Recovery USB, booting into the BIOS via the 'fwsetup' grub command and setting the USB as the first boot device. When the USB boots, I get the a lightblue screen where I am asked to select my keyboard lay-out. Then on the next screen I choose "Troubleshoot", then "Advanced Options" and then "Command Prompt". In the command prompt window I then run the command "bootrec.exe /fixmbr", then exit the command prompt and click on "Turn off your PC". Alas, I still boot into grub.

So this is pretty much where I am right now. I also tried using the Boot Repair from the Recovery Drive tools, but it was unable to fix the issue. Ideally I would love to just have a way to boot back into my current Windows installation and somehow get rid of the system partition so I can extend the Windows partition to the entire SSD. But if this is impossible, I would really want to at least be able to keep my HDD intact. Even if I have to somehow reset the entire SSD and then reinstall Windows on it, I'd be prepared to do that as long as I don't lose the data on the HDD.

Any help would be immensely appreciated!

---

### Post by oldfred on 2017-06-14
If you have the Ubuntu flash drive installer add Boot-Repair and run the summary report.
 May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 

Boot-Repair is primarily for Linux issues and can only fix some Windows issues.
Can you directly boot Windows from UEFI boot menu?

If you deleted any of these partitions, you may have issues. Vendors often also have additional recovery partition(s). This is for UEFI installs. BIOS has fewer partitions.

 [https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

### Post by woutervw2 on 2017-06-14
Thanks a lot for your unexpectedly fast response! The report url is [http://paste.ubuntu.com/24860526/](http://paste.ubuntu.com/24860526/)

I'm really a bit out of my depth with these boot options and partitions, it's my first time dealing with this stuff, so I'm not entirely sure what you mean by the UEFI boot menu. I assume this refers to the possibilities for the Boot Options in the Boot tab of the BIOS? (where the boot mode is UEFI) Those are (in order) USB Hard Disk, USB CD/DVD, Hard Disk:ubuntu and Network:UEFI: IP4 Qualcomm Atheros PCIe Network Controller. When I enter the UEFI Hard Disk Drive BBS Priorities, there's ubuntu as Boot Option #1, Windows Boot Manager as #2 and again ubuntu as #3.

Let me know if I should do anything else.

---

### Post by yancek on 2017-06-14
You have an EFI system, note the EFI partition shown in the boot repair outut (sda2) which contains both windows and Ubuntu EFI files.  Obviously, you can't boot into Ubuntu because you deleted the partition which contained some of the necessary boot files as well as the kernel.  You also have windows code in the MBR which you should not have with an EFI system.  You should have two options on boot, one to enter the BIOS setup and one to select a boot option.  Set it to UEFI boot in the BIOS and select the key which gives you the boot options.  This key varies with manufacturer so watch the screen on boot for it.

---

### Post by oldfred on 2017-06-14
In addition, you show sda5 with the boot flag making it a second ESP - efi system partition.
You can only have one per device/drive at a time.
So use gparted and remove boot flag from sda5.
Then using UEFI boot key often f10 or f12, but varies by vendor, check manual to directly boot Windows in UEFI mode. 
Do not boot in BIOS mode. You may need to make sure settings in UEFI have UEFI on, but CSM/BIOS/Legacy or whatever your system calls it off.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

### Post by woutervw2 on 2017-06-15
I have removed the boot flag from sda5 and been able to boot into Windows (the key for the boot options on my MSI laptop is apparently F11).

---

### Post by oldfred on 2017-06-15
Can you then boot Ubuntu the same way?

Some MSI systems have needed various boot parameters which you add like nomodeset.
 Failing to Boot Ubuntu 16.10 in MSI GP72
[http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72](http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72)
[SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)
MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815)
MSI PX60 2qd 034us Haswell & Optimus libata.force=noncq for SSD hangup
[http://ubuntuforums.org/showthread.php?t=2296878](http://ubuntuforums.org/showthread.php?t=2296878) 


 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by woutervw2 on 2017-06-15
Well, I've deleted the Linux partition, so shouldn't it be impossible for me to boot into Ubuntu now? I mean, there are 2 ubuntu entries in the boot options menu, but neither of them actually boots Ubuntu. The first one leads to a black screen with a red "Secure Boot Violation" message box reading "Invalid signature detected. Check Secure Boot Policy in Setup". When I click OK, it takes me to the "grub minimum bash-line" screen as usual. The other ubuntu option takes me to the "grub minimum bash-line" screen immediately, only it is aligned to the top left corner instead of centrally on the screen.

Should I try the nomodeset?

---

### Post by oldfred on 2017-06-15
If you deleted the partition there is nothing to boot.
UEFI just saves boot entries. And the ESP - efi system partition still has /EFI/ubuntu for initial boot of grub. Rest of grub was in Ubuntu partition.

---

### Post by woutervw2 on 2017-06-15
So how do I move on from here? Can I just Delete the sda5 partition, extend the Windows partition and then try step 5 from my first post again? And I don't have to worry about the boot entries in UEFI mode, just as long as I don't try to use invalid ones? Thanks very much for your help so far already, by the way!

> 5. I've attempted to fix the bootloader by inserting the Recovery USB,  booting into the BIOS via the 'fwsetup' grub command and setting the USB  as the first boot device. When the USB boots, I get the a lightblue  screen where I am asked to select my keyboard lay-out. Then on the next  screen I choose "Troubleshoot", then "Advanced Options" and then  "Command Prompt". In the command prompt window I then run the command  "bootrec.exe /fixmbr", then exit the command prompt and click on "Turn  off your PC".

---

### Post by oldfred on 2017-06-15
With UEFI Windows I thought you could just run the standard Windows repair, but you have to do that from the Windows repair/recovery/install drive. Ubuntu cannot repair most Windows issues.
But again have to know if UEFI or BIOS.
And in UEFI, you should just be able to set Windows entry as first in boot order in UEFI.

If you want to remove the UEFI entries, some UEFI let you do that from UEFI.
From Ubuntu live installer you can use efibootmgr. And also from Ubuntu live installer delete the /EFI/ubuntu folder. It may be mounted /media/$USER/EFI/ubuntu depending on how you mount it from live installer.

More info also in link in my signature.
First check entries, should show order & hex number assigned to each entry:
sudo efibootmgr -v
       Delete entry change XXXX to correct entries. Some UEFI require all 4 HEX char, other just need 1 or 2 significant char.
sudo efibootmgr -b XXXX -B
Delete Ubuntu
[URL="http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743"]http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743
[/URL]
 Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
sudo efibootmgr -o 2,1
see also 
man efibootmgr
[http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr](http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr) 

[URL="http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743"]
[/URL]

---

### Post by woutervw2 on 2017-06-15
I am in UEFI boot mode, and I could indeed just put the Windows entry as first in the boot order so now it boots fine into Windows. Thank you very much again for that already!

Now I have just a few questions left: below is a snap from the Windows Disk Manager (it is in Dutch, but hopefully everything is still clear). The partition now called (G: ) used to be the undeletable one in the way of extending my Windows (C: ) partition, that was the sda5 you had me remove the boot flag from. I assume I can now just delete it and extend the (C: ) partition without causing any problems? Also: how important is it to delete this /EFI/ubuntu folder manually at this time? Can I do this later?

(Can you actually see the attachment?)

---

### Post by oldfred on 2017-06-15
As long as you do not boot or try to boot Ubuntu, the entries in the UEFI and folder in ESP do not matter other than a small amount of space.

If you have no data in the sda5 FAT32 partition, you should be able to just delete it.

Moving thread to Windows sub-forum, since Windows issues.

---

### Post by woutervw2 on 2017-06-16
Okay, I've deleted the sda5 partition, but I can't extend the Windows partition since it's a boot volume. I assume this can be done using gparted, but I've read it's risky to use it for resizing Windows partitions. I've also read the Windows-aimed freeware MiniTool Partition Wizard can be used, but again I'm told this can be risky. In general it seems boot problems can occur when resizing a boot volume. This makes sense to me if I were to shrink the partition, but does it also apply for extending it?

(I'm sorry if this has now become a full Windows issue separate from Linux. If I should turn elsewhere for the final steps, I'll be happy to thank you again very much and do that.)

---

### Post by oldfred on 2017-06-16
Windows NTFS partitions have to have in the PBR - partition boot sector the same start & size info as the partition table. Both Chkdsk and fixBoot can update PBR, but you need to do that to all NTFS partitions, but probably only required on a bootable partition. Not sure with UEFI/gpt as system actually boots thru ESP, so not sure what checks Windows now does.

Most of us suggest Windows tools for Windows & Linux tools for Linux.
And some report gparted works, but others have issues & blame Linux for their Windows issues. So best to use Windows partition tools.

---


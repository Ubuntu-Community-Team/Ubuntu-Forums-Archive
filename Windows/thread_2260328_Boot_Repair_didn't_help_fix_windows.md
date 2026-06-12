---
title: "Boot Repair didn't help fix windows"
date: 2015-01-11
forum: Windows
---

### Post by joseph45 on 2015-01-11
Hi, I attempted to install linux in legacy mode on usb persistence. By doing so, now I cannot boot into windows. I attempted to fix this problem by burning boot-repair to a usb. It didn't help. I'm hoping to recieve some help. Thanks for any assistance! Here are the details for "fix."
[http://paste.ubuntu.com/9709647/](http://paste.ubuntu.com/9709647/)

---

### Post by Lorenz_ on 2015-01-11
What problems do you get when trying to boot into windows?

---

### Post by oldfred on 2015-01-11
You have no Linux installed.

Boot-Repair is primarily a Linux repair tool. It can only make minor repairs to Windows to sometimes resolve dual boot issues.

If you have Windows issues you need your Windows repair disk. 
       Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

You may when booting in UEFI mode be able to use f8 to get into Windows internal repair console.

Do not install Ubuntu in Legacy mode, it becomes difficult to dual boot as every time you have to go into UEFI/BIOS and turn on/off UEFI or BIOS boot mode. UEFI and BIOS boot modes are not compatible and you must totally reboot to change modes.

Do fully backup Windows & efi partition, before installing. Use Windows own partition tools to shrink the NTFS partition to make room for Ubuntu and immediately reboot to let it run chkdsk and repair itself for its new size.


 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)


More details in link in my signature.

---

### Post by joseph45 on 2015-01-12
Is there anything I can do if I do not have a repair disk? I tried using a repair disk once by downloading it off of the internet. I tried a couple variants, but nothing helped me. I tried using some of the advanced features of command prompt to repair my windows boot files, but nothing is working.

---

### Post by LostFarmer on 2015-01-12
> I cannot boot into windows  need more info.  Are you trying to boot into Win8 (EFI booting)  from the USB grub (non EFI booting) ?  if yes, it will not work.  Can not start booting in one mode and change to the other (MBR boot --EFI boot).  Does Win8 boot if the USB is removed ?  If not, just what happens ?

---

### Post by linuxuser600 on 2015-01-12
[FONT=Lucida Grande, Verdana, Bitstream Vera Sans, Arial, sans-serif][COLOR=#393733]Here are two links for Windows 7 repair discs if you need them. I agree with LostFarmer though. We will need more info to help

[/COLOR][/FONT]

[LIST]
[*][Windows 7 System Repair Disc **64-bit**]("http://maximumpcguides.com/downloads/windows-7-64-bit-repair-disc.iso")
[*][Windows 7 System Repair Disc **32-bit**]("http://maximumpcguides.com/downloads/windows-7-32-bit-repair-disc.iso")
[/LIST]

---

### Post by joseph45 on 2015-01-12
I formatted my usb using the FAT file system type. I tried downloading a  windows-8 repair disk in the form of an iso. I mounted the iso into the  /mnt/ folder and moved all of the repair disk's files to my usb. I  restarted my computer and pulled up my bios. Then, I chose UEFI and made  my usb the first UEFI option. I restarted my computer and was able to  boot into the windows-8 repair disk. Nothing I tried helped. I repeated  the same process with a windows-8 installation disk (iso), and I have  had no luck in repairing my computer. I've tried using restore-point and  have failed, since I needed to select the operating system, so I was  confused. I tried refreshing my files, but my windows drive was  locked..? I don't have a backup windows image or a backup usb. All of my  windows files are in tact. I know this, because I was able to mount the  files in linux and kind of virtually look through my windows partition I  suppose. I've used command prompt from my windows-8 recover usb to try  to fix windows by using commands such as bootrec /fixmbr; bootrec  /fixboot; bootrec /rebuildbcd; I tried other commands, but I cannot remember them at the moment. The commands are on my other usb which has kali linux on it.

---

### Post by oldfred on 2015-01-12
We primarily are Linux users, specifically Ubuntu. 
Many dual boot and can help some, but you may do better in a Windows forum, if the standard fixes are not working.
You do need to document what fixes you have run & what error messages you get.

 [http://www.eightforums.com/](http://www.eightforums.com/)

      
 Windows 8 UEFI fixes
[http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader](http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader)
Repair Windows 8 boot issues & repair CD or flash
[http://ubuntuforums.org/showthread.php?t=2105418](http://ubuntuforums.org/showthread.php?t=2105418)
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader](http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader)
Not free but they are good tools
[http://neosmart.net/blog/2013/download-efi-and-uefi-repair-cds-for-windows/](http://neosmart.net/blog/2013/download-efi-and-uefi-repair-cds-for-windows/)

---

### Post by LostFarmer on 2015-01-12
Might see your problem:  from your pastebin```
Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048     2,050,047     2,048,000 Data partition (Windows/Linux)
/dev/sda2       2,050,048     2,582,527       532,480 EFI System partition
/dev/sda3       2,582,528     4,630,527     2,048,000 Data partition (Windows/Linux)
/dev/sda4       4,630,528     4,892,671       262,144 Microsoft Reserved Partition (Windows)
/dev/sda5       4,892,672   832,569,343   827,676,672 EFI System partition
/dev/sda6     879,673,344   897,816,575    18,143,232 Data partition (Windows/Linux)
/dev/sda7     897,818,624   950,247,423    52,428,800 Data partition (Windows/Linux)
/dev/sda8     950,247,424   976,773,119    26,525,696 Data partition (Windows/Linux)
``` you have the wrong partition types on sda5 and sda3.  sda3 should be EFI hiddden and sda5 should be Data partition (Windows/Linux)


DO you have Kali Linux installed on sda6  (NTFS)?   does it boot ?  Did the install of Kali start your current problem ?

---

### Post by joseph45 on 2015-01-12
I tried installing linux from my usb. I put my computer into legacy mode and booted from my usb. I chose usb-persistence and linux booted. Then, I used the GUI menu to locate "install." I clicked "install." Then, a white screen appeared, and the installation program was running. I went through the steps of installing linux. I installed kali linux without grub and without lilo. Later on, I continued to try to install linux. I'm not sure when the problem appeared. I think I might have done something else to have messed up my windows installation, but I haven't had time to look for the link that I used to assist in my linux installation.

---

### Post by LostFarmer on 2015-01-12
Explain what happens when you try to boot WIn in EFI mode?   
Right now I suspect your main problem , sda5 is the wrong partition type (GUID).  
 Due to Win boots in EFI mode , I would NOT try installing linux in MBR (legacy) mode or on a ntfs partiton, just more problems are made.

---

### Post by oldfred on 2015-01-13
Moved to Other OS since not Ubuntu and mostly Windows.

Always use Windows to shrink the NTFS partition and reboot immediately so it can run chkdsk and repair for its new size. Using the installer to shrink Windows in some cases causes issues.

Always make a full backup of Windows & the efi partition. And a Windows repairCD.

       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by joseph45 on 2015-01-13
Boot configuration data is missing or corrupted. Here's some pictures :)[IMG]http://i1344.photobucket.com/albums/p644/Joseph_Austin_Gobert/IMG_20150113_170117_344_zpsd32da87c.jpg[/IMG][IMG]http://i1344.photobucket.com/albums/p644/Joseph_Austin_Gobert/IMG_20150113_170136_743_zpsb24b0e62.jpg[/IMG]

---

### Post by joseph45 on 2015-01-13
I tried adding another partition to put the boot data onto it but sadly, I got an error that said that it was unable to copy the fails. There are apparently multiple indistinguishable devices as well when I tried other commands.

---

### Post by LostFarmer on 2015-01-14
I will ask again :Explain what happens when you try to boot WIn8?

If no answer from you, then no help from me .

---

### Post by oldfred on 2015-01-14
There is no Linux partitions, they all are NTFS or FAT32, not ext4. So you never have installed Linux unless you attempted a wubi install which does not work with gpt partitioning or then any Windows 8 pre-installed system.

---

### Post by joseph45 on 2015-01-16
I managed to fix Windows! I had to completely recreate the EFI partition. I copied the boot files from my windows partition onto a newly created EFI partition. Thank-you for all of the help!

---


---
title: "Forcing System boot up - Solved"
date: 2019-10-13
forum: Windows
---

### Post by johncooool on 2019-10-13
I will start by saying that I do not have a technical problem. I am trying to find a solution for an idea that I have. I am a Microsoft Windows technical support person and have no idea on how to work with this platform.

I have posted the 1st part of the thread in 2 other forums 2 days ago and got zero replies. After doing a lot of research I came to the conclusion that there is a high chance of finding a solution here.

Here is the request:

I am trying to boot Windows 7 or 8.1 that is on my HDD from another disc like a USB flash drive. The idea is to not allow windows to boot up unless the particular USB drive is plugged in to redirect the boot process. It is like a type of security.

I installed Wondershare Live boot and created a USB boot disk which has a Grub menu. It works fine, however, I edited the boot menu in the BIOS to stop HDD boot up and that stopped the process from working. I get error messages like "read error" or "Couldn't find the first disk sector". So I assume that stopping HDD from booting blocks the 1st boot sector of the disk.

I tried to edit the Grub menu from info I found on the internet and none of them worked. 

I don't know if there is a way to bypass the BIOS restriction and to force boot up from the Grub menu.

The solution might be that I disable the boot process in a different way allowing the booting to occur only from the Grub menu.

Please don't suggest other security solutions. I want to learn this for expansion of knowledge.

The below link contains the post I posted in one of the other forums if anyone wants to take a look at it.

[https://windowsforum.com/threads/use-your-usb-stick-as-a-key-to-boot-your-windows-pc.246873/](https://windowsforum.com/threads/use-your-usb-stick-as-a-key-to-boot-your-windows-pc.246873/)

---

### Post by howefield on 2019-10-13
Thread moved to the "*Windows*" sub forum.

---

### Post by yancek on 2019-10-13
Post the menuentry you use in Grub to attempt to boot windows.  Also, post drive/partition information using the command: sudo fdisk -l (Lower Case Letter L in command)

I doubt that it will boot if you disable booting from the hard drive in the BIOS as Grub does not and never has directly booted windows the way it directly boots a Linux install.  It chainloads to the boot partition of windows where the boot files exist so without that access, it won't boot.

Windows 7 is generally a Legacy install using code in the MBR while windows 8 is generally a UEFI/GPT boot with boot files on the EFI partition as well as the system partition.  You obviously can install windows 8 on a Legacy (dos) drive rather than using UEFI/GPT.  

One thing you might do is to set the usb to first boot priority in the BIOS and then create a BIOS password so this setting cannot be changed unless the user has that password.  I'm not aware of any way to do exactly what you are looking for but someone else may have a suggestion.

---

### Post by johncooool on 2019-10-13
I have seen some videos on YouTube with windows booting from within Ubuntu O/S. So you are mistaken about your above comment. 

Of course there is a way to launch it from Grub menu. As I mentioned above. It works before I disable the boot. We just need to figure a way around it. It is not necessary to do it by disabling the HDD from booting in BIOS. There might another way which then can be started by the Grub menu.

I do not understand the code you placed randomly as I have no experience on this platform.

Here is one of the codes I tried, the rest are deleted. It would either give an error that that map table is empty or that it can't hook.

hiddenmenu
default 0
timeout 4
 
 
Title Load Microsoft Windows Win7
map (hd0) (hd1)
map (hd1) (hd0)
map --hook 
rootnoverify (hd0)
chainloader +1
 
title Reboot
reboot


title Back
chainloader /BOOTMGR

---

### Post by johncooool on 2019-10-13
I found a post from another forum were a person bypasses the BIOS to activate the CD-ROM. So I need something similar to that.

[https://msfn.org/board/topic/153330-unable-to-boot-any-bootable-cddvd-solved/page/3/](https://msfn.org/board/topic/153330-unable-to-boot-any-bootable-cddvd-solved/page/3/)

---

### Post by yancek on 2019-10-13
> I have seen some videos on YouTube with windows booting from within Ubuntu O/S. So you are mistaken about your above comment. 

No, I am not.  I imagine it is your limited knowledge of bootloading which is the problem.  I would suggest you do an online search 'chainloading windows from Grub' so you understand the difference in directly booting and chainloading.

> I do not understand the code you placed randomly as I have no experience on this platform.


What code?  Are you referring to the fdisk command as that is the only 'code' I posted?  That command has been around/used for 40 years and has been used on DOS and windows since the beginning and as I stated in my previous post, it is specifically used to list information on physical hard drives and partitions on them.

I'm not sure what "Wondershare" is as I have never heard of it prior to this post.  Is this windows software using Grub4Dos as the link you posted shows using it?

The menuentry you posted to boot windows from Grub4DOS (or Grub Legacy, whatever you have) is incorrect as it needs to be pointing to a partition on which the boot files reside rather than the drive as a whole.  Can't really give more specific information with the general information you have posted.  Good luck.

---

### Post by johncooool on 2019-10-13
Do you have any suggestions for me to try.

To write a code in the same context of what is written above?

---

### Post by QIII on 2019-10-13
Nobody is asking you to "write a code".  This is not a computer game.

Nobody asked you to "write code".  You are doing no programming or software development.

You were asked to issue commands in a terminal emulator.  This is exactly the same as a Windows technical support person might ask a Windows user to do after invoking ***cmd***.  

I would suggest that taking an antagonistic attitude towards a knowledgeable and technically proficient *volunteer* who, out of kindness to a newcomer, is trying to assist you might not be the best approach.

---

### Post by oldfred on 2019-10-13
If you want to understand how the old BIOS/MBR systems boot, this is one of the better links:
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.com/](http://www.multibooters.com/)

Of course since Microsoft required vendors to install Windows 8 in UEFI boot mode with gpt partitioning in 2012, most systems are UEFI. But a user can install even Windows 10 in BIOS boot mode.
UEFI [https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)

Since as shown in above BIOS boot, Windows uses boot flag to find partition with boot files, but grub uses os-prober and looks for the partition with the required Windows boot files and creates a chainload to the Windows PBR - partition boot sector to boot. It does not boot Windows directly.

Some examples:
Windows 7 entry with 100MB initial partition
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 2ae000d2e000a663
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

alternate to chainloader +1
ntldr /bootmgr 

Two changes were made to the commands in (3) versus (4).
The new command insmod ntldr was added.
The command chainloader +1 was replaced with ntldr ($root)/bootmgr
added insmod ntldr and change chainloader +1 to ntldr ($root)/bootmgr, and it works wonders!

the map command is often required if BIOS not booting same drive as Windows. Windows expects to be first in most cases, so the map switches the boot drive, so Windows still thinks it was the drive booted.

#If not hd0,1
menuentry "Windows 7" 
{
insmod ntfs
set root=(hd0,1)
drivemap -s (hd0) ($root)
ntldr /bootmgr
#or chainloader +1
}

---

### Post by johncooool on 2019-10-14
> **oldfred said:**
> If you want to understand how the old BIOS/MBR systems boot, this is one of the better links:
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.com/](http://www.multibooters.com/)

Of course since Microsoft required vendors to install Windows 8 in UEFI boot mode with gpt partitioning in 2012, most systems are UEFI. But a user can install even Windows 10 in BIOS boot mode.
UEFI [https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)

Since as shown in above BIOS boot, Windows uses boot flag to find partition with boot files, but grub uses os-prober and looks for the partition with the required Windows boot files and creates a chainload to the Windows PBR - partition boot sector to boot. It does not boot Windows directly.

Some examples:
Windows 7 entry with 100MB initial partition
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 2ae000d2e000a663
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

alternate to chainloader +1
ntldr /bootmgr 

Two changes were made to the commands in (3) versus (4).
The new command insmod ntldr was added.
The command chainloader +1 was replaced with ntldr ($root)/bootmgr
added insmod ntldr and change chainloader +1 to ntldr ($root)/bootmgr, and it works wonders!

the map command is often required if BIOS not booting same drive as Windows. Windows expects to be first in most cases, so the map switches the boot drive, so Windows still thinks it was the drive booted.

#If not hd0,1
menuentry "Windows 7" 
{
insmod ntfs
set root=(hd0,1)
drivemap -s (hd0) ($root)
ntldr /bootmgr
#or chainloader +1
}


It seems that we are getting closer and it seems that you have correct understanding of my request.

I tried your examples and none of them worked. I got  Error 8 (Kernel must be loaded before booting) with the last code that you game me.

Please give me more tips and more examples to try out.

WINDOWS 7 is installed on the 2nd partition because the 1st one is recovery partition. No UEFI on that device.

Thanks

---

### Post by oldfred on 2019-10-14
With multiple drives, I often have to manually edit boot stanza as I boot.
My hd0 may become hd1, hd1 then is hd2. But boot drive is always hd0, even if sdd or normally hd3 is used to boot.

May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by johncooool on 2019-10-15
> **oldfred said:**
> With multiple drives, I often have to manually edit boot stanza as I boot.
My hd0 may become hd1, hd1 then is hd2. But boot drive is always hd0, even if sdd or normally hd3 is used to boot.

May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

The problem is that I am working a system that is totally foreign to me. So it is a like bling person trying to see. I have no idea how to solve the problems I face with each error.

I tried running Rescatux to run the boot-info-script and I also tried running boot-repair.

In both cases, it would get to the 1st screen and then stop as if there is some compatibility issue.

I don't know if this is because the system is old and does not have UEFI or some other issue.

I tried searching for information that is related to my problems but could not find.

Do you have any more tips or ideas for me to try out?

Thanks

---

### Post by oldfred on 2019-10-15
If system is broken and even Boot-Repair will not run that is a totally different issue.

What error messages are you getting?

Run these:
sudo parted -l
lsblk -f

---

### Post by johncooool on 2019-10-15
> **oldfred said:**
> If system is broken and even Boot-Repair will not run that is a totally different issue.

What error messages are you getting?

Run these:
sudo parted -l
lsblk -f

Thanks for tip, I had Grub2win installed and it was blocking the 2 programs from working. I will try to complete your info from before.

---

### Post by johncooool on 2019-10-15
> **oldfred said:**
> If system is broken and even Boot-Repair will not run that is a totally different issue.

What error messages are you getting?

Run these:
sudo parted -l
lsblk -f

I am adding the below link which contains the report generated by the Boot-Repair software about my system while the HDD is disabled from booting from the BIOS.

Please check it and let me know if there is a way to get it to work.

[https://paste.ubuntu.com/p/BRPgYkRgKS/](https://paste.ubuntu.com/p/BRPgYkRgKS/)

---

### Post by johncooool on 2019-10-15
I don't know if I should run the repair. The PC boots normally as long as the HDD booting is enabled. So what would happen if I repaired it?

Any ideas?

---

### Post by TheFu on 2019-10-15
I don't see any Linux in that boot-info output.  Guess I don't understand the goal, since running Linux isn't it.

---

### Post by oldfred on 2019-10-15
Nothing really to repair.
Boot-Repair really is for repair of Linux systems. But with Windows in BIOS mode, it can install a generic Windows type boot loader.

It would install syslinux which is a Windows type boot loader assuming your Windows boot loader must not be working.
It also copies the boot files from sda1 to sda2 as many users do not know Windows has to have the boot partition to boot, and just delete it. Then they have no boot files. With copies in sda2 then that partition is also bootable, if boot flag is on it. Just a backup.

Windows installs the boot partition in the drive set as default in BIOS.
I have seen examples where users had sdb as default. Windows then put boot partition on sdb, but install (the c: drive) on sda. Then users installed Linux on sdb, erasing boot partition and then are not able to boot Windows.

Do not know details on where in BCD Windows has info on which drive to boot from. Old boot.ini with XP had that info on drive & partition.
Windows also does not let you install to USB external drives, so do not think you can have boot partition on a flash drive.
You might be able to remove boot flag and use grub to boot Windows as it just looks for boot files, not boot flag. But then any user with access could add boot flag.

---

### Post by johncooool on 2019-10-15
You are right. The boot partition is not C. it is the 1st one that is 400MB hidden partition.

The information that I found do deactivate "boot flag" is to make the partition inactive. So when I made it inactive the system stopped booting. Luckily I was able to reverse it from Wondershare as it has those tools.

I ran the Boot repair disk and it completed successfully then I enabled the HDD in the boot menu but the Grub menu commands that I tried did not work including the ones you gave me from before. The 1st one you gave is here below has some details about the size of the partition. Should I edit it further?

[COLOR=#000000]*Windows 7 entry with 100MB initial partition*[/COLOR]
[COLOR=#000000]*### BEGIN /etc/grub.d/30_os-prober ###*[/COLOR]
[COLOR=#000000]*menuentry "Windows 7 (loader) (on /dev/sda1)" {*[/COLOR]
[COLOR=#000000]*insmod ntfs*[/COLOR]
[COLOR=#000000]*set root=(hd0,1)*[/COLOR]
[COLOR=#000000]*search --no-floppy --fs-uuid --set 2ae000d2e000a663*[/COLOR]
[COLOR=#000000]*chainloader +1*[/COLOR]
[COLOR=#000000]*}*[/COLOR]
[COLOR=#000000]*### END /etc/grub.d/30_os-prober ###*[/COLOR]

[COLOR=#000000]*alternate to chainloader +1*[/COLOR]
[COLOR=#000000][I]ntldr /bootmgr 

Thanks[/I][/COLOR]

---

### Post by johncooool on 2019-10-15
The updated link below shows the installation on the MBR that I did with Boot-repair-Disk

[https://paste.ubuntu.com/p/RqWFNmhxqm/](https://paste.ubuntu.com/p/RqWFNmhxqm/)

It seems that it is installed on [COLOR=#000000]sdb1.

I made a mistake. I think SDB1 is the USB stick I am using to run the program.[/COLOR]

---

### Post by oldfred on 2019-10-15
Are you using the correct UUID in Boot stanza. The example just has some old UUID.

You need to be using this:
```
Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        [COLOR=#ff0000]14283BD5283BB518[/COLOR]                       ntfs       SYSTEM
```

If booting another drive, not sure if you need drivemap command or not. You may need to experiment.

[https://www.gnu.org/software/grub/manual/grub/html_node/drivemap.html](https://www.gnu.org/software/grub/manual/grub/html_node/drivemap.html)

---

### Post by johncooool on 2019-10-16
I lack the knowledge to work at the command level. All my support was without using it in the past.

It is like being able to read another language because you know the letters but none of it makes any sense.

It is too bad that you are not here with me to show me the way as I know you could find a solution easily.

Nothing that I try seems to work and that is due to lack of knowledge in the matter.

I think the only way for me to solve it is to copy someones else work on the exact request but I can't find.

Do you think you could right 10 possible codes that you would think should work based on the info that you have already. I can provide more if you require it.

Thanks

---

### Post by johncooool on 2019-10-16
Project has been completed!

I installed Grub from the below link onto a USB and It was able to see the OS and it booted.

HDD bootup is enabled from BIOS.

Boot partition is inactive.

So now system only boots if the USB is flash disk is plugged in and I choose the boot for windows.

The link for the Grub I installed for this project is.

[https://sourceforge.net/projects/supergrub2/](https://sourceforge.net/projects/supergrub2/)

It works only when the Generic MBR is installed from the Boot-Repair-Disk.

---

### Post by johncooool on 2020-08-04
A new update on the above method solution to boot windows only if USB is plugged in.

Windows Hibernate will not work anymore because the Windows partition is made in-active in order for that to work....

Windows Sleep still works. 

They are not the same....

---

### Post by johncooool on 2020-08-04
New Update!

Hibernate will not work because volume is set to inactive.

Sleep still works but it is not the same thing.

---

### Post by johncooool on 2020-08-12
> **oldfred said:**
> Are you using the correct UUID in Boot stanza. The example just has some old UUID.

You need to be using this:
```
Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        [COLOR=#ff0000]14283BD5283BB518[/COLOR]                       ntfs       SYSTEM
```

If booting another drive, not sure if you need drivemap command or not. You may need to experiment.

[https://www.gnu.org/software/grub/manual/grub/html_node/drivemap.html](https://www.gnu.org/software/grub/manual/grub/html_node/drivemap.html)

Your solution did work at the end on Win 7 which is running on an old Laptop using legacy support BIOS.

I am unable to get it to work on a newer Laptop running Win8.1 on UEFI BIOS settings.

Can you give some tips here too?

---

### Post by oldfred on 2020-08-12
Start a new thread with details including make/model & video card of newer system.
And what version of Ubuntu & Windows.
And post link to summary report.
Be sure to include computer & issue in title.
If I do not see it in 24 hrs, you can PM me link to thread, but I see most threads that I may be able to help on.

---

### Post by johncooool on 2020-08-12
I am the thread starter in this one and it is the same issue and you are the one that solved it last time. It is just a different O/S.


I can add details here rather than starting a new thread.

Is that ok with you? Or do you insist on starting a new one?

---

### Post by oldfred on 2020-08-12
If a different system, I prefer a new thread.
Plus this thread is older, things change.

---

### Post by johncooool on 2020-08-12
Ok No problem.

For other visitors. you can find it working well on legacy support Motherboards with the below solution.

______________________________________


[LIST]
[*][INDENT]I installed Grub from the below link onto a USB and It was able to see the OS and it booted normally after selecting it from the Grub menu.

HDD bootup is enabled from BIOS.

Boot partition is inactive. This can be done from Diskpart in CMD while logged in. But do not reboot without the USB being ready with Grub on it. It will show that operating system is missing at which point you can continue to booting to the O/S from the USB Grub menu.

So now system only boots if the USB is flash disk is plugged in and I choose the boot for windows.

The link for the Grub I installed for this project is.

[https://sourceforge.net/projects/supergrub2/](https://sourceforge.net/projects/supergrub2/)

It works only when the Generic MBR is installed from the Boot-Repair-Disk. SO after booting into Boot-repair disk just run a repair and it will install the needed files for this solution to work then exit the program.

Download Boot-Repair-Disk from

[https://sourceforge.net/p/boot-repair-cd/home/Home/](https://sourceforge.net/p/boot-repair-cd/home/Home/)

You can also use the boot repair disk to get it back to working normally. Then the Win O/S will go back to booting normally. So if you can't get this solution working then just boot from boot repair disk and do a repair and restart the system and Windows will load normally again.

Use Rufus to create the 2 USB flash disk for the Grub menu and the Boot repair disk. It sometimes needs to connect to the internet to add needed files. 

Link is: [https://rufus.ie/](https://rufus.ie/)

Important notice![/INDENT]
[INDENT]
Windows Hibernate will not work anymore because the Windows partition is made in-active in order for that to work....[/INDENT]

[*][INDENT]
Windows Sleep still works. 
[/INDENT]
[/LIST]

---

### Post by johncooool on 2020-09-19
For UEFI please check the other thread I started on this forum.

[https://ubuntuforums.org/showthread.php?t=2448722](https://ubuntuforums.org/showthread.php?t=2448722)

Upgrading to another version of Windows from within Windows will not work because the disk is marked as inactive. To be able to upgrade boot from the boot repair disk (that is included in this solution) and run the repair one time and then reboot into windows and proceed with the upgrade.

The issue could also occur when doing a repair. There are repairs that are run from within Windows. That will reinstall it. If there is an issue then change the disk settings back to default like is mentioned here above.

---


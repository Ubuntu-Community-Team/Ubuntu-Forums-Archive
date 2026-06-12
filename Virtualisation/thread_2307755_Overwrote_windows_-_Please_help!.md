---
title: "Overwrote windows - Please help!"
date: 2015-12-28
forum: Virtualisation
---

### Post by robertt3 on 2015-12-28
Hello, I've been trying for weeks to get Windows back but nothing seems to work.
I've downloaded multiple ISO's, & now I bought a key for Windows 7 ultimate to try that.
I've mounted it on to a USB & I try to boot it from BIOS but it just enters a GNU Grub screen that has Linux & advanced options.

The ISO's gave an error saying winload.exe is missing. Any help would be really great as I really need to get windows before Friday.
Thanks!

---

### Post by dragonfly41 on 2015-12-28
When in Ubuntu I would try running boot-repair.  And take a note of the pastebin link.

Also read here ... [https://neosmart.net/wiki/winload-exe-missing-corrupt/](https://neosmart.net/wiki/winload-exe-missing-corrupt/)

---

### Post by robertt3 on 2015-12-28
Thanks for the reply.
Ive tried boot repair multiple times with no success.

---

### Post by oldfred on 2015-12-28
Boot-Repair may not fix it, but the link to the summary report lets us suggest the best way to fix it or at least see what issues may be.
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by ajgreeny on 2015-12-28
You could help us all help you by showing the pastebin link that running Boot-Repair's **Boot-Info-script** gives you, as it may tell us something that you do not recognise as a problem. Running the default repair does not always manage to get everything running again if, f0or example, there are problems with UEFI vs MBR/BIOS, or you are missing the required partitions for booting the system.

Are you sure that Win 7 has been overwritten, or is still there but impossible to boot?  The Boot-Info-script report will tell us all of that information.

Did this all start after you installed Ubuntu in dual boot with an existing Win 7 or has the problem just appeared out of the blue at some time?

EDIT:
Ninja'd by oldfred!  
@ robertt3: You will certainly be in good safe hands with help from oldfred with this problem.
Good luck!

---

### Post by grahammechanical on 2015-12-28
> I've mounted it on to a USB & I try to boot it from BIOS but it just  enters a GNU Grub screen that has Linux & advanced options.

To load any OS from a USB mmeory stick or DVD disc we often need to enter the BIOS & change a setting. The BIOS will most likely see the USB stick as an external USB hard drive. So, it may be under the hard drive section that you make the change to set the motherboard to boot from the USB stick. That is what I have to do with my BIOS motherboard.

Regards.

---

### Post by HermanAB on 2015-12-28
Howdy,

First you need to figure out what you actually did and what you actually want.  Did you really install Ubuntu on the whole disk and Windows is completely gone, or did Ubuntu repartition the disk and Windows is still there but not working?  

If Ubuntu is working properly, then you could consider installing Virtual box and making a virtual machine for Windows, since then you have the best of both worlds and can run Windows in a window in Ubuntu.

If you really want to blow everything away (again) and install Windows from scratch, then you have to overwrite the first bit of the disk with zeros, since Windows is stupid and doesn't know what to do with Linux partitions and file systems.  You can do that with Data Definition (dd) from the Ubuntu install disk.

---

### Post by robertt3 on 2015-12-28
I've tried running Windows 7, 10 & 8 on VirtualBox but it always gives an error saying winload.exe isn't there
Here's my bootrepair summary: [http://paste2.org/1PYk2tIK](http://paste2.org/1PYk2tIK)

---

### Post by oldfred on 2015-12-28
You could have mentioned that it was Virtual-box in first post.

I do not know about Virtual-box and how Windows installs.

Typical dual boot Windows has a 100MB boot partition with bootmgr & /boot/BCD and then main install or c: with winload.exe.

---

### Post by howefield on 2015-12-28
Thread moved to the "*Virtualisation*" forum.

---

### Post by robertt3 on 2015-12-28
Thanks. @oldfred I'm trying to remove Ubuntu on my PC & reinstall windows but it's not working so I decided to try VirtualBox as I needed to use windows before Friday but none of them work.

---

### Post by oldfred on 2015-12-28
It looks like you still have sda1 100MB which normally is a Windows boot partition. But you need boot flag on it. And best to have another primary partition for Windows.
Windows will also install to one primary NTFS formatted partition with the boot flag. And better to have primary partition on drive before the extended partition.
Windows installs also will install its boot loader and has been known to delete or "forget" to write Linux formatted logical partitions on installs & major updates. Partition is still there with all its data, but needs to be added back into partition table.
After creating NTFS primary partition, or any other changes back up partition table structure.

       First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt
sudo sfdisk -d /dev/sda > parts_sda.txt

---

### Post by robertt3 on 2015-12-29
I'm sort of new to this whole thing so I kind of didn't understand a single part of what you said, but I changed the sda1 partition flag to boot. Not sure what I have to do next. I have windows 10 on a USB that I can boot

---

### Post by oldfred on 2015-12-29
Create a large NTFS formatted partition with gparted from Ubuntu live installer or gparted live ISO. Windows does not correctly see Linux partitions. If you just want to totally erase Ubuntu and have any data backed up, Windows may work to erase it totally.

If newer system with UEFI, how you boot Windows installer UEFI or BIOS is then how it installs. But if you change from BIOS to UEFI it will also convert to gpt and that erases entire hard drive.

---

### Post by robertt3 on 2015-12-30
Sadly I do not have an Ubuntu live installer or gparted live ISo.
Is there any way to just reinstall Windows manually without having to use a gparted or ubuntu LiveCD?

---

### Post by oldfred on 2015-12-30
You should be able to use Windows installer to totally erase system. 
But it does not correctly see Linux partitions, so often has issues. I have not used Windows to repartition a drive and have not installed Windows since XP in 2006. 

 [http://www.tenforums.com/](http://www.tenforums.com/)
[http://www.eightforums.com/](http://www.eightforums.com/)
[http://superuser.com/](http://superuser.com/)

---


---
title: "Server 8.10 - Dell PowerEdge 1400 Install"
date: 2009-02-08
forum: Server Platforms
---

### Post by beatgr on 2009-02-08
Installation of Ubuntu Server 8.10
> 
Dell PowerEdge 1400
(earlier motherboard, no Pentium III Tualatin support)
800 MHz, 133 MHz procesor with 256K L2 cache
2,024 Mb memory

Adaptec AIC-7899 Ultra 160/m SCSI Build 25309(on motherboard)
Channel 0: 4 SCSI hard drives -- NO RAID
Channel 1: Dell PV-100T DDS4 (Tape Drive)
*Tape drive: Archive Python 06408-XXX*
*There is NO firmware update for the motherboard based AIC-7899*

Network - Ethernet (2 ports)
Intel Pro/100 (on motherboard)
Intel Pro/100+ Server Adapter (PILA8470B): DRAC 767 card
*Dell Remote Assistance Card v 7.0*


Thanks to earlier posts, suggestions and answers from:
rjromero10;  movingover; Albinootje

1) This retired server previously ran Windows NT 4.0
2) Download from Dell website ANY BIOS updates for your PowerEdge computer.
A09 is the latest BIOS version for the PE 1400.
Format a blank floppy and copy the BIOS/boot image from the Dell download.
3) Reboot PowerEdge, booting server from the floppy drive.  Run the BIOS update, per Dell instructions.

4) At this point, I installed a copy of Windows 2000 Server SP4, on drive #2 of the 4 drives installed.  *I changed the boot order, so that Drive #2 was first hard drive to boot during this process.* After completing hardware driver and security updates (Microsoft Update), I am ready to install Ubuntu.

5) Configure the boot order so that Drive #1 (PowerEdge) is the first hard drive to boot.  This will be the target drive for the Ubuntu installation.
6) Install Ubuntu Server 8.10 from the LiveCD -- per instructions.  I selected the *Guided installation* for the hard drive partitioning (Selection 2, as I remember).
7) When the Ubuntu install tries to "come up" the first time, you will get the **busybox** - the built-in shell.  
Type *exit*, the server will complete the boot process and provide you with a command prompt, such as: username@server:"$

The problem is with this file:  /boot/grub/menu.lst

THE FIX
In menu.lst file, "rootdelay=60" needs to be inserted in the menu selection lines that look similar to this:
>  
/boot/vmlinuz-2.6.27-7-server root=UUID=492ac531-c353-xxxx-xxxx-xxxxxxxxd913 ro quiet splash
I had 2 such lines in my file, (Ubuntu and Ubuntu recovery mode)

The modified line will look like this:
> 
/boot/vmlinuz-2.6.27-7-server root=UUID=492ac531-c353-xxxx-xxxx-xxxxxxxxd913 ro rootdelay=60 quiet splash

The first command line crates a copy of the file.  
After the last character "`" ... I had to type an additional space (spacebar) for the command to properly execute.
The second command line uses your text editor (nano, mousepad, gkedit, emacs, vi) to modify the lines in menu.lst as shown above.
> 
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.`date +~%b-%d-%Y~%T`
sudo nano /boot/grub/menu.lst
Save the file and close your editor.

Now update the grub!
> 
sudo update-grub

Before rebooting the system, you can run update. 
> sudo apt-get update

NOTE: I still have one notice during the boot process to research.  Appears to be associated with the Dell Remote Access Card (DRAC)
> 
[0.616031] .. MP-BIOS BUG: 8254 Timer not connected to IO-APIC


BTW, if you desire the GUI interface for the 8.10 Server, 
rather than the command line interface .. you can run:
> 
sudo apt-get install ubuntu-desktop
The desktop install took almost 20 minutes for my system.

Good luck!

---


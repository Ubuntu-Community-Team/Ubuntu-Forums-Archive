---
title: "Quicken 2007 on WinXP VirtualBox"
date: 2008-10-09
forum: Virtualisation
---

### Post by lipinski on 2008-10-09
I have been able to successfully install Windows XP running within VirtualBox.  I then installed Quicken Home & Business 2007 and upgraded to the latest Quicken patch.  So far, so good.

I have my Quicken Data in a VirtualBox Shared Folder, and manually load/open the Data file from within Quicken via File->Open and opening the file.  However, Quicken will not open this file by default on subsequent Quicken startups.  Every time I start Quicken, I get the "Get Started with Quicken 2007" dialog box, asking me to Select data file.  I can select the file from this menu, and all's well as well - except that I get prompted again on next startup.  This didn't happen on native Win XP.  

The above issue is an annoyance that I can live with.  My next issue is regarding Backup from within Quicken.  When I attempt to perform a backup from within Quicken, It constantly fails stating "Unable to access disk in drive U:. Please make sure the drive is ready and the disk is not write-protected.  If backing up to a CD, make sure the CD is not full.  Do you want to try Again?"

It constantly fails.  I get the same exact error condition if I try to backup to the C: Drive which based on a VBox image (.vdi).

I don't think it is a permissions problem within Quicken because I can create subfolders within the Quick Backup dialog for selecting the backup folder - so I have permissions to create a folder.

Does anyone have Quicken running flawlessly (well, as flawless as Quicken can be) under VirtualBox?

---

### Post by m_j_lyons on 2008-10-09
I'm using a similar setup - I have Ubuntu 8.04 on the desktop and use WinXP in a VM - I was using OpenBox...now I'm using VMWare workstation/player.  

I let Quicken save the data file in the normal Windows directory tree but do my backups to a network folder (which is mapped in XP as my Z drive).  

My biggest issue with this setup is that I can't use my printer/scanner from within XP.  I can scan in Linux and move to a shared folder and then pull files into Quicken...but I can't do it from Quicken directly (crashes virtual machine WinXP when ever I try to access the networked all-in-one scanner/printer.)

All in all it's very functional.  I'm trying to find a way to access that VM from anywhere on my home network...VNC works, but it's clunky.  I'd rather have direct access to the VM desktop.

Cheers,

---

### Post by lipinski on 2008-10-09
> **m_j_lyons said:**
> I'm using a similar setup - I have Ubuntu 8.04 on the desktop and use WinXP in a VM - I was using OpenBox...now I'm using VMWare workstation/player.  

I let Quicken save the data file in the normal Windows directory tree but do my backups to a network folder (which is mapped in XP as my Z drive). 

So, no problems with save or backup, hunh?  Don't know if VMWare vs VirtualBox could be contributing to my issues.  But, I am having issues with Backup both to a shared (via VirtualBox Guest Additions) as well as to the normal Windows directory tree (VirtualBox Virtual Disk .vdi image). 

> **m_j_lyons said:**
> 
My biggest issue with this setup is that I can't use my printer/scanner from within XP.  I can scan in Linux and move to a shared folder and then pull files into Quicken...but I can't do it from Quicken directly (crashes virtual machine WinXP when ever I try to access the networked all-in-one scanner/printer.)

Can't help here - I haven't tried printing or scanning from my WinXP VM.  I had quite a bit of trouble getting my HP PSC2210 (All-In-One) working with Ubuntu in general for scanning.  I just use it directly on Ubuntu and not on WinXP.  Trying to limit my WinXP usage to Quicken only.

> **m_j_lyons said:**
> 
All in all it's very functional.  I'm trying to find a way to access that VM from anywhere on my home network...VNC works, but it's clunky.  I'd rather have direct access to the VM desktop.

VNC is probably the most straightforward option, but agree - the most clunky.  Windows Remote Desktop is another option, but essentially just a proprietary Windows-based VNC.  Depends on what you are running on the PCs you want to connect from.  If it is a Linux-based system, you could investigating ssh-ing to your Ubuntu desktop, exporting your display (to your remote system), and starting VMWare.  If your remote PC is a Windows-based system, you will need some type of X Server, i.e., Hummingbird Exceed, or similar.

---


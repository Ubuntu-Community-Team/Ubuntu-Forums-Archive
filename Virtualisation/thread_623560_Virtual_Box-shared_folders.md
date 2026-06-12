---
title: "Virtual Box-shared folders"
date: 2007-11-26
forum: Virtualisation
---

### Post by jammrk on 2007-11-26
just wanted to make the masses aware of an issue I faced regarding virtualbox and guest addition.  I used a guest addition package from the google project page instead of going about it the normal way:
4.2.1.1 Mounting the Additions ISO &#64257;le
In the “Devices” menu in the virtual machine’s menu bar, VirtualBox has a handy menu
item named “Install guest additions”, which will automatically bring up the Additions
in your VM window.
   If you prefer to mount the additions manually, you can perform the following steps:
    1. Start the virtual machine where you have installed a Windows guest operating
       system.
    2. Select “Mount CD/DVD-ROM” from the “Devices” menu in the virtual machine’s
       menu bar and then “CD/DVD-ROM image”. This brings up the Virtual Disk Man-
       ager described in chapter 3.5, The Virtual Disk Manager, page 34.
    3. In the Virtual Disk Manager, press the “Add” button and browse your host &#64257;le
       system for the VBoxGuestAdditions.iso &#64257;le:
          • On a Windows host, you can &#64257;nd this &#64257;le in the VirtualBox installation
            directory (usually under C:\Program files\innotek VirtualBox).
          • On a Linux host, you can &#64257;nd this &#64257;le in the additions folder under where
            you installed VirtualBox (normally /opt/VirtualBox-1.5.2).
    4. Back in the Virtual Disk Manager, select that ISO &#64257;le and press the “Select” but-
       ton. This will mount the ISO &#64257;le and present it to your Windows guest as a
       CD-ROM.
4.2.1.2 Running the installer
Unless you have the Autostart feature disabled in your Windows guest, Windows will
now autostart the VirtualBox Guest Additions installation program from the Additions
ISO. If the Autostart feature has been turned off, choose setup.exe from the CD/DVD
drive inside the guest to start the installer.
   The installer will add several device drivers to the Windows driver database and
then invoke the hardware detection wizard.
   Depending on your con&#64257;guration, it might display warnings that the drivers are
not digitally signed. You must con&#64257;rm these in order to continue the installation and
properly install the Additions.
   After installation, reboot your guest operating system to activate the Additions. **(taked from vbox user manual)**
It way very convenient, it was a windows executable, it installed without error, I had seamless desktop, full-screen etc... However I was unable to access my shared folder. In case you dont know how here is the process for windows guest:
• In a Windows guest, starting with VirtualBox 1.5.0, shared folders are
  browseable and are therefore visible in Windows Explorer. So, to attach the
  host’s shared folder to your Windows guest, open Windows Explorer and look
  for it under “My Networking Places” -> “Entire Network” -> “VirtualBox Shared
  Folders”. By right-clicking on a shared folder and selecting “Map network drive”
  from the menu that pops up, you can assign a drive letter to that shared folder.
  Alternatively, on the Windows command line, use the following:
  net use x: \\vboxsvr\sharename
  While vboxsvr is a &#64257;xed name (note that vboxsrv would also work), replace
  “x:“ with the drive letter that you want to use for the share, and sharename
  with the share name speci&#64257;ed with VBoxManage.** (taken from vbox manual)**
Then it occurred to me that might be I should try to install the addition the normal way, I removed the previous version (control panel-> add/remove program...).  As it turns out that solved the problem. Sorry for the length of this post, but I just wanted to pass that on. 
vbox manual can be downloaded here:
[http://www.virtualbox.org/download/UserManual.pdf](http://www.virtualbox.org/download/UserManual.pdf) (I included the link location, so you can just use you favorite downloader.  if you are wondering how, in my case the command would be "wget http://www.virtualbox.org/download/UserManual.pdf"

Jammrk

---

### Post by Moonfrost on 2007-12-14
Hi, I tried to open the Virtual Box shared folder in my guest Windows XP and every time I try to open it or something the blue screen of death appears every time saying the usual thing like if it's a hardware issue or whatever contact your hardware manufacturer blah blah blah...do you have any idea what might be causing this? thanks.

---

### Post by Orfintain on 2008-01-02
same issue as moonfrost ,

---


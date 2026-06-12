---
title: "Coming to Linux, Ubuntu for the first time"
date: 2019-01-30
forum: Ubuntu, Linux and OS Chat
---

### Post by franky12 on 2019-01-30
I recently installed Ubuntu 18.04 on an HP 250 G1 laptop and want to become a Linux user. I have a couple of questions:
  
1- Does Linux generally or Ubuntu in particular need installing  device drivers like Windows? If so how to install proper drivers for my  Ubuntu, please?

  2- I know I have some free space. How to find and format it as a new partition?
  3- Which is better: installing apps through the Ubuntu Software app or Terminal?
  4- Do I essentially need some book/tutorial to read to know how to work with Ubuntu well? If so what?
  5- What common apps/programs do I need to install for the time being to start working on Ubuntu?

---

### Post by oldfred on 2019-01-30
You should update UEFI from HP, and if you added an SSD, update firmware for it.

Most drivers are included. Only if newer nVidia video or some WiFi chips may need you to download and install drivers.
Installer is also a live system, best to test in live mode to see how it works. Often better to install & initially configure with hard wired Internet.
Live installer will not be as fast as full install as flash drive & USB ports are not as quick as Internal drives and SATA ports.

If dual booting with Windows use Windows to shrink your NTFS partition. But do not shrink too much, NTFS likes 30% free. At 10% you just about cannot do a defrag as no working room. 
Ubuntu installer wants or will create a / (root) partition that is ext4 formatted. You cannot do that from Windows. I prefer to use gparted in advance, but you can do that from installer.
Most instructions are now older and refer to a swap partition. New versions of Ubuntu use swap file, so no swap partition is required.
If UEFI install, it wants an ESP - efi system partition. But if Windows is UEFI, you already have one, do not create another. And if Windows is UEFI, you want to install Ubuntu in UEFI mode. How you boot install media, is then how it installs.

In my old XP back in 2006, I changed to Firefox, Thunderbird & Openoffice (now LibreOffice fork is standard). Those applications were the same in Linux and most of what I use.

I prefer to install synaptic, as it explains more about software, and gives exact name. If using terminal, you need exact name. For example grub. Very old installs used grub which now is called grub legacy and is only for BIOS boot. New installs use grub2, but its filename is grub-pc for BIOS and grub-efi-amd64 for UEFI 64 bit systems.

Many default apps are already included. Best starting out to only install from Ubuntu repository.

       A master thread on learning/books/terminal/bash/Linux etc
Linux Command Line Learning Resources - cortman
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)
[http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108)
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux)

For general UEFI install instructions, see link in my signature below. A lot of info & many links. 

Vendors systems are very similar across many models, so these may help for HP. And Windows 8 or 10 are very similar and recent installs of Ubuntu are very similar, just newest has more updates, but install procedures are essentially the same.
      
 HP Envy 17 - 18.04.1 works See post #3
[https://ubuntuforums.org/showthread.php?t=2392797](https://ubuntuforums.org/showthread.php?t=2392797)
HP Pavillion X360 13-a220nw
[https://ubuntuforums.org/showthread.php?t=2359510](https://ubuntuforums.org/showthread.php?t=2359510) & 
[URL="https://ubuntuforums.org/showthread.php?t=2407615"]https://ubuntuforums.org/showthread.php?t=2407615
      [/URL]
 Some HP will not boot a flash drive that is gpt partitioned. Some only boot from the USB2 port not USB3 ports.
[http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260](http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260) 
    [URL="https://ubuntuforums.org/showthread.php?t=2407615"]

      [/URL] Also link on how to create a  bootable DVD or USB flash drive, using Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)
Direct link to downloads page, most want  ubuntu-18.04-desktop-amd64.iso
[http://releases.ubuntu.com/18.04/](http://releases.ubuntu.com/18.04/)

---

### Post by Holger_Gehrke on 2019-01-30
Welcome to Ubuntu and to the forum!


[LIST=1]
[*]Drivers for most usual hardware are included with the kernel. So unless you've got some very unusual hardware, you won't have to worry about downloading and installing drivers. You might have to configure some drivers if the automatic configuration process misdetects something, but even that is unusual. The one exception to those rules are graphics drivers for NVidia Graphics boards, but even in that situation there's a tool to download and install the drivers.
[*]gparted - probably called 'Disks' in the menu - is probably the easiest tool for that for a beginner.
[*]If you know exactly - down to the spelling and capitalization of the package-names - what you want to install, than the terminal is faster by an order of magnitude. If you want to browse a selection of programs, than the 'Software'-Application is more useful. Different tools for different situations.
[*]The Basics of working in the graphical environment are quite easy to discover on your own, but there's lots of details that can make things easier and better. There are links to the Ubuntu documentation, the Ubuntu Wiki and the Community Wiki in the menu at the bottom of the orange bar at the top of this page. For working with the command line a good book is definitely advisable. I'm partial to 'The Linux Command Line' by William Shotts ([http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)), but there are lots (and lots and lots ..) of others.
[*]No way to tell what tools you'll need without knowing what you want or need to do. If you know a program which does what you want but isn't available for Ubuntu or generally for Linux, [http://alternativeto.net](http://alternativeto.net) is a good resource to find programs which do the same or similar things that are available.
[/LIST]

Holger

---

### Post by Autodave on 2019-01-30
Ubuntu is the fanciest desktop.  Xubuntu not quite as fancy.  The reason for me saying this is that that machine might be a bit quicker on Xubuntu since Xubuntu doesn't use as much resources as Ubuntu.  Both use the same kernel and have all the same software that can be installed.

If you live where it is legal, you'll want to install the *Ubuntu or Xubuntu restricted extras.  *These are available in the Software center. These will allow you to better see online videos and other things.

Libre Office is a great replacement for MS Office and will allow you to save files, spreadsheets, etc. in MS formats.

---

### Post by wildmanne39 on 2019-01-30
Hello and welcome to the forum, when you actually install Ubuntu or try to if you need assistance please start a thread, one for each issue in the appropriate sub-forum so you can get the help you need.

*Thread moved to **Ubuntu, Linux and OS Chat a more appropriate sub-forum**.*

---

### Post by Skaperen on 2019-02-02
> **Holger_Gehrke said:**
> Welcome to Ubuntu and to the forum!
[LIST=1]
[*]If you know exactly - down to the spelling and capitalization of the package-names - what you want to install, than the terminal is faster by an order of magnitude. If you want to browse a selection of programs, than the 'Software'-Application is more useful. Different tools for different situations.
[/LIST]

Holger

All Ubuntu package names are in lower cases. i don't know if it is possible to have package names with any letters in upper case.  if it is possible then this would only happen to you if you added a weird private repository to your repository sources list.

one thing you will learn about Linux is the matching of letters in nearly all situations requires that case of the letters also match. Microsoft Windows compares text in virtually all situations by ignoring the case.

---


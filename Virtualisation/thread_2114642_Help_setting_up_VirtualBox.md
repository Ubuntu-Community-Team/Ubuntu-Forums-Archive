---
title: "Help setting up VirtualBox"
date: 2013-02-10
forum: Virtualisation
---

### Post by AllenMc on 2013-02-10
I am running Windows 7 and put Ubuntu 12.10 on my computer. I want to be able to switch between the 2 with out having to reboot and also be able to access some files saved in Windows from Ubuntu and the other way around. I was told VirtualBox would be the way to do this. I installed it from here [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads) and set it up the best I could from the instructions in the installer and what I read online. But I cant figure out how to switch from one OS to the other with out rebooting or how to share files.

For sharing files, some things I read said something about having to set up part of virtualBox on the guest OS, so do I need to reboot and also download it on Ubuntu for any of this to work?

Could someone please either give me some simple instructions on how to get both of these things to work or tell me somewhere that has some simple clearer instructions because what I have found so far was not very clear to me on what I needed to do. 

Also when I click start in virtualBox in Windows for my Ubuntu system I get "FATAL: No bootable medium found! System halted." which clearly is part of the problem I just don't know what it means. 

Thank you!

---

### Post by black3agl3 on 2013-02-10
I think you misunderstood the use of VirtualBox. It is used to run an OS within another OS. Say you have windows. You install VirtualBox on windows. Within this VirtualBox, you can run another OS. Say Ubuntu.

How did you actually install ubuntu on your pc?

---

### Post by AllenMc on 2013-02-10
Oo yeah it does seem like I might have misunderstood. So it wouldn't actually be like I was fully using the other OS? But more like using it in a window in my other OS? Like say using Ubuntu in a window in Windows?

I installed wubi Ubuntu (I'm not sure if there are any other versions than wubi) by going here [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) then acctually installing it from here [http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer)

---

### Post by NM5TF on 2013-02-10
> **AllenMc said:**
> Oo yeah it does seem like I might have misunderstood. So it wouldn't actually be like I was fully using the other OS? But more like using it in a window in my other OS? Like say using Ubuntu in a window in Windows?

I installed wubi Ubuntu (I'm not sure if there are any other versions than wubi) by going here [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) then acctually installing it from here [http://www.ubuntu.com/download/deskt...dows-installer](http://www.ubuntu.com/download/deskt...dows-installer)

I use VB to run WIN XP inside Ubuntu...think of it as having a little computer running WIN inside your computer...or vice versa
in your case....don't think you can just call Ubuntu or Win 7 without rebooting in your case...

to do what you are wanting to do, you will need to delete Ubuntu
from your system...

then install Ubuntu into VB and load it that way...it will have all the functionality of a clean install of Ubuntu....

Tommy

---

### Post by AllenMc on 2013-02-10
Oh ok. Well I guess I can be ok with having to reboot my computer to change to a different OS but is there a way for me to be able to share folders/files between them? Not necessarily all of them but at least some folders or files I can specify?

---

### Post by SeijiSensei on 2013-02-10
WUBI itself is a type of virtual machine, but VirtualBox is a much better alternative.

First, download and install the VirtualBox file for Windows at [http://www.virtualbox.org/](http://www.virtualbox.org/).  Then download the Ubuntu 12.04 CD image at [http://releases.ubuntu.com/12.04.1/](http://releases.ubuntu.com/12.04.1/).  Use the regular desktop CD for now even if you think you have a 64-bit machine.  Put the downloaded Ubuntu ISO image somewhere convenient on your desktop.

Now open VirtualBox from the Windows menu and click New.  It will walk you through the process of setting up a virtual machine.  I'd allocate at least 768 MB for Ubuntu if you have 2 GB of memory; on a 4 GB machine give it a full gigabyte.  Allocate at least 10 GB of disk space for the virtual machine.  VB only uses what it needs, so give it some room for future growth.

The installer will ask you where the operating system disk is to be installed.  Follow the steps to point to the Ubuntu ISO you just downloaded.  You'll see Ubuntu boot in a window; choose install and follow the steps.  Tell Ubuntu to use all the disk when it asks.

---

### Post by wildmanne39 on 2013-02-10
*Thread moved to **Virtualisation**.*

---

### Post by black3agl3 on 2013-02-10
> **AllenMc said:**
> Oh ok. Well I guess I can be ok with having to reboot my computer to change to a different OS but is there a way for me to be able to share folders/files between them? 

You can share files between them. Create at least three separate partitions on your hard disk. Install windows on one of them. Ubuntu on another. The last one you use to keep your documents on it. That's what I do.
Though i'm not really sure what you mean by: > Not necessarily all of them but at least some folders or files I can specify?Through my suggestion, folders you do not want to share, you simply do not put on the "sharing" partition.

If that does not suit you, you might consider Dropbox (or Ubuntu One) if your internet connection is really fast.
------------
Many people are suggesting VirtualBox. You have to keep in mind that one of them will always be the primary OS. Say I install Ubuntu inside Windows using virtualbox. You will be able to boot into windows without booting into ubuntu (You simply do not launch virtualbox). The reverse is not possible to the best of my knowledge.

---

### Post by ACubed10 on 2013-02-12
[http://www.youtube.com/watch?v=RqRmNsLqKCc](http://www.youtube.com/watch?v=RqRmNsLqKCc)

AllenMC, this video will explain very well what a virtual machine is.  Good info here.

To help you understand more.  I use virtualbox to install new versions of linux distros (Fedora, OpenSUSE, Arch Linux)  This allows me to boot into Ubuntu then boot up Fedora and play with Fedora for testing, seeing new features, things like that.

---

### Post by Fungus on 2013-02-12
You may want to also take a look at the user help on Sun's VirtualBox website.  There is a ton of helpful information on installing and setting up guest OS's.  There is a nice user manual with lots of step by step details which could save you a lot of grief!

Also, I have a thread going you might want to see:

_Any Suggestions BEFORE I attempt to run Virtualization? _

[http://ubuntuforums.org/showthread.php?t=2106961]("http://ubuntuforums.org/showthread.php?t=2106961")

---

### Post by AllenMc on 2013-02-12
Thanks for everyone's responses. For now I'm just gonna stick with having to reboot my computer to switch between ubuntu and windows 7 and, when I have a little time, try and find a simple way to try and share files between the two. I would try black3agl3's suggestion but this is the 1st time I've ever done a partition which was completely done by the Wubi installer so I would have no idea how to do make a 3rd. 

But when I am a little less busy I am going to use y'all's suggestions to actually learn what virtualBox is and how to correctly use it and install it and everything.

---

### Post by SeijiSensei on 2013-02-12
The easiest method to share files in a dual-boot arrangement is to write them to a USB thumbdrive.  If it is formatted with FAT32 or NTFS, you'll be able to see it from either operating system.  Alternatively you could allocate a portion of the hard drive, format it as NTFS, and mount it on both sides.  If you have already installed both operating systems and have the entire drive allocated, it's easiest to write to a thumbdrive or some other external USB drive.

I have a server on my network that I sometimes use to move files between a VirtualBox host and guest rather than using the "shared folders" method.  As a bonus, copying the file to the network server creates a backup copy.

---

### Post by black3agl3 on 2013-02-13
> **AllenMc said:**
>  I would try black3agl3's suggestion but this is the 1st time I've ever done a partition which was completely done by the Wubi installer so I would have no idea how to do make a 3rd. 
That should contain enough information about partitioning [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

I dont know if you can mount your windows partition from ubuntu installed via Wubi. If it is possible, you might not need to partition your drive at all. Saves you from doing stuff that you dont understand right now...

EDIT: oh and wubi does not partition anything at all [URL="https://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29"]https://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29
[/URL]
[QUOTE=Wikipedia]Wubi adds an entry to the Windows boot menu which allows the user to run [Linux]("https://en.wikipedia.org/wiki/Linux_kernel").  Ubuntu is installed within a file in the Windows file system  (c:\ubuntu\disks\root.disk), as opposed to being installed within its  own [partition]("https://en.wikipedia.org/wiki/Disk_partitioning").[/QUOTE]
[]("https://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29")

---

### Post by Cheesemill on 2013-02-13
> **black3agl3 said:**
> I dont know if you can mount your windows partition from ubuntu installed via Wubi.
Wubi installations automatically mount the host Windows partition under /host.

---

### Post by black3agl3 on 2013-02-14
> **Cheesemill said:**
> Wubi installations automatically mount the host Windows partition under /host.
Thanks for the info.


**@AllenMc:**

From ubuntu: 
Then you can simply make a shortcut to your windows "My documents"
```
 ln -s "/host/Documents and Settings/**Username**/My Documents" **LinktoMyDocuments**

```**Username** is your username on windows. 
[C:\Documents and Settings\**Username**\My Documents]

You can change **LinktoMyDocuments** to whatever you want. This is the name of the shortcut that will lead you to your windows "My Documents"

Then, you just save everything you want to My Documents on windows...
On ubuntu you save everything to LinktoMyDocuments which will be found in your home folder 
(
which contains all the classic folders: Music, Desktop, Documents,..."
[/home/*UbuntuUsername*/LinktoMyDocuments] if this form makes it clearer for you
)


EDIT: use this suggestion only if you haven't yet partitioned your hard disk drive and you want to continue using ubuntu installed via wubi

---

### Post by AllenMc on 2013-02-14
@black3agl3 
That sounds exactly like what I want since I am keeping Wubi for and will probably just end up keeping it and not doing a partition.

Thank you!

---


---
title: "VirtualBox Dont Get It Working"
date: 2008-07-14
forum: Virtualisation
---

### Post by TheBeginning on 2008-07-14
Hello Peoples With Many More Experience.

I Would like to ask some question.
I need to have VirtualBox Installed at my Ubuntu 8.04

But whatever i try, i dont get it working.
What i want ?
I want to have access to my Win XP that allready exist.
(I Prefer Not To Install XP Again)
(I need this, cause there are some programs which i still need)

What i have done:

I added user to the group. "sudo usermod -a -G vboxusers username"

I created a new Virtual Machine.
/home/username/.VirtualBox/VDI/VirtualBoxMachine.vdi

When i want to connect, it keep giving me the same error : "Fatal: No bootable medium found! System halted."

Im a noob with Ubuntu, just working with it since some weeks.
I really dont have any clue what i can do to get VirtualBox working.
The manual, cant help me further, cause i dont understand it much.

Is it possible that somebody help me out via ICQ/MSN (Pidgin) if i pay you?
If somebody is interested in get this working for me, via a program similar like netmeeting that would be nice. I can pay via Wire Transfer.

With Kind Regards TheBeginning

* Sorry for my broken English *

---

### Post by scragar on 2008-07-14
when the thing has reached that stage use the devices menu and add a CD (it can either be an ISO or your real CD drive), you can then restart the box for it to boot from that CD/whatever.

you can also add a CD/whatever from the virtualbox main window, simply by clicking where it say's **CD/DVD romn** as long as that virtualbox is not running.

---

### Post by diffuze on 2008-07-14
You might find this post useful.
[http://ubuntuforums.org/showthread.php?t=769883](http://ubuntuforums.org/showthread.php?t=769883)

---

### Post by TheBeginning on 2008-07-14
Hello Scragar & Diffuce,

Thanks you much for the respons.

I tried to add this command : 
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WindowsXP.vmdk -rawdisk /dev/sda -partitions 2 -mbr ~/.VirtualBox/WindowsXP.mbr -relative -register
(I really dont know where are my XP is located. How can i find this out ?)
(Ubuntu + Win XP is running on 1 HD, 2 partitions)


But it says me : 
VirtualBox Command Line Management Interface Version 1.6.2
(C) 2005-2008 Sun Microsystems, Inc.
All rights reserved.

Cannot open replacement MBR file '/home/username/.VirtualBox/WindowsXP.mbr' specified with -mbr: VERR_FILE_NOT_FOUND

I hope i get some other replys from you guys.

~ TheBeginning

---


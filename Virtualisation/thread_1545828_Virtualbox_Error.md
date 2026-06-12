---
title: "Virtualbox Error"
date: 2010-08-04
forum: Virtualisation
---

### Post by geudrik on 2010-08-04
I have a legal copy of Windows 7 Ultimate (Just did the migration from crap to awesomefreeness) but still need windows for a few things at work.  Nothing major so a VM would be perfect.  

I installed the latest version of VirtualBox, set everything up as I'm supposed to, directed it to my Win7 ISO and when I start the VM, I get the following error:

> 
[IMG]http://www.patlitke.com/vBoxError.png[/IMG]


Anyone have any ideas as to why I can't start my VM / get the install going? :(
Usually VM's are easy (at least, I usually never have issues :s )

---

### Post by gdonwallace on 2010-08-04
I have looked over some of the how-to's on getting VirtualBox VM installed and they really seem overly complicated.

Here is what I do.  I start by creating a blank VM.  Label it whatever OS I am going to install.  Change all the settings to what I like them to be.  During this creation phase, it will ask to create a new virtual drive to install on.  I answer yes to that, and go through the process of creating that drive.  You now have a VM that has nothing in it and a blank Hard Drive with nothing installed.  Insert your Win 7 disk, once it has been recognized, choose the newly created VM and click start.  If you setup the CD drive to use the host, when the VM starts it will boot from that CD and you will be walked through the install process for Win 7.

Two things though.  You said you pointed the VM to the Win7 ISO.  If it is an actual ISO file, then it wont work.  You need to burn that ISO to CD / DVD so that it will create a Win7 CD / DVD.  Secondly, there is a known issue in VirtualBox with the EXT4 file system.  Look at your hard drive settings and make sure that the "Use host I/O Cache" option has a check mark in it.

Good luck.

---

### Post by geudrik on 2010-08-04
Thank you sir, that helped a bunch.  The issue though, was stemming from my use of dual cores.  I can actually boot off the ISO file and install using 1 core (after stepping down from two virtual cores).  But, since my native ubuntu isn't 64 bit, my Win 7 is useless to me >.<

Now, I'm trying x86 Win XP Pro, but it can't detect the hard drive that's attached.  This is obviously the virtual drive that VirtualBox has set up.  XP install just doesn't see it :(

Ideas on that one? :s

---

### Post by Ginsu543 on 2010-08-04
Have you by any chance set your Storage Controller in VBox to SATA instead of IDE (PIIX4)? Win XP cannot natively recognize SATA without first installing SATA drivers.

---


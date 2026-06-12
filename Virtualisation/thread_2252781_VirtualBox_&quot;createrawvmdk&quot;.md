---
title: "VirtualBox &quot;createrawvmdk&quot;"
date: 2014-11-14
forum: Virtualisation
---

### Post by swish2 on 2014-11-14
Ok, bare with me here. I have always thought about switching over, but have been lazy until my windows HDD decided it wouldn't boot after a recovery to an earlier date :\. anyways screw it i decided to use Ubuntu live CD to play around and recover some data, which i was able to do with ease! However i wanted to see if i could take this step further and use VMBOX to  load Windows and run** *Chkdsk -f*** on the drive to see if it could fix the bad sectors. (i have already tried ntfs-progs, etc) this is my final attempt before i wipe my drive, still missing some things, so i figured I would ask for help.

I found this site [http://www.serverwatch.com/server-tutorials/using-a-physical-hard-drive-with-a-virtualbox-vm.html](http://www.serverwatch.com/server-tutorials/using-a-physical-hard-drive-with-a-virtualbox-vm.html)

However that dang **VBoxManage internalcommands createrawvmdk **does not work at all! Says invalid command. I have googled my little fingers off for the past 13 hours and have found nothing other than a few things about using a closed source VMBox or whatever.

Is that "**createrawvmdk**" command obsolete or something?


Any help in any direction would be great.

---

### Post by slickymaster on 2014-11-14
*Moved to the ***Virtualisation*** sub-forum*

---

### Post by ibjsb4 on 2014-11-14
You have the Ubuntu live CD?  I take this to mean that you have the DVD.  Current supported release does not fit on a CD.  Anyhow ..

The live DVD (and older CD) has Gparted, which can be used to check and possibly repair the NTFS file system.

[http://gparted.org/display-doc.php?name=help-manual#gparted-Check-partition](http://gparted.org/display-doc.php?name=help-manual#gparted-Check-partition)
[http://www.dedoimedo.com/computers/gparted.html#mozTocId748422](http://www.dedoimedo.com/computers/gparted.html#mozTocId748422)

There is also TestDisk that can be used to create a live rescue cd.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

I have no idea how to do this with vBox.

---

### Post by swish2 on 2014-11-14
I actually meant that i had the Live USB, I apologize for the misinformation.  I have moved onto installing a full copy of Ubuntu onto a 250gb external USB hard drive, which i am using now by the way.

Yeah I tried testdisk it sees bad sectors but can't fix the issue. and Gparted gave up.  Its an NTFS so really the only thing left is to do a chkdsk.   I remember seeing a post somewhere else that they mounted their drive inside **vBox** and ran the dos command from there and it worked. That is why i was trying to figure out what the heck was up with the *"createrawvmdk"* command in** vBox**

---

### Post by JKyleOKC on 2014-11-15
You can mount the original Windows drive's C:\ folder in VBox as a "shared folder" from the VBox settings menu, with the Windows VM shut down to allow changes of the settings. When you define the shared folder you'll find two check boxes; one if for read/write permission and the other auto-mounts it. I would check the one for r/w but not the one for auto-mounting since if the damage prevents its mounting that could freeze the VM.

To mount it in the VM, power up the VM and then go to the Network Places window, locate the "vboxsrv" (or similar) share there, and drill down that to the C drive's root folder. From there you may be able to run chkdsk /f, but the damage may be too great for this to work. Also, since the shared folders feature in VBox works only on folders, not on the whole drive, chkdsk may refuse to run. However you still might be able to copy off the material you're still missing, before wiping the drive completely.

---

### Post by JKyleOKC on 2014-11-15
Did a bit of research and there's no "createrawvmdk" command in the current versions. However in the help file that's available from the main VBox menu bar, there's a section "9.9.1. Using a raw host hard disk from a guest" that goes into total detail on how to do what you're needing! It even gives you sample commands to use...

Hope this helps!

---

### Post by swish2 on 2014-11-15
JKyle,

Thanks for the info, I will give it a shot and see what happens. I am surprised that I did not see that seeing as how I was looking through their online manual. I guess a second set of eyes looking for the same thing is always good. I will let you all know the results as soon as I try it.

---

### Post by swish2 on 2014-11-15
I just read through that help file and it even has the 'createrawvmdk' command. so i tested it again to make sure that it wasn't anything to do with me maybe running the live Usb of ubuntu.
so to test i just stopped after the command itself, and as you can see it returns the same. lol Maybe i should message the makers of Vbox to either fix it or update their help file lol.

ghost@ghost-Satellite:~$ VBoxmanage internalcommands createrawvmdk
VBoxmanage: command not found
ghost@ghost-Satellite:~$

---

### Post by JKyleOKC on 2014-11-15
Try "VBox[COLOR="#FF0000"]M[/COLOR]anage internalcommands createrawvmdk" instead of "VBox[COLOR="#FF0000"]m[/COLOR]anage internalcommands createrawvmdk" and let us know what happens. Linux is case-sensitive and this often confuses those used to Windows and its lack of same.

I just tried here and this is what I got: ```
Oracle VM VirtualBox Command Line Management Interface Version 4.3.16
(C) 2005-2014 Oracle Corporation
All rights reserved.

Usage: VBoxManage internalcommands <command> [command arguments]

Commands:

  createrawvmdk -filename <filename> -rawdisk <diskname>
                [-partitions <list of partition numbers> [-mbr <filename>] ]
                [-relative]
       Creates a new VMDK image which gives access to an entite host disk (if
       the parameter -partitions is not specified) or some partitions of a
       host disk. If access to individual partitions is granted, then the
       parameter -mbr can be used to specify an alternative MBR to be used
       (the partitioning information in the MBR file is ignored).
       The diskname is on Linux e.g. /dev/sda, and on Windows e.g.
       \\.\PhysicalDrive0).
       On Linux or FreeBSD host the parameter -relative causes a VMDK file to
       be created which refers to individual partitions instead to the entire
       disk.
       The necessary partition numbers can be queried with
         VBoxManage internalcommands listpartitions

WARNING: This is a development tool and shall only be used to analyse
         problems. It is completely unsupported and will change in
         incompatible ways without warning.

Syntax error: Mandatory parameter -filename missing

```I didn't go any deeper but this may get you a bit farther down the rabbit hole...

---

### Post by swish2 on 2014-11-15
well I'll be damned! It is good to know about the case sensitive thing! I shall crawl deeper into the rabbit hole and let you know what happens!

---

### Post by TheFu on 2014-11-15
> **swish2 said:**
> well I'll be damned! It is good to know about the case sensitive thing! I shall crawl deeper into the rabbit hole and let you know what happens!

Linux is different from Windows in many ways. About 80% seems similar, but isn't. 
[http://blog.jdpfu.com/Lin_4_Win_Users](http://blog.jdpfu.com/Lin_4_Win_Users) - provides a primer for Windows users ... I didn't write it, but find it useful for folks new-to-Linux, especially if they've been trained in Microsoft stuff (like domain admins).

---

### Post by swish2 on 2014-11-19
TheFu,

thanks for the read. I will def have to read deeper. See what things are similar yet different. I think i might just be a fully converted junkie lol

---

### Post by TheFu on 2014-11-19
> **swish2 said:**
> TheFu,

thanks for the read. I will def have to read deeper. See what things are similar yet different. I think i might just be a fully converted junkie lol

If you like that perhaps it is time to gain some basic background in an easy to read manner - download this free PDF file [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) - read the first 100 pgs and quickly skim the rest of the book.  This is organized training, not google-for-issueA, then google-for-issueB learning.  It will save you days, weeks, months of frustration to **read** the first 100 pgs.

Learning the CLI happens once and lasts for decades. I use the same commands and scripts I learned in 1993.

Learning Linux GUIs happens every 3 yrs - because GUI programmers need to change things (often for little real progress).

Which do you think is more efficient in gaining knowledge?

Oh ... and if you want much more power over virtualization, check out KVM and virt-manager. Uninstall virtualbox first. Only 1 hypervisor should be installed at a time on computers (for non-experts).  It is only desktop-on-desktop where virtualbox makes more sense than KVM, IMHO. For servers, there isn't any comparison - kvm wins.

---

### Post by swish2 on 2014-11-22
Hey Guys,

Thanks for all of the help! This is propably the best forum experience that i have ever had. Most of the time with any forum, whena newb asks a quiestion they seem to get crapped on, even if they did search through hell and high water to find an answer. I am sure i would have never found the answer being that the commands are Case Sensitive. THANKS!

And Fu thanks for the materials. !!

I am sure that I will have more questions later lol 

Take it easy guys! Marking this as solved.

V/R
Shawn

---


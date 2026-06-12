---
title: "Help with installing LSI RAID drivers on Ubuntu Server"
date: 2012-06-13
forum: Server Platforms
---

### Post by DFergLSI on 2012-06-13
It was suggested that I rename the title of my thread to get a better responce.  I could not edit the title so I made this thread.  Please refer to this..
 
[http://ubuntuforums.org/showthread.php?t=2003028](http://ubuntuforums.org/showthread.php?t=2003028)

---

### Post by spynappels on 2012-06-13
I just replied to your old thread, I'll copy my response here.

---

### Post by spynappels on 2012-06-13
> **DFergLSI said:**
>  The desktop version is not what I am to be testing as the LSI MegaRaid controller and it's family of hardware is not designed for the home user it is for the Enterprise user.
 
Frankly I am stunned.  Ubuntu has done such a great job on making their Desktop easy to use and understand but the server is almost at the opposite end.

While I agree that having the LSI RAID cards supported in Ubuntu would be good, as most Ubuntu servers are run without a GUI, testing with a GUI may give a spurious result. 

Do you simply need the GUI to be able to install the MegaCLI binaries to test you can access the RAID card config from inside the OS? I presume it would be testing access from the CLI anyway, as that is what I've used on RHEL in a customised caching server, but that had the MegaCLI integrated into the custom CLI, there is no GUI on that server.

I guess I'm asking for some more details on exactly what you want to test, and whether you anticipate only needing the GUI to install the MegaCLI libraries and possibly some GUI frontend?

btw, there is a good reason that the server by default has no GUI, you would find that most *nix based server OSs do not have a GUI in production, and those which do often are administered by people from a Windows background, who rely on a GUI.
All the RHEL and Solaris10 servers we run at work (1000+) have no GUI and are administered through SSH/CLI only.

---

### Post by DFergLSI on 2012-06-13
> **spynappels said:**
> While I agree that having the LSI RAID cards supported in Ubuntu would be good, as most Ubuntu servers are run without a GUI, testing with a GUI may give a spurious result. 
 
Do you simply need the GUI to be able to install the MegaCLI binaries to test you can access the RAID card config from inside the OS? I presume it would be testing access from the CLI anyway, as that is what I've used on RHEL in a customised caching server, but that had the MegaCLI integrated into the custom CLI, there is no GUI on that server.
 
I guess I'm asking for some more details on exactly what you want to test, and whether you anticipate only needing the GUI to install the MegaCLI libraries and possibly some GUI frontend?
 
btw, there is a good reason that the server by default has no GUI, you would find that most *nix based server OSs do not have a GUI in production, and those which do often are administered by people from a Windows background, who rely on a GUI.
All the RHEL and Solaris10 servers we run at work (1000+) have no GUI and are administered through SSH/CLI only.
 
 
Ok, here we go!!
 
The installer seems to support LSI with it's own driver, so installing it without using our driver worked.  What I need to do is be able to install our driver during the install.  I also need to be able to update an existing driver to a new one.
 
My command line knowlegde dates back to DOS and Amiga DOS.  I have used the linux command prompt before but only to suppliment things.  This is how we do things in RH and Suse.  At this point I do not know the commnd to figure how Linux has mounted the USB dirve I just inserted.  I think the megacli (command line tool) will be ok.  I am not sure about MSM (GUI Tool).  But I need to get to my USB stick just to find out.
 
I am going to give the desktop a test run just to see what I can get working and done there.  But I really need to get a grip on how these thing would be installed in the Server edition as that is what I really need.

---

### Post by spynappels on 2012-06-13
So is the USB just a memory stick with an installer on it?

If so, you can see the path to the memory stick by doing the following:
```
df -h
```
One of the lines is likely to include /media/<label_of_usb_stick> and you can cd to that path to see what is on the stick.

I would recommend you try it on a server machine with the RAID card installed and Ubuntu Desktop installed first, and we can then give you a hand to replicate the same steps on a server install with the CLI only.

EDIT: I'm dropping offline now, but can pick this up once I get to the office tomorrow, and I can see what the setup is on one of our RHEL server at work too.

---

### Post by DFergLSI on 2012-06-13
> **spynappels said:**
> So is the USB just a memory stick with an installer on it?
 
If so, you can see the path to the memory stick by doing the following:
```
df -h
```
One of the lines is likely to include /media/<label_of_usb_stick> and you can cd to that path to see what is on the stick.
 
I would recommend you try it on a server machine with the RAID card installed and Ubuntu Desktop installed first, and we can then give you a hand to replicate the same steps on a server install with the CLI only.
 
EDIT: I'm dropping offline now, but can pick this up once I get to the office tomorrow, and I can see what the setup is on one of our RHEL server at work too.
 
Thanks, I am installing the Desktop version now.  I tried to look for a way to install a 3rd party Raid Driver but did not see it.  So, I will see if I can update to our driver once the install is finished.  I am going home soon also, so most of this will be picked up tomorrow.
 
David

---

### Post by DFergLSI on 2012-06-14
I left last night before the Desktop version was completly installed.  This morning I came in and had a an error that it could not install Grub.  I am running the install again but it is very, very slow.  It has been running an hour now and says "Retrieving file 35 of 81"....  ??????????

---

### Post by LHammonds on 2012-06-14
If you ever see a grub error when doing an update, make sure you run the "grub-install" command BEFORE you reboot.

First, find out which drive has your Linux boot partition.

```
sudo fdisk -l
```You might see something like this:
```

Disk **[COLOR=Red]/dev/sda[/COLOR]**: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders, total 16777216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006d7e2

   Device **[COLOR=Red]Boot[/COLOR]**      Start         End      Blocks   Id  System
/dev/sda1   [COLOR=Red]*****[/COLOR]        2048      391167      194560   83  Linux
/dev/sda2          393214    16775167     8190977    5  Extended
/dev/sda5          393216    16775167     8190976   8e  Linux LVM

Disk /dev/sdb: 10.7 GB, 10737418240 bytes
107 heads, 17 sectors/track, 11529 cylinders, total 20971520 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x35b92177

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    20971519    10484736   8e  Linux LVM

```In this example, my Linux boot device is /dev/sda1 which is on the hard drive called /dev/sda

So I would need to type the following:
```
sudo grub-install /dev/sda
```

**EDIT:** If you are having problems with grub itself, you might want to remove/purge grub and re-install it.

LHammonds

---

### Post by DFergLSI on 2012-06-14
> **LHammonds said:**
> If you ever see a grub error when doing an update, make sure you run the "grub-install" command BEFORE you reboot.
 
First, find out which drive has your Linux boot partition.
 
```
sudo fdisk -l
```You might see something like this:
```

Disk **[COLOR=red]/dev/sda[/COLOR]**: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders, total 16777216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006d7e2
 
   Device **[COLOR=red]Boot[/COLOR]**      Start         End      Blocks   Id  System
/dev/sda1   [COLOR=red]*****[/COLOR]        2048      391167      194560   83  Linux
/dev/sda2          393214    16775167     8190977    5  Extended
/dev/sda5          393216    16775167     8190976   8e  Linux LVM
 
Disk /dev/sdb: 10.7 GB, 10737418240 bytes
107 heads, 17 sectors/track, 11529 cylinders, total 20971520 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x35b92177
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    20971519    10484736   8e  Linux LVM

```In this example, my Linux boot device is /dev/sda1 which is on the hard drive called /dev/sda
 
So I would need to type the following:
```
sudo grub-install /dev/sda
```
 
**EDIT:** If you are having problems with grub itself, you might want to remove/purge grub and re-install it.
 
LHammonds
 
 
My main issue right now is that I am running the 32bit Desktop install on 3 different hardware configs and after the installer is done coping over the files it is taking forever to install.  The install has been running for 3 hours now and has gotten all the way up to file 35 of 108, the second number keeps going up.  At this rate I figure I should have it installed by say Tuesday of next week.

---

### Post by DFergLSI on 2012-06-14
OK, I think the desktop is a done deal.  I started the install on Three configs this morning between 9am and 9:30am.  Each one has stopped at "Retrieving File 43 of 105" and never goes any farther.  It is not 4:15pm and I don't feel that any OS install should take more then 7 hours.

---

### Post by DFergLSI on 2012-06-14
I am mounting a USB drive. Using..
 
"sudo mount /dev/sdb /media/usb"
 
it is mounting as read only - that is ok for now, would like read/write
 
BUT!  I can only seee 3 files of all the files on the usb drive.  AND, those files are hidden system files in windows.  But I can't see any of the directories, or any of the 'real' files on usb stick.

---


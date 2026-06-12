---
title: "Installing stuff on Virtual box"
date: 2010-05-19
forum: Virtualisation
---

### Post by bigseb on 2010-05-19
So I installed XP in Virtualbox... no problems there but:

1) must I still install all the chipset drivers, graphic card drivers, etc?

2) installing software... XP in VB doesn't read my driver and utility disc?! So I can't install drivers and stuff :( Keeps telling me disc is corrupted or data is not compatible with windows! wth?? It's windows stuff!!

3) It doesn't see my external hardrive either. Is that cos I still need to install all the chipset stuff adn SP2, etc?

Thanks

---

### Post by AClark on 2010-05-19
VirtualBox is presenting virtual hardware to the operating system and the drivers you are referring to are either "built in" or installed when you install the Guest additions from the devices menu.

You will have to install drivers for external devices like printers, scanners etc.

If you are using the OSE version from Synaptic you don't have USB support so that could explain your external disk problem. Or you may not have set up a USB filter in the settings for your virtual machine.

The manual is available from the Help menu and is really very comprehensive.  It can answer most of your questions.

It would be easier to help if you supplied a little more info about your setup - such as OSE or PUEL edition from Virtualbox.org. Your host version etc.

---

### Post by bigseb on 2010-05-20
> **AClark said:**
> 
It would be easier to help if you supplied a little more info about your setup - such as OSE or PUEL edition from Virtualbox.org. Your host version etc.
Don't even know what all that means :( I hope the help menu doesn't explain things along those lines 'cos then I'm stuffed!! Will check it out later

---

### Post by AClark on 2010-05-20
There are two possible versions of Vbox that you could have installed,
The Open Source Edition (OSE) or
The Personal Use & Evaluation License Edition (PUEL)

There are several different ways you could have installed - for instance from Synaptic, using apt-get from the command line, from Vitualbox.org/downloads etc.

All these things make a difference.  If you want to be able to use USB devices you must use the PUEL version of Virtualbox.  If you just went into The Synaptic Package Manager built in to Ubuntu and installed from there then you have the OSE edition.

The manual can be accessed from the Help menu.  I have found it to be quite clearly written and well laid out.  I believe that you can save yourself a lot of time and frustration by reading the manual.

Some of the most important sections would be:
VirtualBoxGuestAdditions
USB Support
Settings Dialog 

There is also lots of good info at the Virtualbox.org forums.

---

### Post by opacatica on 2010-05-21
Hi Bigseb,
 after installing WindowsXP, you should always verify if all drivers where properly installed.  A yellow exclamation mark shows an incorrect driver that have to be manually installed.  Most of the time Microshit Windows cannot find every drivers and you have the task for searching the web for each of them.  I personnaly like when Windows does not find drivers for your Ethernet card and offers to search the internet...  but this is off topic.  As stated by AClark when VBox is used virtual hardware is presented to the guess OS (i.e. Winshit XP).  This actually makes it lot easier to install as a virtual machine because Sun provides an ISO (CD image) with all drivers for those such virtual hardware, called VBox Guest Additions.
 
 I think Sun made a wonderfull job with VBox and I like their website as it is simple to use.  However they lack links for either their Beta versions and Guest Additions.  To download the latest ISO use this link:
[http://download.virtualbox.org/virtualbox/3.2.0/VBoxGuestAdditions_3.2.0.iso](http://download.virtualbox.org/virtualbox/3.2.0/VBoxGuestAdditions_3.2.0.iso)
 When the ISO is fully downloaded, mount a CD for your WindowsXP.  You may either use a physical CD driver or use an ISO file.  The later is prefered as it does not need you to burn the ISO on a disk.  The Guest Additions should start with the autorun and walk you through installation.  This will optimise your configuration.
 
 As for your external disk, the Open Source Edition (OSE) does not provide support for USB, don't even bother trying.  If you need USB support download the PUEL version from [http://download.virtualbox.org/virtualbox/3.2.0/](http://download.virtualbox.org/virtualbox/3.2.0/) and re-install VBox.  I assume you use Ubuntu for your host but have no idea which version but file names are named so to easily choose the proper one.
 I hope this was clear enough...

---

### Post by bigseb on 2010-05-24
I have Version 3.1.4 which I downloaded directly from the site, NOT synaptic! My HELP files don't seem to want to open though :( really stuck :(

Basically my XP has installed fine, now all I need (??) to do is install the driver for my graphics card and USB, and be able to install software from CD. 

Before anyone one mentions it, yes, I could dual boot but I prefer to do it this way, provided I can get it run properly.

Thanks

---

### Post by AClark on 2010-05-24
> I have Version 3.1.4 which I downloaded directly from the site

Still not sure if you have the Open Source or Personal Use edition - they can both be downloaded from Virtualbox.org

As stated before you must have the PUEL version in order to have USB support.

Have you installed the Guest Additions??  (Devices Menu)

> now all I need (??) to do is install the driver for my graphics card and USB

You don't install drivers for Graphics or USB in Virtualbox - Windows thinks it already has drivers installed - they are provided by the Virtualbox program. If you look at the Windows Device Manager you can confirm this.

> I have Version 3.1.4 
> be able to install software from CD.

V3.1.8 is the latest version for 3.1 and V3.2 is now available.
I remember having some weirdness with my CD drives around V3.1.4 that went away with later versions.  I would suggest installing the latest version and see if that helps.  You can always go back without hurting anything.

> My HELP files don't seem to want to open

I don't know why you can't access the help files.  I have several installs of Vbox on different machines and have never seen this issue.  It would seem to indicate maybe some other problem with the install but without more information I'm afraid I can't be much help there.

In any case you can get the help file as a PDF here: 
[http://download.virtualbox.org/virtualbox/3.2.0/UserManual.pdf](http://download.virtualbox.org/virtualbox/3.2.0/UserManual.pdf)
That would be for the latest Version.

Version 3.1.4 help file would be here:
[http://download.virtualbox.org/virtualbox/3.1.4/UserManual.pdf](http://download.virtualbox.org/virtualbox/3.1.4/UserManual.pdf)

Don't give up - It is absolutely possible to run Windows very well in a VM.

With the exception of graphics intensive games I don't notice much or any decrease in performance in my Windows Virtual Machines over native installs.

---

### Post by bigseb on 2010-05-26
Ok I'm really trying here but just not getting it. I installed that Guest Additions, and after doing something I could suddenly see (and read) a disc - some software I wanted to install. It gave me an error message saying it needed a service pack or something. Upon installing service pack two the whole thing just froze, nothing worked. Had to hard shutdown. Ever since then I can't see any disc at all. Must guest additions be ionstalled each and every time?

---

### Post by AClark on 2010-05-26
> It gave me an error message

Error message from Windows?
Error message from VirtualBox?
Error message from the program you were trying to install?

************************************************************
> Upon installing service pack two

Should I take this to mean that your original WinXP install was at Service Pack One??
**********************************************************************

> after doing something I could suddenly see (and read) a disc 

Do you know how to mount a CD in your Virtual Machine? (Devices menu - CD/DVD Devices - CheckBox)
**************************************************************************

> Must guest additions be installed each and every time?

No - but it doesn't hurt to reinstall and that can sometimes solve a problem - or even using Windows add/remove and uninstalling and then reinstalling.  If the hard shutdown screwed something up in Windows maybe a Guest Additions reinstall might help.

Are you sure you installed the version of GuestAdditions that matches your version of VirtualBox ?

Its not essential that the versions match but is generally better if they do.

Are you still at 3.1.4 or did you upgrade to 3.2.0 ??

More info is more helpful.
**************************************************************

As I remember there was a great deal of difficulty experienced by a lot of people when Service pack 2 for WinXP was first released so that could factor in also.

It may not seem like it but you are making progress.

---

### Post by TheFu on 2010-05-26
> **bigseb said:**
> Basically my XP has installed fine, now all I need (??) to do is install the driver for my graphics card and USB, and be able to install software from CD. 

It isn't clear from your responses so far, but **you will not be installing any graphics drivers** for your card.  Inside a virtual machine, your real physical hardware is hidden. Only virtual hardware is presented to a guest operating system. The only graphics adapter seen by a client OS will be "VirtualBox Graphics Adapter". The characteristics of your real graphics adapter doesn't matter.

As to USB ... if you installed the OSE - Open Source Edition - of VirtualBox, then USB is not supported.  If you installed the "other version" that specifically includes USB support, then you'll really need to read the manual to pass thru each USB device (by device ID) that you want ignored by the host OS and only used by a client OS. Or you can pass all of them thru to the client OS, but that may have undesirable effects too.

I was never really that impressed with USB support in VirtualBox myself. It seemed there were gotchas and contention between the Host and Client OSes for which was connected to a USB device. Also, the deviceID without a name/vendor that I expected wasn't fun either.

Anyway, I hope this clarifies some of the things you're working on.

---

### Post by AClark on 2010-05-26
> I was never really that impressed with USB support in VirtualBox myself

I use USB extensively in my VMs and I would say in general it works very well.

I have had good luck using the generic filter allowing all devices to be used by the VM.

Once you understand the basic principle that a USB device can only be used by one operating system at a time it seems to me that things happen pretty logically.

I will admit that it can be kind of hit or miss as to whether Ubuntu or the VM will capture a device when it is first plugged in but it is pretty simple to unmount it and capture it where you want it.

I have a couple printers that won't print from Ubuntu after being disconnected from a VM until they are power cycled but several others don't act this way so it seems more like a driver issue than a VBox issue.

I my experience most of the gotchas have involved just getting USB to work and that was mostly in previous versions 1.x & 2.x .

I would say that that situation has improved with each new release.

I have switched the main computers for two different businesses to Ubuntu and I use Vbox to run accounting & other specialized business software that I haven't been able to find an open source replacements for.

I have been very pleasantly surprised at how well this system is working for me.

---

### Post by bigseb on 2010-05-26
> **AClark said:**
> Error message from Windows?
Error message from VirtualBox?
Error message from the program you were trying to install?

********************************
****************************


Should I take this to mean that your original WinXP install was at Service Pack One??
**********************************************************************



Do you know how to mount a CD in your Virtual Machine? (Devices menu - CD/DVD Devices - CheckBox)
**************************************************************************


No - but it doesn't hurt to reinstall and that can sometimes solve a problem - or even using Windows add/remove and uninstalling and then reinstalling.  If the hard shutdown screwed something up in Windows maybe a Guest Additions reinstall might help.

Are you sure you installed the version of GuestAdditions that matches your version of VirtualBox ?

Its not essential that the versions match but is generally better if they do.

Are you still at 3.1.4 or did you upgrade to 3.2.0 ??

More info is more helpful.
**************************************************************

As I remember there was a great deal of difficulty experienced by a lot of people when Service pack 2 for WinXP was first released so that could factor in also.

It may not seem like it but you are making progress.

- Error message was for XP but came while I was installing my software

- My XP is SP1

- Yes I know how to mount

- Don't know the answers to the rest at the mo. Will get back to you on that. Gotta go to work now :(

---

### Post by bigseb on 2010-05-26
> **TheFu said:**
> It isn't clear from your responses so far, but **you will not be installing any graphics drivers** for your card.  Inside a virtual machine, your real physical hardware is hidden. Only virtual hardware is presented to a guest operating system. The only graphics adapter seen by a client OS will be "VirtualBox Graphics Adapter". The characteristics of your real graphics adapter doesn't matter.


Ok, that answers a big one. Thanks!

@ TheFu and AClark

Is there any way to access 'C:/Documents and settings/etc' from within Linux? That way I wouldn't need to bother fiddling about with USB ports. I could just exit Virtualbox and transfer files using the host OS.

---

### Post by mick463 on 2010-05-28
I am assuming you have ubuntu as your main system .If you do to get all the drivers for usb working you have to add yourself to the virtualbox users group and then they work.

---

### Post by TheFu on 2010-05-29
> **bigseb said:**
> Is there any way to access 'C:/Documents and settings/etc' from within Linux? That way I wouldn't need to bother fiddling about with USB ports. I could just exit Virtualbox and transfer files using the host OS.

Yes, you can access the host OS files/directories from a client by many different methods. VirtualBox has the "share" built-in facility or you can use OS specific file sharing methods like samba, NFS, sshfs, ....  and Windows Shares for MS-Windows hosts.

Accessing files located on a client from the host OS is only available via OS specific file shares like samba.

Obviously, for any of these methods to work, the host and client operating systems must be running.

I would caution against accessing settings on the host from a client.  Accessing documents shouldn't be a problem, but if you're trying to share Firefox or IMAP settings, I'd worry about corruption if multiple clients access/write to the files simultaneously. File locking should handle this, but with programatic access, you never know.

---

### Post by TheFu on 2010-05-29
> **AClark said:**
> I will admit that it can be kind of hit or miss as to whether Ubuntu or the VM will capture a device when it is first plugged in but it is pretty simple to unmount it and capture it where you want it.

When it works, it works. When the host OS (MS-Windows) captures a USB device before the client does, it becomes more difficult. I've also had issues with USB scanners and headsets performing poorly or not at all. The mix of host and client OS probably matters.

Don't misunderstand, if you have a specific USB device and you ALWAYS want the client OS to capture it, as long as you have the client running BEFORE you plug it into the physical port, it will work. If you are less conscientious and forget this, then the hassles begin. I guess I shouldn't expect my mind to be read to "do what I meant, not what I did", but I do.

The other complaint is that the displayed USB IDs aren't very useful to a human. There are usually 4+ USB devices displayed and the listed "vendor" has nothing to do with the name by which I know the device. Something that used a generic term - headphone, headset, flash storage would be nice. Heck, if they'd label the USB controllers as "USB Controllers" at least then the real devices would be determinable.  

How can VirtualBox deal with this?  I don't think they can if the output of `lsusb` doesn't have the data. I know that a name like "unknown device" isn't very useful to me. If the data does show up, like below

[FONT=Courier New]$ lsusb
Bus 002 Device 004: ID 04e8:324c Samsung Electronics Co., Ltd ML-1740 Printer
Bus 002 Device 003: ID 0a81:0205 Chesen Electronics Corp. PS/2 Keyboard+Mouse Adapter
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[/FONT]
I think virtualbox can increase the display size so the last parts can be seen and remove hubs (when did you ever care about a USB hub?).

Sorry, I didn't initially mean to hijack this thread.

---

### Post by GrouchyGaijin on 2010-10-18
> **TheFu said:**
> 

Don't misunderstand, if you have a specific USB device and you ALWAYS want the client OS to capture it, as long as you have the client running BEFORE you plug it into the physical port, it will work. 

I have a question and I hope I can get an answer before I spend a lot of time setting up virtual box only to find out that this will not work.

I have a scanner that happens to be on the not supported list for Ubuntu.  Do you think that if I installed Windows inside Virtual Box I could use the scanner?  I'm thinking no, but it would be nice if it worked.  That way I could use my scanner and dump the Windows partition on my laptop.

---

### Post by AClark on 2010-10-18
> **GrouchyGaijin said:**
> 
I have a scanner that happens to be on the not supported list for Ubuntu.  Do you think that if I installed Windows inside Virtual Box I could use the scanner? 

The short answer is yes you can.

I am assuming you have a USB scanner.

_IF_ you install the PUEL version of VBox from the web site - NOT the open source version in the repositories.

_IF_ you set up & get USB working correctly.  This is MUCH easier than it used to be but still gives some people fits.

The manual that comes with Vbox is actually very good I highly recommend reading the section on USB support and any others that you may have questions about.  It will save you from most of the commonly posted problems.

Remember setting up your Windows install in Virtualbox is just like setting up a new computer - Installing Hardware Drivers etc.

---

### Post by GrouchyGaijin on 2010-10-19
@AClark  It worked.  I was able to get Virtual Box to recognize the scanner in about 10 minutes.  You need to add the user to the group VirtualBox *_then_* reboot Ubuntu. (Logging out might work, but I rebooted.)
The tricky part was getting Windows XP to see the scanner (or anything else) until I checked if usb was enabled in the add hardware dialog box.  It wasn't so I put the Windows CD back in and XP added usb support then everything worked.
I got tired and decided not to try and figure out how to share folders between the Ubuntu host and virtual XP so I just save what I scanned in Virtual Box to an external hard drive then open it up from Ubuntu when I'm done.

---

### Post by AClark on 2010-10-19
> I got tired and decided not to try and figure out how to share folders between the Ubuntu host and virtual XP

Sharing folders is pretty straight forward.  I create a folder for data in my Home folder & then add it under Devices/Shared Folders in Vbox but you can share any folder in your Ubuntu Home directory.

Again the Help file in Vbox explains it well.

I find VirtualBox incredibly useful - I can't remember the last time I booted actual Windows. The last three computers I built are pure Ubuntu and I run two businesses on them.

---

### Post by GrouchyGaijin on 2010-10-20
@AClark

Yep it is pretty straight forward.  I'm so happy now, I can use my scanner again without having to shut down and boot into Windows which takes a long time to boot.  Now I can scan in Virtual Box (Windows on VB launches soooooo much faster than booting into my Windows partition.) and save the scanned files to a shared folder in my home folder in Ubuntu.

This is great!

---


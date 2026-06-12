---
title: "What should be the ideal persistence partion/s size?"
date: 2017-04-23
forum: Ubuntu/Debian BASED
---

### Post by LastDino on 2017-04-23
Well, recently I ran into trouble when I tried to
```
sudo apt-get update && apt-get upgrade && apt-get dist-upgrade
```

on my persistent Sandisk 32 GB (3.0) which I was using for better part of last 6-7 months to have Kali at my disposal.

During upgrade it suddenly popped with error that I was running short on space in "Var" directory.
I tried 
```
sudo apt-get clean 
```

It helped initially but then after some time I ran into same error.

Then I checked with Gparted and it turned out both my 5 GB /Boot and 7 GB persistence partition were almost full. No wonder I was getting this error. 

As, the thing was bit old, I went ahead and decided to format entire thing to repartition, so here I come with some questions

What should be the ideal size for /boot and persistence partitions? Is it idea to have separate data partition as well? Is it a good idea to keep swap space just in case I ran into old hardware?

Is it possible to have multiple persistence partitions? For different OS's running? Without causing problem or conflict?

Generally I keep "/" on HDD installs to be 25 GB as a thumb rule, but here it would be great if I can get some opinions before I get down to making new persistent Kali or Ubuntu install..  

Really sorry if this sounds basic or too confusing, but this is the only place I know where lot of experienced Linux users come on same board.

---

### Post by #&amp;thj^% on 2017-04-23
For myself I like to have a "/" of 15 gigs....this will certainly vary from user to user.
But i have a question for you...
How often do you run:
```
sudo apt autoremove
```

---

### Post by LastDino on 2017-04-23
> **1fallen said:**
> For myself I like to have a "/" of 15 gigs....this will certainly vary from user to user.
But i have a question for you...
How often do you run:
```
sudo apt autoremove
```

Very often, I run
```
sudo apt-get autoremove
```

after each run of that update line command in opening post. In this particular case autoremove didn't free up any space, but clean one did. I'm guessing that it was due to upgrade process was going on and I had done 600 MB of it successfully before getting prompted for 1064MB more. That is when I got the error. I guess lot of leftover from update was collected there and even after autoremove and clean command it wasn't sufficient. 

I don't know specifically which command is better, I tend to use both.

Also, is that 15 gb for persistent USB? Or you're talking about regular HD install?

---

### Post by #&amp;thj^% on 2017-04-23
> **LastDino said:**
> 
I don't know specifically which command is better, I tend to use both.

_**Also, is that 15 gb for persistent USB? **_Or you're talking about regular HD install?

Yes a "_**persistent USB**_"
That's very odd that "autoremove" was not freeing up more space?:confused:
And just to add some information for clairity:
From the manpage of apt-get.

 >    clean clears out the local repository of retrieved package files. It removes everything but the lock file from /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When APT is used as a dselect(1) method, clean is run automatically. Those who do not use dselect will likely want to run apt-get clean from time to time to free up disk space.



 what sudo apt-get autoremove does:

Whenever you install an application (using apt-get) the system will also install the software that this application depends on. It is common in Ubuntu/Linux that applications share the same libraries. When you remove the appplication the dependency will stay on your system.

So apt-get autoremove will remove those dependencies that were installed with applications and that are no longer used by anything else on the system.

And also kali is a Rolling Release...so lots of newer less tested (or less Stable) packages being introduced to your system.
Hope this had some usefulness.

---

### Post by LastDino on 2017-04-23
> **1fallen said:**
> Yes a "_**persistent USB**_"
That's very odd that "autoremove" was not freeing up more space?:confused:
And just to add some information for clairity:
From the manpage of apt-get.

 


 what sudo apt-get autoremove does:

Whenever you install an application (using apt-get) the system will also install the software that this application depends on. It is common in Ubuntu/Linux that applications share the same libraries. When you remove the appplication the dependency will stay on your system.

So apt-get autoremove will remove those dependencies that were installed with applications and that are no longer used by anything else on the system.

And also kali is a Rolling Release...so lots of newer less tested (or less Stable) packages being introduced to your system. 
Hope this had some usefulness.

Yes, very helpful. Especially difference between Autoremove and Clear command. I think that man page explanation holds the answer to as to why Clear had more effect in my case, there must be lot of repository and retrieved packages chunk in Var due to update process and I go with install everything rather than dis-selecting, so that fault also lies with me.

---

### Post by TheFu on 2017-04-23
Well, the "ideal size" is 200TB for each partition, right?

Since that isn't usually possible, we have to compromise.  If you properly maintain the Ubuntu system and don't go crazy with 50 kernels, 200 GUI programs, and 1 wireshark capture, then you can live with 15G for / and 500MB for /boot/.

I stopped using flash storage for USB boots long ago - they are slow. Get a cheap m.2 64G SSD and put it into a USB3 external enclosure - use that for everything.  You'll get the great performance from USB3.

BTW, kali should only be used for security stuff, not as a normal desktop.  Kali is extremely hackable. It is not secure enough to use as a desktop.

My main desktop is 17G total.  I do perl web-app development on it.  Of course, elsewhere on the network and NFS mounted is plenty of storage ... around 16TB, plenty.  If you don't have a need to split /var, /home, /usr, /boot, and you have plenty of storage, then I wouldn't bother splitting into different partitions.  That just leaves unused space in the different partitions.  OTOH, if you use full-disk encryption, then /boot is normally outside the encrypted areas and should be 500MB with the rest of the storage as a single encrypted partition with LVM over the LUKS encryption, then you can have as many LVs sized how ever you want.  Using LVs with ext4 provides lots and lots of flexibility. You can resize most of them on the fly. Through the magic of LVM.

Don't know whether any of this helps with USB live-boots. Sorry.

BTW, please be careful with case and leading / characters. Every OS except Windows is case-sensitive  - /boot is NOT the same as /Boot.  Similarly, /var is not the same as "Var"  - correctness and accuracy are important if you want accurate and correct answers.

---

### Post by LastDino on 2017-04-24
> **TheFu said:**
> Well, the "ideal size" is 200TB for each partition, right?

Since that isn't usually possible, we have to compromise.  If you properly maintain the Ubuntu system and don't go crazy with 50 kernels, 200 GUI programs, and 1 wireshark capture, then you can live with 15G for / and 500MB for /boot/.

I stopped using flash storage for USB boots long ago - they are slow. Get a cheap m.2 64G SSD and put it into a USB3 external enclosure - use that for everything.  You'll get the great performance from USB3.

BTW, kali should only be used for security stuff, not as a normal desktop.  Kali is extremely hackable. It is not secure enough to use as a desktop.

My main desktop is 17G total.  I do perl web-app development on it.  Of course, elsewhere on the network and NFS mounted is plenty of storage ... around 16TB, plenty.  If you don't have a need to split /var, /home, /usr, /boot, and you have plenty of storage, then I wouldn't bother splitting into different partitions.  That just leaves unused space in the different partitions.  OTOH, if you use full-disk encryption, then /boot is normally outside the encrypted areas and should be 500MB with the rest of the storage as a single encrypted partition with LVM over the LUKS encryption, then you can have as many LVs sized how ever you want.  Using LVs with ext4 provides lots and lots of flexibility. You can resize most of them on the fly. Through the magic of LVM.

Don't know whether any of this helps with USB live-boots. Sorry.

BTW, please be careful with case and leading / characters. Every OS except Windows is case-sensitive  - /boot is NOT the same as /Boot.  Similarly, /var is not the same as "Var"  - correctness and accuracy are important if you want accurate and correct answers.

Yes, due to Kali being hackable is why I only operate it on USB 3.0, for everything else I've full installs of Ubuntu variants either dual booting with windows or standalone. My purpose of having Kali is to learn various tools in it and I can't dream about having it on my main hardware before having at least that much knowledge.

I was considering SSD, and will be buying sooner or later for the reasons you mentioned. 

I generally have separate data  partition on USB which is encrypted, but never full disk. Had some trouble with it in past.

And yes, your wise words were helpful, as a typical end user I'm not well versed with all the technical stuff yet. But learning it slowly. 

From what I understood so far on my USB I can leave 10 Gb for main and 10 Gb for persistence and leave rest for my encrypted data drive. Don't want to run in trouble again for lack of space with heavy updates. 

I've come to understand the importance of cleaning too, with right commands, but till I'm still in process of understanding basics, I would be needing to take default approach of installing all updates. Maybe with time that will also change. 

Anyone else with any other tip or experience? It would be great to get more views as I'm going to make my USB persistence tonight.

---

### Post by C.S.Cameron on 2017-04-24
Do not run a full software update on a Persistent flash drive.
Doing so quickly fills and bloats the drive. It duplicates info that is already on the drive as read only.
If you want an updateable or upgradeable system do a Full install.
A full install is also more secure than a Persistent install.
I make the first partition of a Full install NTFS and give it about half the disk space, so It can be read by both Linux and Windows.
Partition sizes can be changed using gparted.

---

### Post by LastDino on 2017-04-24
> **C.S.Cameron said:**
> Do not run a full software update on a Persistent flash drive.
Doing so quickly fills and bloats the drive. It duplicates info that is already on the drive as read only.
If you want an updateable or upgradeable system do a Full install.
A full install is also more secure than a Persistent install.
I make the first partition of a Full install NTFS and give it about half the disk space, so It can be read by both Linux and Windows.
Partition sizes can be changed using gparted.

I had no idea about this duplication phenomena. Is there any particular reason for it? Or way to clear it?

Never tried to do full install on removable drive, will have to check this out. 

Thank you very much for sharing experience, I had no clue about this.

---

### Post by C.S.Cameron on 2017-04-25
There are several ways to do a Live/Persistent install, Grub2, (mkusb), will boot iso files and Syslinux, (Unetbootin), will boot filesystem.squashfs files, both file types are read only.
If you do an update, new files are loaded but the original files being updated remain on the drive as they are read only, Computer Janitor will not get rid of them;)
Likewise with a Live/Persistent install the kernel is read only so the drive can not be upgraded. 
Even if it could, casper-rw, (the persistence file or partition), can not be reused from Ubuntu version to Ubuntu version, (but home-rw can).

[U]Following is step by step for installing 16.04 on a 16GB flash drive on an Intel machine.
[/U]
Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD or Live USB.
Start the computer, the CD/USB should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install third-party software.
Continue.

At "Installation type" select "Something else".
Continue

Confirm Device is correct.
Select "New Partition Table".
Click Continue on the drop down.

(Optional partition for use on Windows machine)
Click "Free space" and "+".
Make "Size:" about 1000 MB.
Select "Primary".
Location for the new partition = "Beginning of this space".
"Use as:" = "FAT32 file system".
And Mount point = "/windows".
Select "OK"

Click "free space" and then "+".
Select "Size:" = 5000 to 7000 megabytes, "Primary", "Beginning of this space", Ext4, and Mount point = "/" then OK.

(Optional home partition)
Click "free space" and then "+".
Select "Size:" = 1000 to 4000 MB, "Primary", Beginning, Ext2, and Mount point = "/home" then OK.

(Optional swap space, allows hibernation)
Click "free space" and then "+".
Select "Size:" = remaining space, (1000 to 2000 megabytes, or same size as RAM), "Primary", "Beginning of this space" and "Use as" = "swap area" then OK.

(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".

Select your location.
Continue.
Select Keyboard layout.
Continue.
Insert your name, computer name, username, password and select if you want to log in automatically or require a password.
Requiring a password to log in and selecting "Encrypt my home folder" are good options if you are worried about loosing your USB drive.
Select Continue.

Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if, when partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
You can revise grub later, if you wish.

---

### Post by LastDino on 2017-04-25
Thank you very much for posting detailed guide. So, basically remove HDD and treat USB as HDD and do install. Thanks :3

I'll mark thread as solved as I've come to learn lot of new things and seems like I might go with the "install" rather than "persistence", which makes it much more easier to maintain. Though, I feel there will be some proprietor driver issues across machines, but lets cross that bridge when it comes to it.

---

### Post by C.S.Cameron on 2017-04-26
My attempts to do a Full install to USB work on most machines I try as long I do not install proprietary drivers, (ie Nvidia).
As I understand Nvidia drivers do not even work with a Persistent install as video drivers are loaded before persistence.

---

### Post by LastDino on 2017-04-27
> **C.S.Cameron said:**
> My attempts to do a Full install to USB work on most machines I try as long I do not install proprietary drivers, (ie Nvidia).
As I understand Nvidia drivers do not even work with a Persistent install as video drivers are loaded before persistence.

That is probably true as well. Not that I've any third party graphic card drivers, and my requirement is only booting into USB to troubleshoot and do minor work and save. Shouldn't be problem with install.

---


---
title: "Some help?"
date: 2005-06-23
forum: Repositories &amp; Backports
---

### Post by Multikill on 2005-06-23
Ok so I'm a linux nub, but I'd like to switch over to ubuntu as I've heard great things.  So If someone could link me to a step to step guide on how to fully switch from windows home edition to ubuntu that would be great.

I think a while back I downloaded it but I didn't mess around with the files much, so it didn't get installed.  The one thing inspiring me to do this is the majority of internet user thats I know recommend linux.  

The switch to firefox was awesome, I'm hoping this is as well.

---

### Post by Lunde on 2005-06-23
[QUOTE=Multikill]Ok so I'm a linux nub, but I'd like to switch over to ubuntu as I've heard great things.  So If someone could link me to a step to step guide on how to fully switch from windows home edition to ubuntu that would be great.

I think a while back I downloaded it but I didn't mess around with the files much, so it didn't get installed.  The one thing inspiring me to do this is the majority of internet user thats I know recommend linux.  

The switch to firefox was awesome, I'm hoping this is as well.[/QUOTE]
 You know what really hit me.. there are no easy obtaiable guide for installing ubuntu, this is weird. I only looked for 10min, but I was sure it was one in the documentation area of [www.ubuntu.com](www.ubuntu.com).

But anyway.. it's pretty easy. It's one of the easyest linux distros I've ever installed so I'm sure you're safe.

I'll just write in quick what you have to do. 

**1.) **First you have to make an empty partition on your disk or simply get a second harddrive (I reccomend about 7-10 gig so you have som place for your programs, don't give it more even if you have the space for it, it's better to split in several partitions and maybe put the "home" directory on a seperate partition). I suggest you dual boot for a while until you at least have everything working in Ubuntu.

**2.)** Then boot from your CD and the installation will guide you through everything. Make sure you choose the empty space on your hard drive for installing Ubuntu, Ubuntu will partition your swap and root automaticly. 

Note: if you have a Pentium3 or newer, it's most likely a i686, not i386, both kernels will work fine, but install the one that's made for your system

**3.)** Get back here in the forum if you have problems connecting to the Internet, search for a solution or ask a question if you can't find it.

**4.)** Check out this excellent site for all sort of weird and wonderful things you can do with your new system
[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

**5.)** And find out some more here:
[http://www.ubuntuforums.org/showthread.php?t=31094](http://www.ubuntuforums.org/showthread.php?t=31094)

---

### Post by Dragonfly_X on 2005-06-23
I would recommend a duel boot with windows since u'r a nub. burn the image you downloaded onto a CD and:

1: Backup, Backup and Backup!!!

2: Partition u'r HD, if you have a separate HD even better.

3: Pop the ubuntu install CD into the drive and set the boot sequence to boot up from the cd.

4: press "enter" to enter setup and chose your language,location,ect.

5: When you get to the partitioning setup choose manually setup partition table.

6: Choose the partition or HDD you want to install it on. the default file system is ext3 so don't change it.

7: click ok and next or whatever follows and let ubuntu install it-self

If you follow the instructions of the installer it will be easy, u'll c! :-)

---

### Post by Multikill on 2005-06-24
ahh ok.  So I need to burn the file to a CD or send in for a cd.

and another question.  What does partition your drive mean.  I remember doing something like that when i bought a new Hard Drive a while ago for some spare room but why do I need to do it for installing this?  And how do I dual boot?

---

### Post by Lunde on 2005-06-24
[QUOTE=Multikill]ahh ok.  So I need to burn the file to a CD or send in for a cd.

and another question.  What does partition your drive mean.  I remember doing something like that when i bought a new Hard Drive a while ago for some spare room but why do I need to do it for installing this?  And how do I dual boot?[/QUOTE]
 The Ubuntu installer disk is .iso file, this ia a cd image ready to burn to a cd. There is also a possibuility to install from the net, I've never tried this, but if you have a  internet connection throug a standard networkcard it should work without problems.

Partitioning your disk: Split your disk into smaller parts. Ubuntu need a whole hard drive or an empty space on a hard drive. If you have an empty hard drive, Ubuntu will do this for you during installation. If not, you need to create som empty space on your drive before installation.

Dual boot: meens you can boot 2 or more OS from the same Computer. If you have Windows on your PC and you install Ubuntu on a seperate disk or partition on the same PC, Ubuntu will install Grub (A bootloader). This is a menu that load when you start your PC and let you choose which OS to start.

---

### Post by Multikill on 2005-06-24
thanks, your a helpful person.  I hope this is a good switch.

---

### Post by Lunde on 2005-06-24
[QUOTE=Multikill]thanks, your a helpful person.  I hope this is a good switch.[/QUOTE]
 We have all started from scratch here and have recieved the same help from more experienced people. This is something unique for the Linux, Gnu and open source community. Don't be scared to ask questions if you can't find the answere in this forum.

---

### Post by Multikill on 2005-06-25
Yea, I changed my boot order to make the CD drive boot first, and I have the ubuntu cd in it with the .iso on that cd.  How do I get it to install?

---

### Post by Lunde on 2005-06-25
[QUOTE=Multikill]Yea, I changed my boot order to make the CD drive boot first, and I have the ubuntu cd in it with the .iso on that cd.  How do I get it to install?[/QUOTE]
 What happens? does it still just boot windows? Maybe you have to press F12 during boot to choose the medium you're booting from, depending on your computer how it deals with CD boot.

---

### Post by Multikill on 2005-06-27
Pushing F12 doesn't do anything.  

And how do i go about making a new partition?

---

### Post by Lunde on 2005-06-27
[QUOTE=Multikill]Pushing F12 doesn't do anything.  

And how do i go about making a new partition?[/QUOTE]
 First to make sure of a coupple of things:
You are sure that your BIOS is set to boot from CD first?
When you burnt the CD, did you burn from .iso image, not burning the .iso file to a CD.  

Your empty space now is the place you want to install Ubuntu? if so, the Ubuntu installer will create the partitions for you if you just choose the empty space in the Installer when it asks where to install Ubuntu.

---

### Post by Multikill on 2005-07-19
i just burnt the ISO file not the image.  How do i burn the image?

---

### Post by Lunde on 2005-07-19
[QUOTE=Multikill]i just burnt the ISO file not the image.  How do i burn the image?[/QUOTE]
 Normally you have to choose write/burn from image and browse for the .iso file as source. If you can't find this, let me know which burner program do you use

---

### Post by Multikill on 2005-07-23
ok so im installing linux on my laptop right now.  If this messes anything up can i just rewrite over everything on windows?  Because im pretty sure i set the partition up right but not positive.  I'm a little squimish about it with my laptop because it costs alot and its parts (harddrive) are customized for it so it would be difficult to replace granted I mess it up.

---

### Post by varunus on 2005-07-23
Don't know if its too late for this, but here's a step by step guide on how to repartition your hard drive in the Ubuntu installer (by shrinking the windows partition): www3.telus.net/linux4u/ubuntu.html

If you did mess up the partitioning, its possible that it erased your windows drive...you'll have lost all your data, but you can reinstall windows over the entire drive and try again.  (Hence the "backup, backup, backup" advice from another poster.)

---

### Post by Lunde on 2005-07-23
It's very hard to mess up your hardware, so don't worry to much about that. If it's a new Laptop it also may have a varanty. 
What you might mess up is the disk partitioning, then what you have to do is repartition and reinstall everything, so be a bit careful. 
If you managed to create som free space on your drive, Ubuntu will take care of the rest and it should go painless. The above guide that varunus suggested is a great reference.

If you mess up anything, let us know and we'll help you with that. If you are unsure about what to do, just ask.

---

### Post by Multikill on 2005-07-23
well, ubuntu isn't working for me.   I push ESC to boot from windows in the GNU GRUB boot loader, and it has three different options.  They all are ubuntu.  I'd like to reinstall windows and redo it all (its new i had nothing to backup lol) with mabye someone online to ask about the partitioning?  Because to be honest I didn't know what to do for that, i just kinda went with what seemed logical.

And what i mean by its not working, is when it brings the login screen i login and it says could not look up internet address for ubuntu.  This will prevent GNOME from operating correctly.  It may be possible to correct the problem by adding ubuntu to the file/etc/hosts

---

### Post by Lunde on 2005-07-23
Is your windows partition still there? The Ubuntu problem is just a minor network problem so you don't need to give up.

At the Gnome login, press:
**Alt+Ctrl+F1**
then log in with your username and type:
**sudo fdisk -l**
This will list your partition tables, is your windows partition still there?

Did the Ubuntu installer recognise you network card / modem?

---

### Post by Multikill on 2005-07-23
EDIT:  I reintsalled linux and its freezing just after I login everytime.  I plugged my ethernet cord into it this time and the network error isn't appearing, but it is freezing, or at least i think it is.  The mouse won't move or anything.  It just has the ubuntu logo and thats it.  And yes windows is gone.

and another thing 

When i log in, the ubuntu logo comes up and if i move my mouse around while clicking it, it goes, but then freezes on the desktop.  If i don't move the mouse around it just plain freezes, any ideas?

---

### Post by Lunde on 2005-07-24
It may be the graphic drivers
Can you post your hardware specs, model of screen card?

Also do you want a Windows installation on your Laptop, If so check if you have a partition for it  with the above fdisk command I posted.

---

### Post by Multikill on 2005-07-24
In all honesty, I don't know my graphics driver.  Its a laptop so what ever is in their is in their.  I can get into the command line before I log in if their is a way to check thru that...

On another note I succesfully installed Ubuntu on my Desktop :)

---

### Post by Lunde on 2005-07-24
[QUOTE=Multikill]In all honesty, I don't know my graphics driver.  Its a laptop so what ever is in their is in their.  I can get into the command line before I log in if their is a way to check thru that...

On another note I succesfully installed Ubuntu on my Desktop :)[/QUOTE]
 The command:
**lspci**
Should list your hardware

---


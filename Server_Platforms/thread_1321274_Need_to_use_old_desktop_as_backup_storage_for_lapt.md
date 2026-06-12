---
title: "Need to use old desktop as backup storage for laptops"
date: 2009-11-09
forum: Server Platforms
---

### Post by aaronchall on 2009-11-09
Greetings, I am very new at this.  (I once spent several hours trying to network my wife's laptop and mine, only to find that the problem was that we were not on the same workgroup (in Windows...))

So now I'm on Ubuntu, most of the time, and my wife is on Vista.  

I have an old desktop (256 MB Ram, 1Ghz processor) with lots of storage space (two hard drives, one empty one with 80GB), and a wireless router.  XP (home) is crawling on it (it never ran very fast anyways.)  I've tried Puppy Linux, but it ran out of memory quickly, and the applet(?) designed to show available memory didn't work very well.

So, recalling I'm new to networking computers and filesharing, and security, as well as being very new to Linux, what OS should I use on my desktop to enable us to save/backup our laptops to it?  I would like to be able to browse the internet on it as well, and perhaps use OpenOffice too, so a GUI is necessary.

Would it also be possible to access the files from a remote computer via the internet?

My ISP is Cox, if that affects anything.

---

### Post by Aemaeth on 2009-11-09
Ok well here goes (I have this implementation running and it works great!)

download and burn a copy of ubuntu-9.04 or 9.10 server edition (I still use 9.04)

warning - this OS is text based so gui options are not present if you would like a gui i would reccommend using web-min. download and install instructions are easiest if you add the repositories to your /etc/apt/sources.list 
link here [http://www.webmin.com/deb.html](http://www.webmin.com/deb.html) - very useful

so go through the install and make sure to check the modules for samba, ssh-server, and anything else you might want to get your feet wet with... I reccommend using the Linux LVM so you can add the other hard drives to the array.

as for remote access use the ssh option you installed above and setup port triggering to get access through your router. if you use a linksys router I would reccommend usign [www.dyndns.org](www.dyndns.org) to setup a web address that will keep updated to your non-static ipaddress...

as for samba remember that filesystem level permissions trump whatever you set in samba. so to make them both happy try sudo chmod 777 permissons and then restrict file access at the samba level...

if this is too broad of a setup example let me know and ill write a better how-to....

Cheers!

---

### Post by hictio on 2009-11-10
> **aaronchall said:**
> Greetings, I am very new at this.  (I once spent several hours trying to network my wife's laptop and mine, only to find that the problem was that we were not on the same workgroup (in Windows...))

So now I'm on Ubuntu, most of the time, and my wife is on Vista.  

I have an old desktop (256 MB Ram, 1Ghz processor) with lots of storage space (two hard drives, one empty one with 80GB), and a wireless router.  XP (home) is crawling on it (it never ran very fast anyways.)  I've tried Puppy Linux, but it ran out of memory quickly, and the applet(?) designed to show available memory didn't work very well.

So, recalling I'm new to networking computers and filesharing, and security, as well as being very new to Linux, what OS should I use on my desktop to enable us to save/backup our laptops to it?  I would like to be able to browse the internet on it as well, and perhaps use OpenOffice too, so a GUI is necessary.

Would it also be possible to access the files from a remote computer via the internet?

My ISP is Cox, if that affects anything.

Hey, man, you want that box to do everything and then some ;)
For the OS that would allow you and your wife to make backups of your laptops, I would say that you safely go with Ubuntu Server (what else are you going to get around here :) ), and to make the actual backups, take a look at [BackupPC](http://backuppc.sourceforge.net/).

You can install a GUI on your Ubuntu Server box, take a look at the archives, or use the search, that's a question often asked.
Here are few links on the subject:

[Installation on Low Memory Systems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[Modest Spec or Barebones Installation of Ubuntu](http://www.psychocats.net/ubuntu/minimal)
[Ubuntu Minimal Desktop](http://wiki.dennyhalim.com/ubuntu-minimal-desktop)

---

### Post by aaronchall on 2009-11-10
Hey guys, thanks for the response!!!

> **Aemaeth said:**
> Ok well here goes (I have this implementation running and it works great!)

download and burn a copy of ubuntu-9.04 or 9.10 server edition (I still use 9.04)

warning - this OS is text based so gui options are not present if you would like a gui i would reccommend using web-min. download and install instructions are easiest if you add the repositories to your /etc/apt/sources.list 
link here [http://www.webmin.com/deb.html](http://www.webmin.com/deb.html) - very useful

so go through the install and make sure to check the modules for samba, ssh-server, and anything else you might want to get your feet wet with... I reccommend using the Linux LVM so you can add the other hard drives to the array.

as for remote access use the ssh option you installed above and setup port triggering to get access through your router. if you use a linksys router I would reccommend usign [www.dyndns.org]("http://www.dyndns.org") to setup a web address that will keep updated to your non-static ipaddress...

as for samba remember that filesystem level permissions trump whatever you set in samba. so to make them both happy try sudo chmod 777 permissons and then restrict file access at the samba level...

if this is too broad of a setup example let me know and ill write a better how-to....

Cheers!

I'm not sure I followed all of that.  What is the Linux LVM?  I use a USR router, if that makes a difference.  

> **hictio said:**
> Hey, man, you want that box to do everything and then some ;)
For the OS that would allow you and your wife to make backups of your laptops, I would say that you safely go with Ubuntu Server (what else are you going to get around here :) ), and to make the actual backups, take a look at [BackupPC]("http://backuppc.sourceforge.net/").

You can install a GUI on your Ubuntu Server box, take a look at the archives, or use the search, that's a question often asked.
Here are few links on the subject:

[Installation on Low Memory Systems]("https://help.ubuntu.com/community/Installation/LowMemorySystems")
[Modest Spec or Barebones Installation of Ubuntu]("http://www.psychocats.net/ubuntu/minimal")
[Ubuntu Minimal Desktop]("http://wiki.dennyhalim.com/ubuntu-minimal-desktop")

OK, Ubuntu server 9.10 should work ok on 256MB RAM?  But I won't have a GUI?  I'm ok with a command line, I grew up playing around on DOS (I found a few commands by trial and error, lots of errors), I just think it would be great to have a browser and text editor or something like that as a backup.  I'll look more into those links a little later.  But I suppose the command line may be the best solution given my unwillingness to install more RAM in an 8yr old computer...

Thanks again!!

Aaron

---

### Post by hictio on 2009-11-10
> **aaronchall said:**
> Hey guys, thanks for the response!!!



I'm not sure I followed all of that.  What is the Linux LVM?  I use a USR router, if that makes a difference.  



OK, Ubuntu server 9.10 should work ok on 256MB RAM?  But I won't have a GUI?  I'm ok with a command line, I grew up playing around on DOS (I found a few commands by trial and error, lots of errors), I just think it would be great to have a browser and text editor or something like that as a backup.  I'll look more into those links a little later.  But I suppose the command line may be the best solution given my unwillingness to install more RAM in an 8yr old computer...

Thanks again!!

Aaron

Ubuntu Server will work with 256 MB just fine (of course, if you later plan on hosting a mega popular website with an Oracle back office on it, the thing will melt; but for home use it'll do just fine :) )
Take a look at the link for the backup program I have recommended you, you install it from the command line, but after that you can do must of its administration thru a webfront.
Personally, I would not install a GUI, I mean, not one if the idea is running the GUI with the purpose of administering the box; you'll learn far more using the CLI thru SSH, something that will serve you good, because you'll be able to use with any other Linux distro or in other situation down the road.

---

### Post by aaronchall on 2009-11-12
> **Aemaeth said:**
> Ok well here goes (I have this implementation running and it works great!)
 
download and burn a copy of ubuntu-9.04 or 9.10 server edition (I still use 9.04)
 
warning - this OS is text based so gui options are not present if you would like a gui i would reccommend using web-min. download and install instructions are easiest if you add the repositories to your /etc/apt/sources.list 
link here [http://www.webmin.com/deb.html](http://www.webmin.com/deb.html) - very useful
 
so go through the install and make sure to check the modules for samba, ssh-server, and anything else you might want to get your feet wet with... I reccommend using the Linux LVM so you can add the other hard drives to the array.
 
as for remote access use the ssh option you installed above and setup port triggering to get access through your router. if you use a linksys router I would reccommend usign [www.dyndns.org]("http://www.dyndns.org") to setup a web address that will keep updated to your non-static ipaddress...
 
as for samba remember that filesystem level permissions trump whatever you set in samba. so to make them both happy try sudo chmod 777 permissons and then restrict file access at the samba level...
 
if this is too broad of a setup example let me know and ill write a better how-to....
 
Cheers!
 
 
So I'm going to download it, but it says there is 32 and 64 bit versions, and that to be sure you NEED the 32 bit version before using it, and that the 64 bit version is suitable for server configurations.  I'm pretty sure my processor is 32 bit, so... do I NEED the 32 bit version?  (my emphasis on the all caps...)

---

### Post by aaronchall on 2009-11-12
So, do I NEED the 32 bit version, and how do I know this?

---

### Post by aaronchall on 2009-11-12
So I'm basically going to take a leap of faith (in myself) and assume the notes on the download page are just badly written, and that the 32 bit version is necessary given the age of the processor, and go ahead and download that one.
 
 
Do these notes really say anything????
"64-bit version: This version is suitable for server configurations 
32-bit version: Please ensure your server requires this option" 
 
Unless someone stops me, 32 is what i'll burn on download completion.

---

### Post by hictio on 2009-11-12
What OS are you running on the box you want to install that Ubuntu Server?
If it is a Linux derivative, to know if it has a 32 bit edition installed, open a Terminal and type:

```

file /sbin/init ENTER

```

You'll see something like this:

```

/sbin/init: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.4.3, dynamically linked (uses shared libs), not stripped

```

This one is 32 bits.

---

### Post by aaronchall on 2009-11-13
Figured I share a little trial and error with you...: 

```
me@SYSTEM:~$ md5sum /DISK_IMG/ubuntu server iso/ubuntu-9.10-server-i386.iso
md5sum: /DISK_IMG/ubuntu: No such file or directory
md5sum: server: No such file or directory
md5sum: iso/ubuntu-9.10-server-i386.iso: No such file or directory
```Most apparent problem here was the fact that it was reading the directory as seperate locations because of the locations, but instead of addressing that, I wrote in the /media part that was the first thing I was thinking could be wrong...
```

me@SYSTEM:~$ md5sum /media/DISK_IMG/ubuntu server iso/ubuntu-9.10-server-i386.iso
md5sum: /media/DISK_IMG/ubuntu: No such file or directory
md5sum: server: No such file or directory
md5sum: iso/ubuntu-9.10-server-i386.iso: No such file or directory
me@SYSTEM:~$ md5sum /media/DISK_IMG/"ubuntu server iso"/ubuntu-9.10-server-i386.iso
55618ad5f180692f9dac20cbff352634  /media/DISK_IMG/ubuntu server iso/ubuntu-9.10-server-i386.iso
me@SYSTEM:~$ 
```So then I remembered from about a month back to put in the quotes... 
So now I'm feeling really clever.  And proper ISO download.  

Super. Now I just need a CD to burn it to.  (I have a feeling that the USB1 on the old computer would be a bit too slow...)

Aaron

---


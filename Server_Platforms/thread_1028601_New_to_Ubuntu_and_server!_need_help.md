---
title: "New to Ubuntu and server! need help"
date: 2009-01-02
forum: Server Platforms
---

### Post by EVPCS on 2009-01-02
Hello everyone,
I hope that somebody will be able to help me.
I recently got a power edge 1400 (oldies)
P3, 1256MB of ram and 3X36GB SCSI HDD

I have been trying for the last 3 days to install Ubuntu server (the last version) everything seem fine until the install ask me to reboot.

When the server reboot I have the following message:
Gave up waiting for root device. Common problem:
-Boot args (cat /proc/cmdline)
-Check rootdelay= (did the system wait long enough?)
-Check root= (did the system wait for the right device?)
-Missing modules (cat / proc/modules; Is /dev)
Alert! /dev/mapper/evpcsserver-root does not exist. Drooping to a shell!
BusyBox v1.10.2 Ubuntu 1:1,10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built in command.
(initrawfs)

So far I have not been able to start ubuntu.
Like I said I am very new at server and ubuntu (I am a PC tech but unfortunately not server yet)

Any help would be much appreciated.
Thank you
Eric.

---

### Post by HermanAB on 2009-01-02
So you can boot the live CD, but it won't install to the HDD properly.

I would try the usual tricks and add 'noapic nolapic acpi=off' to the kernel boot line.  I think you need to press Esc at boot up then type that - been a while since i had that kind of trouble.  Some googling for the above will get you going.

Eg:
[http://ubuntuforums.org/showthread.php?t=3000](http://ubuntuforums.org/showthread.php?t=3000)

Cheers,

Herman

---

### Post by cariboo on 2009-01-02
If your computer is all SCSI, try replacing the cdrom drive with an IDE, if you search this forum for dell+poweredge, I think you'll find that changing the cdrom drive is the path to a successful installation.

Jim

---

### Post by EVPCS on 2009-01-02
Thanks for the replies

I already tried the noapic install and the same thing happened,
same message.

Concerning the CDROM it is an IDE already only the HDD are SCSI
but I can try to change it and put a new one to make a try.

The thing is that the server does not find the boot to start ubuntu if I understand the error message.

Thanks anyway
more help would be appreciated
Thanks 
Eric.

---

### Post by Lori700698 on 2009-01-02
I just had this happen with a desktop install I'm working on tonight. (similar error)  The problem was the disk I burnt~go figure.  Anyway, re-burnt a new disk and slowed down the burn speed and re-installed.  Everything went fine until I got to the desktop (which this is not related to your problem at all), the computer I have is sadly slow even with Ubuntu Hardy, I was hoping for a little better performance than I was having with XP.  It's my mom's desktop and I guess we will be looking for an upgrade in the near future.

---

### Post by EVPCS on 2009-01-03
Thanks I am burning e new CD right now and will retry...
I let you know if that works
thanks again#-o

---

### Post by albinootje on 2009-01-03
> **EVPCS said:**
> 
Alert! /dev/mapper/evpcsserver-root does not exist. Drooping to a shell!

You configure RAID in the BIOS of that machine ?

Did you set up software RAID during the installation ?
If so, which one ?

Can you boot from the server cdrom.
Press alt-F2 after being in the first installation step.
"Copy and paste" the content of :
```

lspci
lshw -c storage -sanitize

```

---

### Post by EVPCS on 2009-01-03
The problem is that I didn't find any setup for the RAID (weird no?)
I also try in the SCSI adapter configuration nothing there neither.

How do you setup software raid in the install?
I type the code that you posted and I have several line displayed on my machine but don't understand exactly what it is for.

my scsi adapter is: AIC-7899P U160/M

I am almost done with the new CD image that I am burning at very slow speed on a XP machine.
previous one was burned on a Vista machine.

I wish to make this server working, not easy!

---

### Post by albinootje on 2009-01-03
> **EVPCS said:**
> The problem is that I didn't find any setup for the RAID (weird no?)
--- cut ---
my scsi adapter is: AIC-7899P U160/M
--- cut ---
I wish to make this server working, not easy!

The "power edge 1400" comes with RAID according to this :
> 
Whereas the 1300 provided a pair of Adaptec chipsets offering both Ultra/Narrow and Ultra2/LVD services, the 1400 now sports a dual-channel Adaptec AIC-7899G Ultra160 chipset. This is largely redundant on the review model as Dell opted to fit its PERC 2/DC PCI RAID controller card. Based around a full-length dual-channel AMI controller card, this fine piece of kit included the full 128Mb of cache memory and an on-board battery backup pack. Three 9Gb Quantum 10K Ultra160 hard disks are nestled in the large hard disk cage at the front and came configured in a RAID-5 array. The cage has room for one more drive, which is easily removed from the front of the server.


This link also talks about RAID on that machine :
[http://lists.us.dell.com/pipermail/linux-poweredge/2007-July/031968.html](http://lists.us.dell.com/pipermail/linux-poweredge/2007-July/031968.html)

Here's a posting about a similar (1400SC) without RAID controller :
[http://ubuntuforums.org/showthread.php?t=776730](http://ubuntuforums.org/showthread.php?t=776730)

Can you please check whether your machine is a 1400 or a 1400 something ?

And.. it is possible that those disk were used in a RAID configuration in the past, in that case you need to wipe the RAID signatures from them, if you really have a machine without hardware RAID options right now.

---

### Post by EVPCS on 2009-01-03
from the service tag this is a 1400SC

---

### Post by albinootje on 2009-01-03
> **EVPCS said:**
> from the service tag this is a 1400SC

Good :) That makes things easier. 

Please read this carefully :
[http://ubuntuforums.org/showthread.php?t=776730](http://ubuntuforums.org/showthread.php?t=776730)

---

### Post by EVPCS on 2009-01-03
alright I managed to install a raid 5 and a raid 0
I had an SCSI RAID card hidden somewhere in my office :-)

Now everything is installed...

The computer is booting asking me my login and Password then I have:
eric@evpcsserver:~$

What I am suppose to do?

Sorry but it's very new to me...

---

### Post by albinootje on 2009-01-03
> **EVPCS said:**
> alright I managed to install a raid 5 and a raid 0
I had an SCSI RAID card hidden somewhere in my office :-)

Now everything is installed...

The computer is booting asking me my login and Password then I have:
eric@evpcsserver:~$


Excellent! :)

> 
What I am suppose to do?

Sorry but it's very new to me...

Depends on what you want to do.
You want a webserver ? a samba server ? a ssh server ?

Here's something to read :
[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

---

### Post by EVPCS on 2009-01-03
I would like to have a server in my office that can manage the internet in my office (wired and wireless) and to be able to use this server for (if it's possible) backing up several application on different machines in my office.
just an internal server...
Something that you may want to know is that the rest of my machines are XP and 1 Vista.
All the XP machines are very powerful for video editing the Vista is only for office purpuse.

Let me know if all of that is possible but first I would like to see this server up and running.

Thank you in advance

---

### Post by albinootje on 2009-01-03
> **EVPCS said:**
> I would like to have a server in my office that can manage the internet in my office (wired and wireless) and to be able to use this server for (if it's possible) backing up several application on different machines in my office.
just an internal server...


So you want it to be a backup-server and a router.

I think that it makes more sense to let a Linksys or Asus wifi-box do the routing.
Much easier to set up, and no need to find and buy a wifi-card that works with Linux, to be put in your server machine.

For the backup part, start working to have Samba running.

This is pretty good to start with :
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by EVPCS on 2009-01-03
Ok I intalled Samba

Now I have a question (may a stupid one)
When I enter my login name and password; the system should start something correct?
Like XP when you login you have XP that start and you have the desktop and blabla...
Here the only thing i've got so far is a command line: eric@evpcserver:"$

and that's it.
the only thing I can do from there is enter sudo....

Am I missing something?

---

### Post by albinootje on 2009-01-03
> **EVPCS said:**
> Ok I intalled Samba

Now I have a question (may a stupid one)

No worries.
> 
When I enter my login name and password; the system should start something correct?

Well, before you log in to the txt mode (virtual console, or tty) on the server edition, the system should have already started all services.
> 
Like XP when you login you have XP that start and you have the desktop and blabla...
Here the only thing i've got so far is a command line: eric@evpcserver:"$

and that's it.
the only thing I can do from there is enter sudo....

Am I missing something?

The Ubuntu server installation only gives you a txt based setup in the end.
If you prefer to have a GUI on your server after all, go ahead, and do the following :
```

sudo apt-get update
sudo apt-get install ubuntu-desktop

```
After installing that you'll have a GUI as in the desktop edition.

---

### Post by EVPCS on 2009-01-04
Thank you so much, you've made my day :-)

Now one more question;
From the desktop where do you setup the network?

Anyway I have to redo the all thing because I think I messed up a little to much before reading your post; but no big deal, I starting to get to use to :-)

I have some updates available but I have already an error message:
E: dpkg was interrupted, you must manually run 'dpkg--configure-a' to correct the problem.
E:_cache->open()failed, please report.

So I am going to reformat the all thing and redo a brand new install :-)

Thank you so much again I will post later to tell you how the all thing is doing.

Cheers.

---

### Post by albinootje on 2009-01-04
> **EVPCS said:**
> Thank you so much, you've made my day :-)

Cool! ;-)
> 
Now one more question;
From the desktop where do you setup the network?

There should be the Network Manager icon visible on the top panel.
> 
Anyway I have to redo the all thing because I think I messed up a little to much before reading your post; but no big deal, I starting to get to use to :-)

I have some updates available but I have already an error message:
E: dpkg was interrupted, you must manually run 'dpkg--configure-a' to correct the problem.
E:_cache->open()failed, please report.

So I am going to reformat the all thing and redo a brand new install :-)

No, wait.. 
This is not MS-Windows

Please open a terminal, and perform :
```

sudo dpkg--configure-a
sudo apt-get -f install

```
That should be enough.

---

### Post by cacycleworks on 2009-01-05
> **albinootje said:**
> 
No, wait.. 
This is not MS-Windows

Hehehe, that's awesome.

@EVPCS: I basically use an ubuntu server in my office in a way similar to how you want to use yours. So, let me say some thoughts about how I use our computers to help you get more ideas. 

I have one linux computer that I use for a mysql server and internal web server. I do all kinds of random php/mysql programming on it to handle in-office information. It is also the master storage for information transfer between my website and our QuickBooks windows XP box. (It uses qodbc to transfer info from the linux mysql server into QB)

This same computer has a hard drive tray that is removable to the front of the chassis. Instead of a CD, it has the tray. I have 3 hard drives that I put in the trays. Occasionally, I will backup files from various places to that removable hard drive and then I rotate their usage. HDs not in use are stored off site.

At this moment, I'm using a winXP box for our office RAID, as it is already part of our workflow. It is in my plan to move it to a linux machine so that user access security can be implemented.

I have SSH and HTTP routed to internal linux servers from the office firewall, which gives me access to my local files. It is easy to have a server running openssh server, have the firewall route to it, and then IN this server, you "mount" hard drives from all over the office. And to mount a windows share on this server, you can use smbmount so that you can do things to that windows computer from your linux world. So from home, you can "SSH in to" the office and read any file. Or I can ssh into the work computer and send a document to the printer at work.

From your home linux computer, you can "mount" your office hard disk as a local drive and then access files at work as though they were right there. And it's all encrypted. 

I personally do not have a visual desktop installed on any of our servers, as anything I do on them is done via SSH command line from some other computer. In the computer room, there are a couple of monitors and keyboards that use KVM switches for when we have to use a locally connected "console". Which is rare. One of our "servers" is that winXP with the RAID. I have to use its monitor and keyboard once a week to restart it.

Linux is amazing at how easy it is to connect to other computers. There are no limits to what can be done.

:)
Chris

---

### Post by EVPCS on 2009-01-05
Thanks Chris and Happy New year!

And thank you and Happy New year to Albinootje as well who as been very helpful; I try the last command:
Code:
sudo dpkg--configure-a
sudo apt-get -f install

But the system failed so I did reformat the all thing, I am about to reload Ubuntu.

Now I have four HDDs in that machine; 3 X 36GB SCSI and 1 SCSI 18GB
What RAID config would you recomand and on which one would you put the OS?

I will find a way to add more storage later on but for now that should be enough.

I am working on it and let you know soon how the things are doing.

Concerning the desktop wich one do you recommend?
Ubuntu, Kubuntu or Xubuntu?

But I want to make sure that I will have all the command to setup my network properly from the desktop.

ok let's go to work :-)

Thank you Guys and Happy New Year!

---

### Post by albinootje on 2009-01-05
> **EVPCS said:**
> 
Now I have four HDDs in that machine; 3 X 36GB SCSI and 1 SCSI 18GB
What RAID config would you recomand and on which one would you put the OS?
-- cut --
Concerning the desktop wich one do you recommend?
Ubuntu, Kubuntu or Xubuntu? 

Happy new year, wishing all of you a beautiful and inspiring 2009!

About RAID :
============
RAID0 (striping) is only about speed, useful for gamers or an application server for example, but.. remember losing one disk in a RAID0 configuration means losing all of your data

RAID1 (mirroring) is aimed at enhancing security of your data. 
If one disk dies, you still have the full data on the other disk(s). 
You will lose a little bit performance because of the writing to the two or more disks.
 
RAID5 is a bit of a combination of RAID0 and RAID1.

For more information see here :
[http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks](http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks)

In your situation i would go for software RAID1, and test that.

Ubuntu variety :
================
If you're coming from Planet Microsoft then Kubuntu is perhaps a nice choice. 
Xubuntu is a bit nicer for older machines.
I prefer Ubuntu (Gnome desktop) myself since quite a while.

---

### Post by cacycleworks on 2009-01-06
> **EVPCS said:**
> 
Now I have four HDDs in that machine; 3 X 36GB SCSI and 1 SCSI 18GB
What RAID config would you recomand and on which one would you put the OS?

Concerning the desktop wich one do you recommend?
Ubuntu, Kubuntu or Xubuntu?


It is my personal preference to only RAID identical drives, so the 3 would be in a RAID and then the 18G gets the OS.

As far as desktop, that is a lot of a "feeling" or personal preference. I like how xubuntu looks and that it is simple, but I don't use it much because it seems stable on only one of my computers -- and that one is in storage, waiting for when the kiosk it is intended for is moved into production.

That leaves ubuntu and kubuntu ... gnome vs KDE. Every once in a while I will try gnome again to ensure that I do not miss anything. And each time, I just feel lost. KDE has so much configurability! And KDE has a lot of underlying connectivity. You can have remote "locations" that are ftp or whatever and they can be accessed from just about any other program.

And KDE4 is just getting started. I would suggest getting hooked on it and grow with it. :-) But try each of them. They're relatively easy to change between them with apt-get ... and if you keep /home on its own partition ... and always back up your home directory, it's easy to run a complete reinstall of the OS.

Chris

---


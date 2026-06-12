---
title: "What to do with this old PC?"
date: 2009-11-26
forum: The Cafe
---

### Post by kaldor on 2009-11-26
I found the first computer my family owned; an HP Pavilion 8550c with 96 MB of RAM, 20 GB hard drive and 500MHz processor. OS is Windows 98.

I plan on using it as a small storage server, but I of course want to run Linux or at least some other *nix. The Windows 98 install is  pretty well useless, as it takes up to 30 minutes to boot up, turning the computer off results in a freeze. To put you in perspective of how old this computer is, the most up-to-date browser on it is Netscape 4, which is also connected to the e-mail service we had long ago. Very old.

What OS should I load on this? Live CDs will not work due to the RAM (I assume). Does anyone have any experience/links to Linux on this computer? I'd like to be able to set up an SSH server or similar.

Any ideas?

---

### Post by Psumi on 2009-11-26
Test ReactOS and report to its devs.

---

### Post by kaldor on 2009-11-26
"but I of course want to run Linux or at least some other *nix"

I don't want a Windows clone. :(

---

### Post by Psumi on 2009-11-26
> **kaldor said:**
> "but I of course want to run Linux or at least some other *nix"

I don't want a Windows clone. :(

I would rather run a Windows clone than Windows or linux, especially when that Windows clone is MUCH safer than Windows.

Granted, they have yet to implement a user switch environment, meaning you only get one user, and that's an admin. But that will change eventually.

---

### Post by JBAlaska on 2009-11-26
Puppy or DSL (Damn Small Linux) should run ok on it

---

### Post by ZankerH on 2009-11-26
Try DSL or Puppy GNU/Linux.

---

### Post by -grubby on 2009-11-26
> **Psumi said:**
> I would rather run a Windows clone than Windows or linux

Yeah, I love ReactOS! It makes this pretty blue color often.

And at the OP, yeah, put a Linux server OS on it and use it for various server tasks.

EDIT: Oh! You asked for a specific OS. Let's see, Arch, Debian Server, Ubuntu Server?

---

### Post by RoestVrijStaal on 2009-11-26
I think *buntu won't install on this pc, because 128 MB RAM is recommend for Ubuntu server and Xubuntu. The alternate of Xubuntu could run on 64 MB RAM, but if you want to run it smoothly, 128+ MB is recommend.

Last years I had also a Win98 PC with 256 MB, but running Xubuntu on it was not really cool (but it worked) at all.

You could turn the pc into a FirewallBox, with for example m0n0wall.

I hope you could find some more memory modules, otherwise you could take out the hardware compontents you still could use (for example the HDD) and nuke the rest. Or maybe donating it to developing countries...

---

### Post by Kevbert on 2009-11-26
[[COLOR="Red"]Puppy[/COLOR]]("http://www.puppylinux.org/") will probably run OK. See requirements [[COLOR="Red"]here[/COLOR]]("http://puppylinux.org/wikka/MinReq").

---

### Post by cascade9 on 2009-11-26
> **kaldor said:**
> I found the first computer my family owned; an HP Pavilion 8550c with 96 MB of RAM, 20 GB hard drive and 500MHz processor. OS is Windows 98.

I plan on using it as a small storage server, but I of course want to run Linux or at least some other *nix. The Windows 98 install is  pretty well useless, as it takes up to 30 minutes to boot up, turning the computer off results in a freeze. To put you in perspective of how old this computer is, the most up-to-date browser on it is Netscape 4, which is also connected to the e-mail service we had long ago. Very old.

What OS should I load on this? Live CDs will not work due to the RAM (I assume). Does anyone have any experience/links to Linux on this computer? I'd like to be able to set up an SSH server or similar.

Any ideas?

30 minutes? Thats the original wik98 install I would bet. My much older computer (cyrix pr166+, 48MB, 2GB hdd) started faster than that with a fresh win98 install. About 5-7 minutes IIRC. I think your windows is rotten.

Mind you, even if you reinstalled win9x for a faster boot, its pretty useless these days. Well, I dont trust an OS with no security releases, so its a bad idea IMO anyway. 

You could try DSL (damn small linux)-

[http://distrowatch.com/table.php?distribution=damnsmall](http://distrowatch.com/table.php?distribution=damnsmall)
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

Then there is the 'try to make it workable as something else' solution. Go into the bios, turn off all the junk you wont need (serial ports, parallel port, etc.). Take the cover off and remove the hardware you wont need (pci modem, floppy drive, etc.). Try to find more RAM (pc100/pc133 is pretty cheap these days, even going to 128MB would help...256MB+ would really help). Its possible you could even upgrade the CPU (100mhz p3 or celeron only, porbably 800Mhz P3 would be the best option). 

You could pack it with a few PCI network cards- very cheap- and run it as smoothwall-

[http://distrowatch.com/table.php?distribution=smoothwall](http://distrowatch.com/table.php?distribution=smoothwall)
[http://www.smoothwall.org/](http://www.smoothwall.org/)

Its even possible that with a nvidia PCI card (8000 series or above), 256MB RAM and a p3-800 it would play HD video. Would make an interesting HT box. 

Or even throw a PCI SATA card, a 1TB drive and some form of linux you could use it as a backup server/streaming box.

---

### Post by kaldor on 2009-11-26
> 
EDIT: Oh! You asked for a specific OS. Let's see, Arch, Debian Server, Ubuntu Server?

I think they'd be far too heavy for a PC with 96 MB of RAM.


Puppy seems like it *might* work, but I still want to get an idea of all my options.

---

### Post by markp1989 on 2009-11-26
give a command line install of ubuntu (from alternative install cd, press f4 to select minimal install) , you shouldnt need much ram for a fileserver.

for cli only 96mb should be plenty, just dont throw too many tasks at it.

---

### Post by mkvnmtr on 2009-11-26
Ubuntu minimal install. You can add the server software of your choice with the install disk.

---

### Post by clanky on 2009-11-26
> **kaldor said:**
> Any ideas?

Burn it with fire.

Seriously if Windows is taking 30 minutes to boot the chances are that you have a problem with the hardware and that nothing will run reliably on it, if you still have the original system restore CD you could try to re-install windows which would give you an idea of what sort of state the hardware is in.

If windows re-installs successfully and the boot time is reduced then it might be worth trying to install some form of Linux, if not then the computer probably won't run anything without some surgery.

---

### Post by kaldor on 2009-11-26
> **clanky said:**
> Burn it with fire.

Seriously if Windows is taking 30 minutes to boot the chances are that you have a problem with the hardware and that nothing will run reliably on it, if you still have the original system restore CD you could try to re-install windows which would give you an idea of what sort of state the hardware is in.

If windows re-installs successfully and the boot time is reduced then it might be worth trying to install some form of Linux, if not then the computer probably won't run anything without some surgery.

Windows was installed around 1997-1998 and was used extensively up until around 2004; it's the original install, on an old PC, on an old OS, so I think it'd be normal for this to happen. I'll compare that to Puppy.


As for the other comments, I am going to look into the alternate install discs. Also, for more info, I do not require any GUI at all. The CLI will suffice just fine. But, having a very very lightweight window manager is a plus in case I need it.

---

### Post by JBAlaska on 2009-11-26
Just download Puppy and stick it on there, it will work fine and not take 30 min to boot lol

---

### Post by prshah on 2009-11-26
> **kaldor said:**
> 96 MB of RAM, 20 GB hard drive and 500MHz processor. 

I plan on using it as a small storage server, 

I'm running an (Ubuntu) email server, PHP-based Intranet on an AMD 450Mhz, 96MB RAM (64+32), 5GB IDE. Slow but manageable. I could not complete installation without working swap.

It really depends on what you want to "serve". Anything more than the above will be unrealistic. Streaming video is out of the question. Streaming audio may not be viable.

---

### Post by kaldor on 2009-11-26
I want a server to be able to share files with computers in my home without needing a flash drive, etc. I'd likely network it with SSH. I want the server to be accessible to my laptop and my 2 desktops while I am at home. 

Laptop runs on Ubuntu 
Desktop #1 runs on Mint
Desktop #2 runs Windows XP, but it is not my own (something for school required me to use one of their Windows-based computers due to standards)

---

### Post by prshah on 2009-11-26
> **kaldor said:**
> I want a server to be able to share files with computers in my home without needing a flash drive, etc. I'd likely network it with SSH. I want the server to be accessible to my laptop and my 2 desktops while I am at home. 


That it can handle easily; why not setup a home mail server for your family while you are at it?

SSH for file transfers may be a little slow; I suggest you use samba or NFS instead, unless you have a particular need for secured file transfers. Using SSH for admin work will be fine.

Why not also setup an FTP server for friends, family and colleagues to upload files to? Eg family events photos, etc.

---

### Post by Exodist on 2009-11-26
> **kaldor said:**
> I found the first computer my family owned; an HP Pavilion 8550c with 96 MB of RAM, 20 GB hard drive and 500MHz processor. OS is Windows 98.

I plan on using it as a small storage server, but I of course want to run Linux or at least some other *nix. The Windows 98 install is  pretty well useless, as it takes up to 30 minutes to boot up, turning the computer off results in a freeze. To put you in perspective of how old this computer is, the most up-to-date browser on it is Netscape 4, which is also connected to the e-mail service we had long ago. Very old.

What OS should I load on this? Live CDs will not work due to the RAM (I assume). Does anyone have any experience/links to Linux on this computer? I'd like to be able to set up an SSH server or similar.

Any ideas?

Install a non X install of Ubuntu (no gnome or xorg) then install xorg and something lite like Afterstep. Should run fine. I had a simular setup 11 years ago running Windowmaker with some old school gtk apts.

---

### Post by Grifulkin on 2009-11-26
FreeNAS or TinyCore seriously.  TinyCore is smaller than puppy or DSL and doesn't usually get mentioned in these forums.

---

### Post by Kevbert on 2009-11-27
> **Grifulkin said:**
> FreeNAS or TinyCore seriously.  TinyCore is smaller than puppy or DSL and doesn't usually get mentioned in these forums.

Wow, TinyCore only needs 32Mb minimum and MicroCore 48K according to one of the posts. Tinycore can be found [[COLOR="Red"]here[/COLOR]]("http://www.tinycorelinux.com/welcome.html").

---

### Post by K.Mandla on 2009-11-27
Assuming it's an i686, Arch will run like greased lightning on it. If you want something educational, you could go crackers and install Crux or something source-based. I use that on a 550Mhz Celeron and runs like a cat on fire.

As for uses. ...

[http://kmandla.wordpress.com/2007/09/14/things-to-do-with-an-old-computer/](http://kmandla.wordpress.com/2007/09/14/things-to-do-with-an-old-computer/) 
[http://kmandla.wordpress.com/2007/03/16/ten-things-you-can-do-keep-an-old-computer-useful/](http://kmandla.wordpress.com/2007/03/16/ten-things-you-can-do-keep-an-old-computer-useful/)

---

### Post by The Real Dave on 2009-11-27
> **kaldor said:**
> I found the first computer my family owned; an HP Pavilion 8550c with 96 MB of RAM, 20 GB hard drive and 500MHz processor. OS is Windows 98.

I plan on using it as a small storage server, but I of course want to run Linux or at least some other *nix. The Windows 98 install is  pretty well useless, as it takes up to 30 minutes to boot up, turning the computer off results in a freeze. To put you in perspective of how old this computer is, the most up-to-date browser on it is Netscape 4, which is also connected to the e-mail service we had long ago. Very old.

What OS should I load on this? Live CDs will not work due to the RAM (I assume). Does anyone have any experience/links to Linux on this computer? I'd like to be able to set up an SSH server or similar.

Any ideas?

I've installed Ubuntu 9.10 server on a 451Mhz PIII with 64Mb RAM, and a 6Gb HDD. It uses around 30Mb. Give it a shot :) You won't have anything graphical, but SSH and samba can be set up automagically in the install :) 

Before I tried Ubuntu Server, I worked on making a custom DSL server edition using [these]("http://home.comcast.net/~dsbonnell/NAS_Files/NAS-server.html#links") instructions. Never did get it quite right though. 

BTW, FreeNAS will also work great on that hardware, I use it on two (admittedly much more powerful) servers, but its been on that 451Mhz PIII too, worked fine. I would advise using it in the LiveCD method, ie, booting the CD, configuring it, then letting it reboot. As it does that, it'll save the config to a floppy, or USB key, and after rebooting, reads the config, sets itself up, and loads into RAM. :) Means that you can set the HDDs to spin down after a while, saving power, heat, noise and wear.

---

### Post by Joe Ker1086 on 2009-11-28
I have a pretty old pc too.....was tryin to find a use for it and Tiny Core looks like a pretty good choice for a mini server.

---

### Post by jdarias on 2009-11-28
If you want a storage server only, you can go with [www.freenas.org](www.freenas.org). It runs freebsd but their developers are currently migrating into a debian based system, wich will be corenas.
I have an old laptop with just 128 ram and 5 gb hdd, and freenas in it. The installation size is very small 128 mb, and i have it running samba, ftp and bittorrent. It has a lot of services too, itunes, webserver, etc. They all are activated and configured with a nice webui.

---

### Post by ssam on 2009-11-28
measure how much power it uses. if its 100 watts, then it will cost about $100 per year to run.

instead you could spend $100 on a beagleboard or sheeva plug, that could do all the same work, and only use a couple of watts.

---

### Post by clubsoda on 2010-04-08
As RoestVrijStaal suggested, it's the memory which is key. Plug in a couple of 128MB SDRAMs and you should be able to install just about anything. Some of those old machines exceed the manufacturer's specifications. Upgrade the BIOS and you might get 512MB of RAM in there.

You can unclog Win98 by installing the latest Intel chipset drivers, which will force re-detection of your hardware and should fix the slow start-up. Sorry to say it but for general usage you won't do better than Win98 on that machine. Add [KernelEx](http://sourceforge.net/projects/kernelex/) and Firefox 3 and you'll be in business.

But I guess my reply is too late. What did you end up doing with it?

---

### Post by Eestlane on 2010-04-08
Install server only.

---

### Post by Warpnow on 2010-04-08
Slitaz kicks DSL/Puppy's *** for experienced linux users. Puppy is really good for being easy and simple, but people familar with linux will probably find slitaz more comfortable.

---

### Post by old fert on 2010-04-08
If it was running windows 98, it probably has pc133 memory.  I just repurposed an old AMD 400 box last week.  It had 128 mb of ram, but was entirely too slow.  See if you can find some more ram.

I salvaged a couple of 256 mb sticks from some old computers and did an online install of xubuntu (cd wouldn't install).  

It is a good internet browser, word processor, etc.  It's going to one of my grandkids or one of the neighborhood kids who doesn't  have a computer. 

Good luck.  It's a shame to waste an old computer.

---

### Post by themarker0 on 2010-04-08
> **Psumi said:**
> Test ReactOS and report to its devs.

I second that if you want to help them...

If you don't want to, and just want a file server put freebsd 4 or 5 on it. Works like a charm for me.

---

### Post by Khakilang on 2010-04-08
I too had a similar spec computer but its a clone so I upgrade to 384MB RAM and install Ubuntu 9.10. It work fine so I may be use it to test other Distro and put it to good use.

---

### Post by swoll1980 on 2010-04-08
Will it blend?

---


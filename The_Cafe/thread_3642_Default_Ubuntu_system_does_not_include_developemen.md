---
title: "Default Ubuntu system does not include developement tools"
date: 2004-11-08
forum: The Cafe
---

### Post by jvzsys on 2004-11-08
Reaction from Clarion NewsGroups. Help me out here - the good people of the Ubuntu Forums
Johan van Zyl

Default Ubuntu system does not include developement tools.  If you need 
to do your own compilation for wine, or even the kernel yourself, it 
will be a difficult task.  You will have to download all the required 
development tools and install them yourself.  And... in most cases, 
conflicts between the different libraries will eventually kill all your 
enthusiasm.

I downloaded many distros and still stick to Fedora because I need to 
compile programs in gcc.  As a File Server, I would dare say SME Server 
is the lightest.  It all depends on your requirements.  But... through 
logical thinking, after a while, I may be more inclined towards Suse in 
long term aspect.

Well... you can also obviously get it from their repository, in package 
called 'build-essential', by simply running 'apt-get install 
build-essential'

Thanks.

Kelvin Chua
SINGAPORE

---

### Post by jdodson on 2004-11-08
i had to install gcc off the ubuntu CDS.  its there, just have to dig around either synaptic or apt-get, but gcc is included.  i had to build ndis-wrapper(cause i had no internet connection to install the packages from).  gcc on the ubuntu cd seemed fine for me and what i need to build(which isnt much to be fair).  however you can install most of the gcc libraries off the ubuntu repositories, i guess i would take ubuntus package manager for fedoras in a heartbeat, that might just be me though.

---

### Post by ubuntu-geek on 2004-11-08
[QUOTE=jdodson]i had to install gcc off the ubuntu CDS.  its there, just have to dig around either synaptic or apt-get, but gcc is included.  i had to build ndis-wrapper(cause i had no internet connection to install the packages from).  gcc on the ubuntu cd seemed fine for me and what i need to build(which isnt much to be fair).  however you can install most of the gcc libraries off the ubuntu repositories, i guess i would take ubuntus package manager for fedoras in a heartbeat, that might just be me though.[/QUOTE]
 I have compiled lots of apps without a hitch, If I need a development package i just install it. Someone correct me if I am wrong, but I believe Ubuntu left out the development packages to keep the installer down to 1 cd, also tons of applications are available in the Universe so the need to compile most programs is limited.

I personally like the fact all the extra junk is not installed.

---

### Post by kastorff on 2004-11-08
Can't please everyone...I'm sure some thought went into what would/could be included on a single CD. I personally love the approach...put together a good solid working desktop, and let the user fill it out as they choose.

---

### Post by ubuntu-geek on 2004-11-08
[QUOTE=kastorff]Can't please everyone...I'm sure some thought went into what would/could be included on a single CD. I personally love the approach...put together a good solid working desktop, and let the user fill it out as they choose.[/QUOTE]
 Well said..

---

### Post by zenwhen on 2004-11-08
Fire up synaptic, reload the repo listings, and install build-essential. 

How hard is that?

---

### Post by Klunk on 2004-11-10
At the end of the day, most people are downloading the iso image and burning it. I would, therefore, presume that most people have some sort of broadband link. Hence having to download a few packages is no great problem. That is certainly the case as far as I am concerned.

Slghtly off topic but ...

I am a total newbie to Ubuntu after using slackware (about 9 years ago) followed by Red Hat 5.2 (i386 and sparc), Red Hat 6.x, Red Hat 7.x and then Red Hat 8.0. I had been running Red Hat 8.0 as a pure server install, no X but with DHCP, JBoss, Apache, OpenLDAP and mail server. I wanted to bring my (perfectly working) system 'up to date' and after being recommended Ubuntu on the GLLUG mailing list. I did a clean install onto a new disk and it worked out of the box. I had to reconfigure my graphics card (actually swapped it for a spare to get the right resolution) and swap my soundcard to a spare one I had. The server elements migrated seamlessly. I for one would recommend Ubuntu on first impressions, I have never had a working Linux install so soon after upgrading.

---

### Post by jdodson on 2004-11-10
[QUOTE=kastorff]Can't please everyone...I'm sure some thought went into what would/could be included on a single CD. I personally love the approach...put together a good solid working desktop, and let the user fill it out as they choose.[/QUOTE]

yep, strange as when i have a 4 cd distro i install practically everything and use literally nothing:)  ok well xorg, gnome, firefox, rhythmbox, gedit, gnome-terminal, apache/mysql/php, python, gcc, g++, gaim, gftp, ssh, sftp... but thats about it.  oh and some games at times:)

---

### Post by eNiNjA on 2004-11-11
i have compiled darn near anything...on a clean ubuntu install.
 
 sure, i had **sudo apt-get install build-essential **heh..but that was it, the rest was up to me, as it should be.
 
 just like any unix/linux/ix, if i wanted it done right, i had to read, search, find the requirements, put them were i know where they are at, and link them together accordingly, to ever expect them to function right..

---

### Post by HiddenWolf on 2004-11-11
[QUOTE=ubuntu-geek]I have compiled lots of apps without a hitch, If I need a development package i just install it. Someone correct me if I am wrong, but I believe Ubuntu left out the development packages to keep the installer down to 1 cd, also tons of applications are available in the Universe so the need to compile most programs is limited.

I personally like the fact all the extra junk is not installed.[/QUOTE]

Amen. 
It is definatly possible to get every possible compiler from universe, but why would a desktop distribution want to install it by default?

Anyone who can compile, can certainly use apt to install a compiler.

---


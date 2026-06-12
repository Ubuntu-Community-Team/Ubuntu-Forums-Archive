---
title: "Things are getting worse and worse and ..."
date: 2005-12-05
forum: The Cafe
---

### Post by obi22 on 2005-12-05
Hi all!
I'm a Linux beginer but not a computer lamer (started with ZX Spectrum). 
However since I've installed Ubuntu 5.10 I'm spending all my free time trying to tweak linux my way (the only right way).
And what?
-Nothing! My only success so far is mounted properly FAT32 partition!

So, I'm wondering:
-Why FireFox is so tought to install, why do I need to install klik or automatix , why should I even know about /opt/ directory existence? (and don't tell me about source code reutilizing - linux version 8,2MB vs. 5,9MB windows)
-Why do I need to mess with config files to get NumLock enabled afther boot, and manually setting DMA in 21st century?
-Why root account is disabled by default - I'm sure not for safety reasons, because 
only thing you can do with user privilages is browsing WWW with old, slow and not practical FireFox 1.07.

Cheers

---

### Post by 23meg on 2005-12-05
> **obi22]
-Why FireFox is so tought to install, why do I need to install klik or automatix , why should I even know about /opt/ directory existence? (and don't tell me about source code reutilizing - linux version 8,2MB vs. 5,9MB windows)[/quote] If you mean Firefox 1.5, you don't need klik or automatix (which in themselves are made for ease of use). You don't need to know what the /opt directory is either said:**
> http://wiki.ubuntu.com/FirefoxNewVersion[/url] to your terminal.
[QUOTE=obi22]-Why do I need to mess with config files to get NumLock enabled afther boot, and manually setting DMA in 21st century?I didn't need to do anything get numlock enabled in my system. So haven't most others I suppose, so it must be a problem specific to your configuration. As for DMA, I'm not sure, since I don't use IDE drives; others will be able to explain better why (or * if*) it's not enabled in a default Ubuntu insatllation.
[QUOTE=obi22]-Why root account is disabled by default - I'm sure not for safety reasons, because 
only thing you can do with user privilages is browsing WWW with old, slow and not practical FireFox 1.07.[/QUOTE]It's for security reasons. Ubuntu finds this security model suited to its goals and its target audience. If you'd like to use Ubuntu, you'll have to live with this *as a default*. And you can do, and are supposed to do, most things you normally do without root privileges, not just use Firefox. All you need root for is system-wide changes and operations.

---

### Post by Terry of Astoria on 2005-12-05
Sorry you're not having as good a time as I am. I've never used a ZX Spectrum but I know what I like and it's Ubuntu. I don't know the answers to all your questions, but I think the root account is disabled because somehow the developers thought that Ubuntu might be easier for a newcomer to use that way. It's easy to create a root password and 'enable' the root account. You just "sudo passwd root".

---

### Post by obi22 on 2005-12-05
> **Terry of Astoria]It's easy to create a root password and 'enable' the root account.[/QUOTE]
I did it  said:**
> 

[QUOTE=23meg]It's for security reasons. Ubuntu finds this security model suited to its goals and its target audience. If you'd like to use Ubuntu, you'll have to live with this as a default. And you can do, and are supposed to do, most things you normally do without root privileges, not just use Firefox.
Take a look at any wiki or howto - sudo in every line

...and I really would like to use Ubuntu fitted as a pair of glowes

---

### Post by TeeAhr1 on 2005-12-05
I've got the NumLock problem going on too, it's driving me nuts.  The worst is when I forget that it doesn't come on at startup and try to use it.

What's the probem with Firefox?  I just untarred it and ran.

I actually like having root disabled.  I have roommates on my computer quite often, and it makes a nice idiotproofing layer.  "If it asks you for a password, you shouldn't be doing it to my computer."  If you're sure you want to enable root, it's easy.  Follow the advice upthread.

---

### Post by obi22 on 2005-12-05
[http://ubuntuguide.org/#numlockx](http://ubuntuguide.org/#numlockx)

but again sudo, sudo, sudo

[QUOTE=TeeAhr1]What's the probem with Firefox? I just untarred it and ran.[/QUOTE]
It really doesn't work for me, don't know what the problem is

---

### Post by 23meg on 2005-12-05
> **obi22]I did it  said:**
> 


Take a look at any wiki or howto - sudo in every line

...and I really would like to use Ubuntu fitted as a pair of glowes
Sudo has a grace period, which is 15 minutes by default, and is adjustable. So you don't need to enter your password every time, and since you're copying and pasting from guides, you'll not have to type sudo either. 

And since you enabled the root account as well, if you're typing lots of commands in the terminal that require sudo, you can use "su" instead, and log out of root when you're done.

---

### Post by 23meg on 2005-12-05
[QUOTE=obi22][http://ubuntuguide.org/#numlockx](http://ubuntuguide.org/#numlockx)

but again sudo, sudo, sudo[/quote]When you're making system-wide changes you'll have to bear with sudo as long as you're not logged in as root, period. This is how it is in Ubuntu (actually just about every other distro as well), and won't change. 

[QUOTE=obi22]
It's really doesn't work for me, don't know what the problem is[/QUOTE]
Maybe you should describe how exactly the procedure in [http://wiki.ubuntu.com/FirefoxNewVersion](http://wiki.ubuntu.com/FirefoxNewVersion) fails for you, along with the exact errors you're getting, in an appropriately titled thread.

---

### Post by obi22 on 2005-12-05
I didin't follow exactly every step wiki's howto, but TeeAhr1 says that the only thing should be done is extract tar file (and mozilla.org too), but afther clicking firefox nothing happens?!

---

### Post by dweez on 2005-12-05
Did you see this line of the [wiki]("https://wiki.ubuntu.com/FirefoxNewVersion")?
> You need package 'libstdc++5' installed.

My first attempt at getting FF 1.5 going was similar to your's.  Click on it and nothing happened.  After I installed libstdc++5, it worked.

---

### Post by 23meg on 2005-12-05
[QUOTE=obi22]I didin't follow exactly every step wiki's howto[/QUOTE]Why not?

---

### Post by obi22 on 2005-12-05
Because I opposite to You do not prefer copy-paste method when I don't know what does it mean (Don't get me wrong I don't want to be rude it's just my weak english) and as I can figure what is going out there there isn't any special moves :confused: exept dpkg witch i don't understand. 

Thanks dweez, libstdc++5 might be a problem - i don't have it installed so far :o  I've checked other nessesary libs, but this one is listed at last and i didn't check it -> Please kill me, I'm an idiot!

-----------------------------------------------------
**This one is written from FF1.5 ;]**
libstdc++5 wasn't installed, damn what a shame!
but look at all this threads about FF installation, no one said it loud and clearly "You don't have libstdc++5 in your system by default" **only You DWEEZ**, you've saved one Linux user!

---

### Post by aysiu on 2005-12-05
[QUOTE=obi22]
-Why FireFox is so tought to install, why do I need to install klik or automatix , why should I even know about /opt/ directory existence? (and don't tell me about source code reutilizing - linux version 8,2MB vs. 5,9MB windows)[/quote] It's not. In fact, in Ubuntu it comes preinstalled, unless you want version 1.5.

> 
-Why do I need to mess with config files to get NumLock enabled afther boot You don't. If it's such a big deal, use KDE. 

> and manually setting DMA in 21st century? I read somewhere that it has to do with it messing up some people's systems if it's enabled by default.

> 
-Why root account is disabled by default - I'm sure not for safety reasons, because 
only thing you can do with user privilages is browsing WWW with old, slow and not practical FireFox 1.07. I'm using 1.0.7 now, and it's just fine. Read more here: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Incidentally, this is the security model Mac OS X uses, and none of the Mac users complain.

---

### Post by 23meg on 2005-12-05
Well, I'd say don't worry about anything on the official wiki and other well regarded unofficial places doing damage to your system. Just follow every step on that guide and you'll get firefox 1.5.

---

### Post by ssam on 2005-12-05
i quite like the sudo thing.

if you want to be able to use it without typing your password then you can have a play in the sudoers file.

i use
```
sudo su
```
when i need a shell.

in someways it is more secure than enabling root. (see [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) )

---

### Post by obi22 on 2005-12-05
[QUOTE=aysiu]It's not. In fact, in Ubuntu it comes preinstalled, unless you want version 1.5.[/QUOTE]
really??

[QUOTE=aysiu]You don't. If it's such a big deal, use KDE.[/QUOTE]
from your link:
*It is generally recommended that you do not run applications with root privileges, but if you have to, it is recommended that you do not run "sudo {GUIAPP}", as sudo may not set up the environment correctly, and particularly **on KDE this can be detrimental**.*
I prefer to stay with Gnome - I like it even without NumLock btw I'm going to fix it some day.
[QUOTE=aysiu]I read somewhere that it has to do with it messing up some people's systems if it's enabled by default.[/QUOTE]
but 64bit Ubuntu version is avilable, don't you affraid it can mess some people systems

[QUOTE=aysiu]I'm using 1.0.7 now, and it's just fine.[/QUOTE]
most comfortable for me is Maxthon on wINDOWS

[QUOTE=aysiu]Incidentally, this is the security model Mac OS X uses, and none of the Mac users complain.[/QUOTE]
I have a big respect for Mac OS

Thank You All for your time and help, for now i'm still determined to stay with linux.

---

### Post by erikpiper on 2005-12-05
Wht don't you use automatix? It is ALMOST command line free- and it works. There is also a new script to install FF 1.5 in he tips/tricks section by arnieboy- to guy eho made automatix. It works great! (All the bugs are now gone)

[http://www.ubuntuforums.org/showthread.php?t=99004](http://www.ubuntuforums.org/showthread.php?t=99004)

---

### Post by TeeAhr1 on 2005-12-05
[QUOTE=obi22][http://ubuntuguide.org/#numlockx](http://ubuntuguide.org/#numlockx)[/QUOTE]
Thx!

---

### Post by gord on 2005-12-05
ahh if only things were as simple as the good old specky -_-

stick in the tape, type:
LOAD ""

press play! genius!

---

### Post by aysiu on 2005-12-05
[QUOTE=obi22]
from your link:
*It is generally recommended that you do not run applications with root privileges, but if you have to, it is recommended that you do not run "sudo {GUIAPP}", as sudo may not set up the environment correctly, and particularly **on KDE this can be detrimental**.*[/quote] Which link is this? In any case, there is a recommendation in place of that: gksudo {GUIAPP} for Gnome or kdesu {GUIAPP} for KDE.

> 
I prefer to stay with Gnome - I like it even without NumLock btw I'm going to fix it some day. You know, I actually just did a fresh install of Ubuntu today for fun, and installing numlockx did the trick. I didn't have to fiddle at all with the config file. I wonder if something's changed or if the Ubuntu Guide just had that extra step for some other reason.

> 
but 64bit Ubuntu version is avilable, don't you affraid it can mess some people systems But people have the choice of whether to use the 64-bit version or the x86 version. If every version came with DMA enabled, people wouldn't have a choice before it messed up their systems.

> 
most comfortable for me is Maxthon on wINDOWS I'm not sure if you can do it successfully, but maybe you can try running that with Wine.

> 
Thank You All for your time and help, for now i'm still determined to stay with linux. Great. Keep in mind, though that Ubuntu is not Linux. It's an operating system that uses the Linux kernel. If, for some reason, you don't like Ubuntu in the end, consider trying another Linux distribution--they really are different from each other.

---

### Post by erikpiper on 2005-12-05
[QUOTE=obi22]really??
[/QUOTE]

Internet > Firefox- How do you miss it :confused:

---

### Post by obi22 on 2005-12-06
[QUOTE=gord]ahh if only things were as simple as the good old specky -_-

stick in the tape, type:
LOAD ""

press play! genius![/QUOTE]

hehe It was even simpler, ctrl + P gave PRINT and then just type "" 
that's how it was on my TIMEX 2048 sixteen years ago :razz:

---

### Post by prizrak on 2005-12-06
This is kinda weird but I had DMA enabled by default on my laptop (never bothered to check the desktop) with a Breezy install.

---


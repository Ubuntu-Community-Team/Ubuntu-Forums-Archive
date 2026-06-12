---
title: "FreeBSD failure."
date: 2005-12-22
forum: The Cafe
---

### Post by xequence on 2005-12-22
Ok, I resized my windows partition to six GB and made a new one for FreeBSD (also 6 GB). When I installed freebsd two things went wrong - 1: It didnt include a GUI. I had to go and install a whole bunch of things, and even after getting Xorg and Gnome, when I did startx it brought up "Twm" which is to me, unuseable and horrible. Second, it killed my windows installation. I have no idea how or why, but it did... (I couldent boot up windows. It said something like (windows root system) could not find ntoskernel.exe).

Oh, how I was looking forward to trying freebsd :/

---

### Post by Sheco on 2005-12-22
and this forum is related to freebsd in which way?

---

### Post by Adrian on 2005-12-22
[QUOTE=xequence]Ok, I resized my windows partition to six GB and made a new one for FreeBSD (also 6 GB). When I installed freebsd two things went wrong - 1: It didnt include a GUI. I had to go and install a whole bunch of things, and even after getting Xorg and Gnome, when I did startx it brought up "Twm" which is to me, unuseable and horrible. Second, it killed my windows installation. I have no idea how or why, but it did... (I couldent boot up windows. It said something like (windows root system) could not find ntoskernel.exe).[/QUOTE]

I remember that installing a DE in Freebsd wasn't very simple. But there are very good instructions in the Freebsd handbook:
[http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/)
Most of the problems I had were solved by reading that excellent manual, and I managed to make Gnome and KDE to work nicely (and I learned a lot on the way!).

Maybe you want to check out [DesktopBSD]("http://www.desktopbsd.net/") and [PC-BSD]("http://www.pcbsd.org/")...?

[QUOTE=Sheco]
and this forum is related to freebsd in which way?[/QUOTE]
Well, we're in the "Community Chat" section after all, aren't we?

---

### Post by BSDFreak on 2005-12-22
[QUOTE=xequence]Ok, I resized my windows partition to six GB and made a new one for FreeBSD (also 6 GB). When I installed freebsd two things went wrong - 1: It didnt include a GUI. I had to go and install a whole bunch of things, and even after getting Xorg and Gnome, when I did startx it brought up "Twm" which is to me, unuseable and horrible. Second, it killed my windows installation. I have no idea how or why, but it did... (I couldent boot up windows. It said something like (windows root system) could not find ntoskernel.exe).

Oh, how I was looking forward to trying freebsd :/[/QUOTE]

Three things, run gdm or KDM or change your config files in your home directory to start the WM of your choice. You can ALWAYS rerun sysinstall, just boot and type sysinstall and get what you were missing from the other install.

You most probably moved your partition numbers around and that is why you can't start XP anymore, edit the boot file and supply the correct number, you'll find the number by running cfdisk in FreeBSD.

You're not going to give up this easy, are you?

---

### Post by BSDFreak on 2005-12-22
[QUOTE=Adrian]I remember that installing a DE in Freebsd wasn't very simple. But there are very good instructions in the Freebsd handbook:
[http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/)
Most of the problems I had were solved by reading that excellent manual, and I managed to make Gnome and KDE to work nicely (and I learned a lot on the way!).

Maybe you want to check out [DesktopBSD]("http://www.desktopbsd.net/") and [PC-BSD]("http://www.pcbsd.org/")...?


Well, we're in the "Community Chat" section after all, aren't we?[/QUOTE]

It's as easy as selecting the DE in sysinstall, it will install dependencies and it will work just fine.

As an aside, if you like windows, you're going to love any of those flavors, they are striving to be almost as good as windows at doing what windows does, otoh, why the heck would you want a second grade windows if you already have XP?

---

### Post by xequence on 2005-12-22
> and this forum is related to freebsd in which way?

And I said this forum was related to FreeBSD when?

> Three things, run gdm or KDM or change your config files in your home directory to start the WM of your choice. You can ALWAYS rerun sysinstall, just boot and type sysinstall and get what you were missing from the other install.

I reran sysinstall many many times. And I typed in GDM and it said it wasnt a valid command.

> You're not going to give up this easy, are you?

I had to have windows running by today for my little brother, so I deleted it and reinstalled windows :P

> I remember that installing a DE in Freebsd wasn't very simple. But there are very good instructions in the Freebsd handbook:
[http://www.freebsd.org/doc/en_US.ISO...ooks/handbook/](http://www.freebsd.org/doc/en_US.ISO...ooks/handbook/)
Most of the problems I had were solved by reading that excellent manual, and I managed to make Gnome and KDE to work nicely (and I learned a lot on the way!).

Maybe you want to check out DesktopBSD and PC-BSD...?

Ill probably try PC-BSD sometime. And the handbook really didnt tell me anything helpful, though I was probably looking in the wrong place :P

---

### Post by DevilsAdvocate on 2005-12-22
BSDFreak, have you tried PCBSD?  I know very little about BSD but got this up and running w/ ease.

Just saw your last post about PCBSD...it's very nice.

---

### Post by canadianwriterman on 2005-12-22
I think your problem is that FreeBSD is run by the Liberals and supported by the NDP!

---

### Post by BSDFreak on 2005-12-22
> **xequence]And I said this forum was related to FreeBSD when?



I reran sysinstall many many times. And I typed in GDM and it said it wasnt a valid command.[/QUOTE]


KDM is the standard for FreeBSD, just type kdm.

> I had to have windows running by today for my little brother, so I deleted it and reinstalled windows :P

Wimp.  said:**
> Ill probably try PC-BSD sometime. And the handbook really didnt tell me anything helpful, though I was probably looking in the wrong place :P

You did this the wrong way, have a plan before you install, read the docs before you install, KNOW what you want to install and it WILL work for you.

---

### Post by BSDFreak on 2005-12-22
[QUOTE=DevilsAdvocate]BSDFreak, have you tried PCBSD?  I know very little about BSD but got this up and running w/ ease.

Just saw your last post about PCBSD...it's very nice.[/QUOTE]

Yes i have, and sure it is nice, for a windows user, for a BSD user it's hell.

It has separate installation programs for apps which are then NOT upgradable via the ports or CVSUP systems, it aims to be almost as good as windows and i'm sorry but that isn't what i'm looking for in an OS.

---

### Post by canadianwriterman on 2005-12-22
[QUOTE=BSDFreak]KDM is the standard for FreeBSD, just type kdm.



Wimp. ;)





You did this the wrong way, have a plan before you install, read the docs before you install, KNOW what you want to install and it WILL work for you.[/QUOTE]

Let's be kind to strangers. Who knows, they might come over to our side some time!

---

### Post by xequence on 2005-12-22
> KDM is the standard for FreeBSD, just type kdm.

Wow. That was probably where it went all wrong :K

> Wimp. 

Probably. But my brother gets really mad when he cant play runescape :P

> It's as easy as selecting the DE in sysinstall, it will install dependencies and it will work just fine.

As an aside, if you like windows, you're going to love any of those flavors, they are striving to be almost as good as windows at doing what windows does, otoh, why the heck would you want a second grade windows if you already have XP?

I have an install disk of XP but I dont use it. Its too slow. I use 2000.

> Yes i have, and sure it is nice, for a windows user, for a BSD user it's hell.

It has separate installation programs for apps which are then NOT upgradable via the ports or CVSUP systems, it aims to be almost as good as windows and i'm sorry but that isn't what i'm looking for in an OS.

What accually is ports? Is it like apt on ubuntu?

---

### Post by DevilsAdvocate on 2005-12-22
[QUOTE=BSDFreak]Yes i have, and sure it is nice, for a windows user, for a BSD user it's hell.

It has separate installation programs for apps which are then NOT upgradable via the ports or CVSUP systems, it aims to be almost as good as windows and i'm sorry but that isn't what i'm looking for in an OS.[/QUOTE]

I suspected you might feel that way.  Excellent.

---

### Post by Iandefor on 2005-12-22
Sorry to hear FreeBSD didn't work out. I know you'd been planning on trying it out... oh well, better luck next time, eh?

---

### Post by xequence on 2005-12-22
> I think your problem is that FreeBSD is run by the Liberals and supported by the NDP!

If that was true, id never even consider trying it :P

> Sorry to hear FreeBSD didn't work out. I know you'd been planning on trying it out... oh well, better luck next time, eh?

Yea =) I am probably going to try again in a week when I have all day to mess around and try to get it working. I was just too rushed last night trying to do stuff ;)

---

### Post by BSDFreak on 2005-12-22
[QUOTE=xequence]Wow. That was probably where it went all wrong :K[/QUOTE]

Maybe, but hey, you live and learn. :)



> Probably. But my brother gets really mad when he cant play runescape :P

Hey, i know i usually forget smileys but i did put one after that, i wasn't serious and i did understand your dilemma. 



> I have an install disk of XP but I dont use it. Its too slow. I use 2000.

You are really just begging for viruses and spyware, aren't you?

> What accually is ports? Is it like apt on ubuntu?

Exactly, the ports system is a great piece of software that works just like apt-get, if you like aptitude, you are going to love portsman.

The updating of the entire system are described in the handbook, look for cvsup and how to use it, learn to recompile your kernel and one thing is for sure, no matter WHAT you have used before, Windows, Linux, OSX, NOTHING even comes close to the responsiveness and speed of FreeBSD.

---

### Post by prizrak on 2005-12-22
BSD confused the hell out of me, I think I used Open not Free though. I really can't remember what it was. I just know that I knew how to use Linux and tried the same things with it and it didn't work :(

---

### Post by xequence on 2005-12-22
> You are really just begging for viruses and spyware, aren't you?

I accually got more viruses in XP for some odd reason. Never had one in 2000. Besides, XP is too slow to play unreal tournament ;)

> Hey, i know i usually forget smileys but i did put one after that, i wasn't serious and i did understand your dilemma.

Its ok ;)

---

### Post by BSDFreak on 2005-12-22
[QUOTE=prizrak]BSD confused the hell out of me, I think I used Open not Free though. I really can't remember what it was. I just know that I knew how to use Linux and tried the same things with it and it didn't work :([/QUOTE]

OpenBSD is very different, set up right it's the most secure OS on the planet but to get it configured and even working the way you want it takes an administrator.

It's getting better though, if you want a system that is absolutely secure and where you are in complete control, OpenBSD is it.

Most linux distros use the sysV init, try Slackware (which uses the BSD init) to ease into it, not that that is much easier to configure but at least you'll be in the same water as you are with other Linux distros.

---

### Post by BSDFreak on 2005-12-22
> **xequence]I accually got more viruses in XP for some odd reason. Never had one in 2000. Besides, XP is too slow to play unreal tournament  said:**
> 

All spyware and viruses work just as well in both OS's natively, the difference is SP2 for XP, streamline it or just keep it handy to install before you connect to the net, NEVER even connect to the net without that or another firewall active.



[QUOTE]Its ok ;)

Looking up i see that you'll probably try it again, i think that is great, the FOSS world definently needs more people like you.

---

### Post by xequence on 2005-12-22
> All spyware and viruses work just as well in both OS's natively, the difference is SP2 for XP, streamline it or just keep it handy to install before you connect to the net, NEVER even connect to the net without that or another firewall active.

My XP install CD is SP1 as far as I know. I did an install of XP once and it got a virus in 10 minutes.

> Looking up i see that you'll probably try it again, i think that is great, the FOSS world definently needs more people like you.

I really hope I can get it working ;)

---

### Post by BSDFreak on 2005-12-22
[QUOTE=xequence]My XP install CD is SP1 as far as I know. I did an install of XP once and it got a virus in 10 minutes.



I really hope I can get it working ;)[/QUOTE]

You are welcome to contact me with any questions on BSD, i'll help you if i can. :)

---

### Post by poofyhairguy on 2005-12-22
[QUOTE=Sheco]and this forum is related to freebsd in which way?[/QUOTE]


No way. But its community chat so talking about Freebsd is fair game.

---

### Post by xequence on 2005-12-22
> 
No way. But its community chat so talking about Freebsd is fair game.

Yea =O

> You are welcome to contact me with any questions on BSD, i'll help you if i can. 

Thanks for the offer, I'll probably PM you around the time I try the install again :)

---

### Post by prizrak on 2005-12-23
[QUOTE=xequence]Yea =O



Thanks for the offer, I'll probably PM you around the time I try the install again :)[/QUOTE]
Hey don't PM we all wanna learn!
:)

---

### Post by M3ta7h3ad on 2005-12-23
TWM is my favourite WM :) okay its pretty damn unuseable, but I loves it! :D wireframe windows and stuff! YUMMY! :D

---

### Post by BSDFreak on 2005-12-23
[QUOTE=M3ta7h3ad]TWM is my favourite WM :) okay its pretty damn unuseable, but I loves it! :D wireframe windows and stuff! YUMMY! :D[/QUOTE]
Actually, type something like "k3b" in one of those terminals and it'll work just as great as clicking k3b in the KDE menu.

It's not unusable, to make it usable you will need to do some configuring though, as a basic WM it's just fine.

---

### Post by PatrickMay16 on 2005-12-23
[QUOTE=BSDFreak]
You are really just begging for viruses and spyware, aren't you?[/QUOTE]
Before I installed Ubuntu, I used Windows 2000 exclusively. I still use it from time to time (maybe once a month or so) and I haven't got any viruses or spyware on it at all.

If you know what you're doing, you won't get junkware.

---

### Post by -Rick- on 2005-12-23
FreeBSD is not really an easy OS(as you found out the bad way ;)). Before I installed I read some important parts of the manual...you really have to know what you're doing.
If you installed X, kde/gnome from the sysinstall you simply have to read [this]("http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/x11-wm.html#X11-WM-KDE-DETAILS") to start kdm at boot time.

I guess you could try DesktopBSD/PCBSD if you want something easier...

---

### Post by BSDFreak on 2005-12-23
> **-Rick-]FreeBSD is not really an easy OS(as you found out the bad way  said:**
> this[/URL] to start kdm at boot time.

I guess you could try DesktopBSD/PCBSD if you want something easier...

Explaim, and btw, destopBSD/PCBSD are not really OS's, just variation of the OS called FreeBSD.

---

### Post by -Rick- on 2005-12-23
[QUOTE=BSDFreak]Explaim[/QUOTE]
In order to install FreeBSD (and mostly) configure it you need to read the manual from time to time(like getting kdm to work). Also you need to think what for boot loader you need, that BSD's require a primary partition etc
After you installed a linux distro such as ubuntu you have a nice and shiny desktop, with BSD you need to figure out how to install additional packages(using pkg_add or ports), how to configure your xorg.conf and if you're unlucky recompile a kernel.

> and btw, destopBSD/PCBSD are not really OS's, just variation of the OS called FreeBSD.
I know...

I just want to say that BSD's need some more time to setup. After that its pretty easy to use it. And yes I'm also a 'BSDFreak' ;)

---

### Post by BSDFreak on 2005-12-23
[QUOTE=-Rick-]In order to install FreeBSD (and mostly) configure it you need to read the manual from time to time(like getting kdm to work). Also you need to think what for boot loader you need, that BSD's require a primary partition etc
After you installed a linux distro such as ubuntu you have a nice and shiny desktop, with BSD you need to figure out how to install additional packages(using pkg_add or ports), how to configure your xorg.conf and if you're unlucky recompile a kernel.[/QUOTE]

All true, you need to make a plan to install beforehand, you need to have the instructions handy should you need them, it's not as easy to set up as other systems but it is so damn fast that you will have saved the time in less than a day anyway.


> I know...

I just want to say that BSD's need some more time to setup. After that its pretty easy to use it. And yes I'm also a 'BSDFreak' ;)

'tis all cool, i was just wondering what you meant by "FreeBSD is not really an OS." which i completely misread... 

Sorry about that.

---


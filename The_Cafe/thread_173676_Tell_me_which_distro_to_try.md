---
title: "Tell me which distro to try"
date: 2006-05-10
forum: The Cafe
---

### Post by towsonu2003 on 2006-05-10
I've been downloading distros to try them out one by one. But I was looking to the 1st 100 distros listed in distrowatch... Did I miss anything you'd recommend me to try out? (I need them to be free ;) )
[list]
[*] Ubuntu 6.06 (will be my base)
[*] Linux Defender
[*] Auditor
[*] Linux from Scratch
[*] DSL
[*] Gentoo
[*] Mepis (when its new version comes out)
[*] CentOS
[*] Vector
[*] IPCop (firewall only)
[*] Debian (stable, to see how that feels like)
[*] Puppy
[*] Fedora
[*] FreeBSD
[*] Zenwalk
[*] OpenBSD
[*] Slackware
[*] Slax
[*] opensuse
[/list]
I checked these out as well, but didn't like either their web site, documentation, or their "message"
[list]
[*] PCLinuxOS
[*] Linspire
[*] Linux XP :mrgreen: 
[*] rPath
[/list]
Thanks :)

*edit*: Recommended so far:
[list]
[*] arch
[*] foresight
[*] debian unstable/testing
[*] frugalware
[*] puppy
[*] mandriva
[*] fc
[/list]

---

### Post by johnc4510 on 2006-05-10
You've got a good list to start with. I just usually keep my eye on distrowatch a couple of times a week to see what's new out there, and then I try it via live cd if possible. Ubuntu is my first choice though.

---

### Post by woedend on 2006-05-10
arch is pretty good...i liked it.
opensuse a lot of people like
debian testing/or unstable(stable sucks for desktop use)

---

### Post by towsonu2003 on 2006-05-10
[QUOTE=woedend]arch is pretty good...i liked it.
opensuse a lot of people like
debian testing/or unstable(stable sucks for desktop use)[/QUOTE]
yep, I forgot to add suse :) edited the post just now ;)

arch seems to be in development for a while (version is 0.7.1). is it stable (no crashes and so on)?

---

### Post by Omnios on 2006-05-10
Try puppy Linux and tell us if ints any good, from what I read its supposed to be easy to use lol.

---

### Post by woedend on 2006-05-10
eh...arch is a rolling release distro...similar to ubuntu I guess you could say.  Youd want to do a netinstall.  Basically, you download noodle, install the base, run a system update(very quick since base install is tiny), and then it downloads the latest apps from the repo's (at your request!  not an automated desktop install).  Anyhow, there is stable/unstable/testing like debian...however stable is not near as stable as debian. It works fabulously, but seemingly every once in a while an upgrade could/will break the system.  The best remedy to this I think is to watch the msg boards.  Normally if something will break or something needs to be changed, it's posted within a day or two of the update.  I used it for about 2 weeks on and off and it never crashed for me.  But I did have my other problems(couldn't use cd drives unless root, 2 ethernet cards kept switching names)

---

### Post by siimo on 2006-05-10
Archlinux - very hands on in terms of configuring and installing but very powerful, it is my distro of choice. Its Repos+community+AUR (Arch User Repository where anyone can submit PKGBUILDs) has almost anything i'd ever want including community packagers packaging latest CVS versions of xfce, gnome (near the end of its cycle), gaim, firefox etc.

Frugalware - based on slackware but Archlinux's pacman pkg management.  Tries to configure things more automatically then Archlinux.

Foresight Linux - uses a unique innovative pkg panagement called conary (rPath you rejected uses it too but Foresight is aimed at desktop users.  Always has latest Gnome like ubuntu and packs the latest and greatest gnome toys.

Mandriva - great for new users very powerful GUI tools I rate better than SUSE's YAST and also the best RPM pkg management in URPMI 


i have used all four extensively and recommend highly.  Foresight needs to mature a little bit still, though it has a superb conary backend and a nice installer based on Fedora's it is a great distro to check out latest gnome goodies just like ubuntu is.

---

### Post by briancurtin on 2006-05-10
id definitely check out Arch. i jumped ship from ubuntu to Arch a while back and have loved every second of it. since Arch is a rolling release like was said earlier, the version numbers really only have to do with what software was packaged in the snapshot as well as the installer. after you install, one of the first things you do is "pacman -Syu" to bring everything up to date, so everthing is squared up. 

i think its a great distro and its definitely worth a shot for at least a week just so you get the feel of how it works and how often things are updated. i run "pacman -Syu" probably twice a day and ill catch at least something that got upgraded each time. its not necessary to do it that often, some do it more and some less, but when you are just starting to check it out, it gives you a sense of how up to date this distro really is

---

### Post by ComplexNumber on 2006-05-10
i would recommend fedora core 5. solid, stable, lots of applications on the CD/DVD (good for people without internet conenctions), nice looking default look, good admin tools now (but not quite as good mandriva or suse).

---

### Post by towsonu2003 on 2006-05-15
so far I tried the following. To my surprise, compiling was too easy in each of them, in contrast to Ubuntu... 
[list]
[*] CentOS: User interface not good enough, old programs. However, I like their idea to make a for-a-fee distro free-to-use... Maybe will get better with 5th release? 
[*] Vector: Very good. 
[*] Puppy: Funny desktop picture, fast, nice. 
[*] Fedora: Not good, too many bugs hit me. 
[*] FreeBSD: Install CD didn't boot. 
[*] Zenwalk: Very good, exceeding my expectations. Still have it, and using from time to time with joy. Imagine Slackware + 2.6 kernel + simple configuration GUIs + 1CD + easy compiling. 
[*] Slackware: My idol, even with kernel 2.6 in testing directory. Unfortunately, couldn't compile a kernel in it, borked installation. Will go back to it as soon as possible. 
[*] Slax: Extremely good liveCD, and you can eject the CD (use adequate boot option). Slackware in a nice LiveCD with good GUI interface. I would continue using it if wvdial worked and if it could have non-root user enabling ability. 
[*] opensuse: A little slow and bloated. Repositories not yet sync'd, so no new software (with 6CDs, who needs new software except conky?). But extremely polished. Checkinstall is in the CD, making compilation a very nice experience. Xen is enabled in a separate kernel, but I don't know how to use it yet... I'll continue using this one along with Zenwalk & Dapper beta for now. So many things in the menus (a feature in Slackware that made me start using Linux). 
[/list]

---

### Post by briancurtin on 2006-05-15
[QUOTE=towsonu2003][list]
[*] CentOS: User interface not good enough, old programs. However, I like their idea to make a for-a-fee distro free-to-use... Maybe will get better with 5th release? 
[/list][/QUOTE]
i was under the impression that Cent was made to be rock solid, so some of their stuff is old because they are going for stability. a lot of web hosts that say they use RedHat, which is a good portion of them, actually use CentOS from what i know. im sure some do use RH, but i'm 2 for 2 in checking out webhosts that use CentOS but advertise RH.

---

### Post by RAV TUX on 2006-05-15
> **towsonu2003]I've been downloading distros to try them out one by one. But I was looking to the 1st 100 distros listed in distrowatch... Did I miss anything you'd recommend me to try out? (I need them to be free  said:**
> 
[*] Ubuntu 6.06 (will be my base)
[*] Linux Defender
[*] Auditor
[*] Linux from Scratch
[*] DSL
[*] Gentoo
[*] Mepis (when its new version comes out)
[*] CentOS
[*] Vector
[*] IPCop (firewall only)
[*] Debian (stable, to see how that feels like)
[*] Puppy
[*] Fedora
[*] FreeBSD
[*] Zenwalk
[*] OpenBSD
[*] Slackware
[*] Slax
[*] opensuse
[/list]
I checked these out as well, but didn't like either their web site, documentation, or their "message"
[list]
[*] PCLinuxOS
[*] Linspire
[*] Linux XP :mrgreen: 
[*] rPath
[/list]
Thanks :)

*edit*: Recommended so far:
[list]
[*] arch
[*] foresight
[*] debian unstable/testing
[*] frugalware
[*] puppy
[*] mandriva
[*] fc
[/list]


I went through the same thing you did and came up with a short list of what worked great and to use in cojunction with Ubuntu

My first recommendation would be:

Yoper:
[http://www.yoper.com/](http://www.yoper.com/)

& 

PC-BSD
[http://www.pcbsd.org/](http://www.pcbsd.org/)

also quite impressive are:

Dreamlinux Studio Edition
[http://www.dreamlinux.com.br/english/index.html](http://www.dreamlinux.com.br/english/index.html)

&

Morphix 0.5-pre4 Gnome
[http://www.morphix.org/index.php?option=com_content&task=view&id=39&Itemid=59](http://www.morphix.org/index.php?option=com_content&task=view&id=39&Itemid=59)

also both of the following are good to:

Musix Gnu + Linux
[http://www.musix.org.ar/en/index.html](http://www.musix.org.ar/en/index.html)

&

GNU/Linux Kinneret
[http://www.linux-kinneret.org/](http://www.linux-kinneret.org/)

I would steer clear of the following (of course this is very subjective and based on personal experience, you will have to learn this by experience):

OpenSUSE, Mepis (unless they have come out with a new version based on Ubuntu), Fedora Core 5, gnoppix, debian k11 hurd, and  mandriva.

---

### Post by xXx 0wn3d xXx on 2006-05-15
> **towsonu2003]I've been downloading distros to try them out one by one. But I was looking to the 1st 100 distros listed in distrowatch... Did I miss anything you'd recommend me to try out? (I need them to be free  said:**
> 
[*] Ubuntu 6.06 (will be my base)
[*] Linux Defender
[*] Auditor
[*] Linux from Scratch
[*] DSL
[*] Gentoo
[*] Mepis (when its new version comes out)
[*] CentOS
[*] Vector
[*] IPCop (firewall only)
[*] Debian (stable, to see how that feels like)
[*] Puppy
[*] Fedora
[*] FreeBSD
[*] Zenwalk
[*] OpenBSD
[*] Slackware
[*] Slax
[*] opensuse
[/list]
I checked these out as well, but didn't like either their web site, documentation, or their "message"
[list]
[*] PCLinuxOS
[*] Linspire
[*] Linux XP :mrgreen: 
[*] rPath
[/list]
Thanks :)

*edit*: Recommended so far:
[list]
[*] arch
[*] foresight
[*] debian unstable/testing
[*] frugalware
[*] puppy
[*] mandriva
[*] fc
[/list]
I would recommend Debian unstable/testing. I tried Debian testing and it was great. There was one problem though, my network card was not reconized (I have a new laptop though). I'm sure that if I could get the latest updates, it would be reconized though. As soon as a new testing version comes out, I am surely going to try it. It would also be familiar to you because Ubuntu is based on Debian. You would be able to install most programs that you use on Ubuntu.

---

### Post by TrailerTrash on 2006-05-15
[QUOTE=briancurtin]i was under the impression that Cent was made to be rock solid, so some of their stuff is old because they are going for stability. a lot of web hosts that say they use RedHat, which is a good portion of them, actually use CentOS from what i know. im sure some do use RH, but i'm 2 for 2 in checking out webhosts that use CentOS but advertise RH.[/QUOTE]


CentOS is very rock solid. I used it for a while on my desktop with some updated apps and it was very smooth. I find it to be more stable than Debian Sarge (or what ever its called).

---

### Post by briancurtin on 2006-05-15
i only used Cent for like two weeks and didnt get to know all that much, but it seemed to be pretty solid so i guess i was right

---

### Post by towsonu2003 on 2006-05-15
[QUOTE=TrailerTrash]CentOS is very rock solid. I used it for a while on my desktop with some updated apps and it was very smooth. I find it to be more stable than Debian Sarge (or what ever its called).[/QUOTE]
I didn't have much time to do research -to find howto update packages by adding repos etc- and the network speed to do any updates -dial up-, so I based my "final experience" on what the distro offered out of the box.

---

### Post by RAV TUX on 2006-05-15
[QUOTE=TrailerTrash]CentOS is very rock solid. I used it for a while on my desktop with some updated apps and it was very smooth. I find it to be more stable than Debian Sarge (or what ever its called).[/QUOTE]

If you want a distro that is ROCK solid, and very refined and intelligent I would stick with Yoper (out of New Zealand).

[http://www.yoper.com/](http://www.yoper.com/)
[[IMG]http://img235.imageshack.us/img235/6073/logo1fi.png[/IMG]](http://imageshack.us)

I dual boot Ubuntu/Yoper.

---

### Post by kabus on 2006-05-16
[QUOTE=woedend]But I did have my other problems(couldn't use cd drives unless root, 2 ethernet cards kept switching names)[/QUOTE]

The first problem probably means your user isn't in the optical group.
Second one is a udev issue, solution here : 

[http://wiki.archlinux.org/index.php/Udev#Mixed_Up_Devices.2C_Sound.2FNetwork_Cards_Changing_Order_Each_Boot](http://wiki.archlinux.org/index.php/Udev#Mixed_Up_Devices.2C_Sound.2FNetwork_Cards_Changing_Order_Each_Boot)

---

### Post by tseliot on 2006-05-16
Try PCLinuxOS, it's a very nice distro

---

### Post by fuscia on 2006-05-16
no damn small linux? try it on some tired old POS.

---

### Post by nalmeth on 2006-05-16
yeah d.s.l. is must

if you have 3d-card, kororaa livecd lgd3d livecd are a lot of fun

pclinuxos, yeah it's good, I use when I'm not at my own computer using dapper. Just so I can use my media.

Also, try E-Live

---

### Post by ice60 on 2006-05-16
i listened to an interview with the two developers of DSL the other day, i think it was recent, anyway there's Damn Small Linux Not (DSL-N) which you could try out
[http://www.damnsmalllinux.org/dsl-n/](http://www.damnsmalllinux.org/dsl-n/)


if you have a windows box networked to another computer you could try BackTrack and play with some of the hacking tools it has.
[http://new.remote-exploit.org/index.php/Tools](http://new.remote-exploit.org/index.php/Tools)

here are some demos of some of the programs, it's abit script-kiddieish but fun stuff. this first one is Metasploit, there's loads of other stuff too on the 
[http://www.irongeek.com/i.php?page=videos/metasploit1](http://www.irongeek.com/i.php?page=videos/metasploit1)
[http://new.remote-exploit.org/index.php/Demos](http://new.remote-exploit.org/index.php/Demos)

---


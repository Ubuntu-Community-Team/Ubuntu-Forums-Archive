---
title: "Do you still compile software?"
date: 2009-03-21
forum: The Cafe
---

### Post by Grant A. on 2009-03-21
With the advent of package managers and pre-compiled binaries, there really isn't much need to compile anything anymore unless you really want bleeding edge stuff. Anyways, do you still compile programs, even though you have a package manager?

---

### Post by Bachstelze on 2009-03-21
Of course. There are tons of situations when you have to compile programs. You might want a version of a program that is not in the repositories, or the program might not even be there at all, you might be involved in the development of said program and need to always run the latest version, etc.

I do not compile *all* my programs from source, of curse, but quite a few of them.

---

### Post by OutOfReach on 2009-03-21
very rarely now. but yes i still do.

---

### Post by binbash on 2009-03-21
Of course i do, not all softwares are at the repos.Also i usually use svn version of most softwares.

---

### Post by t0p on 2009-03-21
Do I compile?  Yes, sometimes.  It's not always possible to get a .deb.  Most of my software comes from repos, through synaptic.  But not all of it.

---

### Post by cmay on 2009-03-21
no. i never compile anything else than my own small c programming examples. 
i have compiled programs before but its a long time since i did that and i did it only to learn how to compile a program. all i need is in a little shellscript i call custom and when on a fresh install i run this to uninstall gnome-games and instll tbhe media codecs and some other programs i always install. so no compiling needed.

---

### Post by cardinals_fan on 2009-03-21
Yes and no.  Do I cd into a directory and ./configure && make && make install?  No.  Do I use Tazwok to cook my own packages from the source, either to modify the compile flags or because the software isn't in the repos?  Absolutely.

---

### Post by jordilin on 2009-03-21
Yes. One of those legendary mp3 players that I miss in Ubuntu repos for instance, XMMS, I download the sources and compiled it by hand :guitar:

---

### Post by blueshiftoverwatch on 2009-03-21
I've compiled software once or twice but that was quite awhile ago. It's not something I'll do unless I have to. Most of the time the application I want to use is either in the repos or comes in deb package.

---

### Post by Nevon on 2009-03-21
In my two-three years of using Linux, I've probably only compiled maybe... 20-25 applications. Usually because they're not in the repositories, but sometimes because the repo versions are severely outdated.

---

### Post by gn2 on 2009-03-21
Never compiled anything, not once ever. Never had the need to.

---

### Post by Skripka on 2009-03-21
Yep.  Although on Arch it is nicely automated via AUR and yaourt.

---

### Post by WatchingThePain on 2009-03-21
Yes but only if it's the last resort.
Not that it's difficult normally.

---

### Post by adamlau on 2009-03-21
Always. From GIMP to Pidgin to Firefox to Xfce, how else can you optimize and strip unused features out of an app to improve its load and response times?

---

### Post by Eisenwinter on 2009-03-21
I use Arch with the testing repository enabled for Pacman, and I still compile some programs.

---

### Post by inobe on 2009-03-21
haven't had to compile anything for at least a year...


seems that everything i do the apps are already in the repos


i had thoughts of compiling a few apps because they were newer' but only for the reason, the previous versions worked well enough to leave alone.

---

### Post by BGFG on 2009-03-21
> **adamlau said:**
> Always. From GIMP to Pidgin to Firefox to Xfce, how else can you optimize and strip unused features out of an app to improve its load and response times?

This is why I want to learn to compile. My current mplayer is compiled, but i was just following instructions. Anyone know any good links to compile and slim down Gnome ?

---

### Post by adamlau on 2009-03-21
Mplayer is a great candidate for a custom build. Here are my options for r29023 (for use with SMPlayer):

```

./configure --disable-mencoder --disable-lirc --disable-xf86keysym --disable-tv --disable-pvr --disable-network --disable-smb --disable-ftp --disable-gif --disable-jpeg --disable-liblzo --disable-xanim --disable-tremor-internal --disable-speex --disable-theora --disable-faac --disable-libdv --disable-liba52-internal --disable-musepack --disable-libamr_nb --disable-libamr_wb --disable-vidix --disable-dga2 --disable-dga1 --disable-sdl --disable-aa --disable-v4l2 --disable-tga --disable-pnm --disable-md5sum --disable-yuv4mpeg --disable-mga --disable-vdpau --disable-fbdev --disable-ossaudio --disable-arts --disable-esd --disable-jack --disable-openal --disable-nas --prefix=/usr/local
```

Minimal deps (libmad, lame, xvidcore, x264) and weighs in at under 7 MB installed (not including the binary codec package). Slimming down GNOME is typically by way of trial and error since your requirements may differ from the requirements of others. ./configure --help is your friend.

---

### Post by Bachstelze on 2009-03-21
Why all the --disable flags? I highly doubt all those features would be enables on a standard Ubuntu install.

Also, don't get your hopes too high about the performance gain of compiling. Most of the time, it is not noticeable, and is pure placebo effect.

---

### Post by adamlau on 2009-03-21
Those options are required to disable what is enabled by default on my Arch workstation. I find that most of the time, the gains are noticeable, particularly when you optimize_and_strip your builds. Fewer relocations, fewer deps, increased likelihood of improved stability as a result.

---

### Post by bigbrovar on 2009-03-21
As a sysadmin for a uni that run ubuntu on their systems .. i do get requests from Profs about some software there would need for their class few of which aren't available in the repos hence i have no option but to download and compile.. its usually a general PITA most times

---

### Post by Bachstelze on 2009-03-21
> **adamlau said:**
> Those options are required to disable what is enabled by default on my Arch workstation. I find that most of the time, the gains are noticeable, particularly when you optimize_and_strip your builds. Fewer relocations, fewer deps, increased likelihood of improved stability as a result.


They are not enabled "by default", they are enabled because they are installed on your system, so the mplayer configure script detected them and enabled them.

So you have things installed on your system that you don't need, since you're disabling them in mplayer. How stripped down and optimized is that! ;)

---

### Post by TalioGladius on 2009-03-21
Only when the software I'm trying to install doesn't have an installer package.

---

### Post by mamamia88 on 2009-03-21
nothing i need to compile from source so far and hopefully i never have too

---

### Post by gnomeuser on 2009-03-21
I am a packager, so I compile a lot of source code so that others might not have to.

---

### Post by sim-value on 2009-03-21
Yes ...

I think also about switching too gentoo ...
(compile everything :D)

/me

---

### Post by RedSquirrel on 2009-03-21
> **Grant A. said:**
> With the advent of package managers and pre-compiled binaries, there really isn't much need to compile anything anymore unless you really want bleeding edge stuff.

... or if you run dwm and you want to customize it. In that case, compiling is mandatory. ;)

I compile software daily using Gentoo's Portage.

On other distributions, I would compile a few select programs, usually to get the latest development code, but in some cases to enable options that the package maintainer decided to leave out.

---

### Post by Ozor Mox on 2009-03-21
Only when the version in Synaptic is sufficiently out of date that I want to use a newer version. That is only ever really with games, because sometimes the versions in the package manager are not compatible with the newest versions and I can't play people online.

So very rarely is my answer.

---

### Post by MaxIBoy on 2009-03-21
I compile software if there isn't an up-to-date prebuilt package available (from the repos or elsewhere.) Since I tend to use development releases a lot, this happens quite often.

I also compile some software specifically for the performance gain (especially the Linux kernel.)

---

### Post by Sealbhach on 2009-03-21
> **bigbrovar said:**
> .. its usually a general PITA most times

Yes, yes it is. I've only done a few for practice but if I had to compile everything I'd be saving up for a Mac.


.

---

### Post by Daisuke_Aramaki on 2009-03-21
I use Lunar and sorcerer predominantly, which are source based distributions. So the package management program takes care of configure make, make install automatically. when i need a program installed, i write a spell (sorcerer) or module (lunar) and cast the spell (sorcerer) or use lin (lunar) to install. This way i can set dependencies for the program and also optimization flags for the compilation. cast and lin take care of the compilations

---

### Post by inobe on 2009-03-21
> **gnomeuser said:**
> I am a packager, so I compile a lot of source code so that others might not have to.

i created .rpm's in opensuse for backup purposes "checkinstall" ;)

edit: [http://www.asic-linux.com.mx/~izto/checkinstall/](http://www.asic-linux.com.mx/~izto/checkinstall/)

---

### Post by BGFG on 2009-03-21
> **Daisuke_Aramaki said:**
> I use Lunar and sorcerer predominantly, which are source based distributions. So the package management program takes care of configure make, make install automatically. when i need a program installed, i write a spell (sorcerer) or module (lunar) and cast the spell (sorcerer) or use lin (lunar) to install. This way i can set dependencies for the program and also optimization flags for the compilation. cast and lin take care of the compilations

Very Cool terminology :)

---

### Post by jimi_hendrix on 2009-03-21
yes

if i want a new version or i want a program and there is no .pkg.tar.gz available for pacman

---

### Post by ibutho on 2009-03-21
I don't compile as much as I used to do in the past, but I still build some packages from source, to customise them to my specific needs.

---

### Post by cardinals_fan on 2009-03-21
> **inobe said:**
> i created .rpm's in opensuse for backup purposes "checkinstall" ;)

edit: [http://www.asic-linux.com.mx/~izto/checkinstall/](http://www.asic-linux.com.mx/~izto/checkinstall/)
Try Tazwok on SliTaz.  You'll wonder why nobody created this before...

---

### Post by ghindo on 2009-03-21
There's one program that I very much like but still (:() has not made it into the Ubuntu repos:  Rubyripper.  I have submitted a bug report, but it doesn't look like there will be any progress.  So unless I want to become a MOTU, I compile from source.

---

### Post by oldos2er on 2009-03-21
I compile some apps because I enjoy learning about the process.

---

### Post by lisati on 2009-03-21
On the rare occasions that I compile stuff these days it's usually small-scale home-grown stuff. I think I've only compiled other software for use within Ubuntu once, maybe twice, to fix a problem that was solved when Intrepid was released.

EDIT: Just remembered one other occasion, so that I could potentially give feedback to another user of these forums on one of their projects.

---

### Post by inobe on 2009-03-21
> **cardinals_fan said:**
> Try Tazwok on SliTaz.  You'll wonder why nobody created this before...

thanks you :)


i back stuff up on a daily basis, i appreciate this valuable information.

---

### Post by spupy on 2009-03-21
I use Gentoo, so installing a package means compiling it, but it is automatic. 

Even if I wasn't using a source-based distro, there are programs that I always compile by hand. The reason is that I have some modified versions of them that I prefer to the vanilla versions - pidgin, liferea, leafpad, evince, file-roller, geany, transmission, synaptics driver, and some others. :)

---

### Post by cardinals_fan on 2009-03-21
> **inobe said:**
> thanks you :)


i back stuff up on a daily basis, i appreciate this valuable information.
No problem.  How does it help you with backups (or do you mean backing up the fact in your mind)?

---

### Post by kk0sse54 on 2009-03-21
Another Gentoo user here, yet even in my Arch install I compile everything through ABS as well as in NetBSD I generally compile everything through pkgsrc.

---

### Post by -grubby on 2009-03-21
I've only compiled something once, and it turns out that it was already in the repos.

---

### Post by PurposeOfReason on 2009-03-21
Just finished my first full gentoo installation, so yes. Even before that I used the ABS heavily with arch.

---

### Post by tubezninja on 2009-03-21
I compile whenever a software package isn't in the repos, or when the repo package is set up in such a way that it's unsutiable for the application.

Cases in point:

1. I had a developer who needed [Amberfish]("http://www.etymon.com/tr.html").  Doesn't exist in the repos, so I compiled it.

2. Same developer had code that did not work well with the [Suhosin Patch]("http://www.hardened-php.net/suhosin/"), which comes standard with the ubuntu repo version of LAMP.  So I had to compile PHP myself for that use case.

---

### Post by adamlau on 2009-03-22
> **HymnToLife said:**
> They are not enabled "by default", they are enabled because they are installed on your system, so the mplayer configure script detected them and enabled them.So you have things installed on your system that you don't need, since you're disabling them in mplayer...
Correct, but those auto detected deps are typically installed as part of other packages (often unnecessary due to how Arch devs handle them in vanilla builds). Disabling means no dep relocation required = potential for faster startup + fewer worries if the deps are buggy. Do what you may, some prefer to build for fun and profit and others don't...

---

### Post by jomiolto on 2009-03-22
I develop software myself, so obviously I do ;)

As for the software I merely use: sometimes I do compile it myself. There's this weird form of satisfaction I get from using software that I have compiled myself from the latest source...

---

### Post by JoshuaRL on 2009-03-22
I've only compiled a couple of times.  If I ever get into maintaining packages, then I'll of course do that more.  But I think that mainly compiling skips out on one of the biggest reasons I love Linux:

Repos

I'm just a "sudo aptitude update && sudo aptitude safe-upgrade" away from a fully updated and safe system.  (Either that or Adept/Update Manager tells me I have updates available)  I don't have to routinely go out searching for new versions to keep my system up to date and safe.  Sure, some of my applications are a little behind the bleeding edge, but then again they're usually pretty bug-free too.  And if I ever need a newer app or one that's not in the repos, I go looking for a PPA.  Lately there's been a lot of those.  Currently, other than the standard Ubuntu ones, I'm running repos for:

OO.o
Opera
Google Linux
Amarok 2
Medibuntu
Wine
Spring
Cairo Dock
e17 (from SVN)
SynCE
Kubuntu-Experimental (KDE 4.2)

And so far, everything works great.  I pick my repos and applications carefully, and I have no issues.  And I get the great new software I need, without all the compile time and with updates.

---

### Post by loell on 2009-03-22
I do packaging (none official).

so I compile occasionaly,  or maybe not. since the compilation of packages doesn't happen on my machine, and does only on launchpad's remote compile farm.

---

### Post by K.Mandla on 2009-03-22
Yes, I still compile software and kernels. I find it's the best way to customize a package to my needs. 

That being said, outside of Crux I usually don't compile things, unless it's from Arch's AUR. To me, part of the appeal of using Arch or Ubuntu is the fact that you don't have to compile anything. ... :|

The last time I compiled something in Ubuntu was ... I can barely remember. No, wait. I compiled a GTK1.2 version of Beaver late last year. ;)

---

### Post by Paqman on 2009-03-22
I used to when I was new to Linux, but don't any more. The advent of PPAs has pretty much removed the need to compile anything for Ubuntu.

Package managers are Linux's killer app, IMO. By circumventing your package manager you're breaking the dependency system, which doesn't appeal. If I find an app which is compile-only (which is extremely rare) then i'll keep looking until I find an alternative that offers a .deb or a repo.

---

### Post by RedSquirrel on 2009-03-22
> **Paqman said:**
> Package managers are Linux's killer app, IMO. By circumventing your package manager you're breaking the dependency system, which doesn't appeal.

Wouldn't you tell your package manager what you've done? :)

---


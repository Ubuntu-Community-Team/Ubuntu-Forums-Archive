---
title: "I'm looking for a distro that..."
date: 2009-04-10
forum: The Cafe
---

### Post by CJ Master on 2009-04-10
* Does not force me to edit any configuration files that I don't give a care about (*cough*arch*cough*)
* HOWEVER! starts out with a bare minimal gnome system and lets me add programs with a Ubuntu-like Add/Remove.
* I do not wish to install at command line, I will if forced though.

Basically: I want a distribution that only install what's required for it to simply boot up AND what I install. GNOME desktop environment is greatly preferred.

Any ideas? :)

---

### Post by WalmartSniperLX on 2009-04-10
I know for a fact that Gentoo CAN be that distro ;)

Then again you mentioned config files.

---

### Post by CJ Master on 2009-04-10
> **WalmartSniperLX said:**
> I know for a fact that Gentoo CAN be that distro ;)

Then again you mentioned config files.

If I recall correctly, Gentoo involved compiling from source. No thank you. :P

---

### Post by lemuriaX on 2009-04-10
Have you tried building a Debian system up from a barebones install? I did this recently with an old G3 Mac laptop someone gave me and it was fun. Didn't install Gnome on it due to resource limitations, went with XFCE.

---

### Post by lisati on 2009-04-10
I don't think you'll be able to completely avoid the command line unless you're extremely fortunate with your choice hardware and software. 

If I was completely happy to limit what I do with it to browsing, and email, together with the games that come installed by default, the laptop I'm using right now would require little or no command line work after a fresh install of Ubuntu 8.10 (It's one of the Toshiba Satellite M200 range)

---

### Post by CJ Master on 2009-04-10
> **lemuriaX said:**
> Have you tried building a Debian system up from a barebones install? I did this recently with an old G3 Mac laptop someone gave me and it was fun. Didn't install Gnome on it due to resource limitations, went with XFCE.

Interesting. Is bare-bones install a separate iso (like a "lite" edition?) or the normal iso? Plus: what would a barebones install, install? Would it be easy enough to add gnome?

Thank you for your time. :)

---

### Post by CJ Master on 2009-04-10
> **lisati said:**
> I don't think you'll be able to completely avoid the command line unless you're extremely fortunate with your choice hardware and software. 

If I was completely happy to limit what I do with it to browsing, and email, together with the games that come installed by default, the laptop I'm using right now would require little or no command line work after a fresh install of Ubuntu 8.10 (It's one of the Toshiba Satellite M200 range)

Eh.. well I'm not afraid of the command line by any means (as long as I know what to do) I just prefer a GUI.

While Ubuntu is excelent for many things, being a minimal install is unfortuantly not one of them. (many, many unnecessary (for me) packages are installed.)

Thanks for the idea though.

---

### Post by Flag on 2009-04-10
Pclos ?

---

### Post by Newuser1111 on 2009-04-10
[http://www.debian.org/CD/netinst/](http://www.debian.org/CD/netinst/) ?

---

### Post by CJ Master on 2009-04-10
I haven't had any experiance with PCLinuxOs Gnome Ed., but I'm pretty sure it's not what I'm looking for. It looks like Ubuntu.

---

### Post by WalmartSniperLX on 2009-04-10
Linpus and OpenSuse are both very non-interactive with the CLI. You can customize what packages you want installed with the install DVD of openSuse and there are several different versions of Linpus. I think one of them is a gnome/Icon based interface. It's the same OS used on the mini Acer laptops preinstalled with linux.

---

### Post by CJ Master on 2009-04-10
Thanks for NetInst link, I have the question. Is the "testing" version the rolling release Debian? If not, could you please provide a link to the NetInst for Debian Unstable?

Thank you!

---

### Post by CJ Master on 2009-04-10
> **WalmartSniperLX said:**
> Linpus and OpenSuse are both very non-interactive with the CLI. You can customize what packages you want installed with the install DVD of openSuse and there are several different versions of Linpus. I think one of them is a gnome/Icon based interface. It's the same OS used on the mini Acer laptops preinstalled with linux.

Dang, people are posting so fast I can't keep up! :lolflag:

Just the fact that the installer is a "DVD" is turning me away from it. Why would it require the size of a DVD to install a barebones system?

Linpus, I'll take a look, thanks!

Edit: Linpus is a no-go, way too much preinstalled. Thanks anyways though!

---

### Post by lemuriaX on 2009-04-10
> Interesting. Is bare-bones install a separate iso (like a "lite" edition?) or the normal iso? Plus: what would a barebones install, install? Would it be easy enough to add gnome?

There is a graphical installer and while you can choose to install a desktop environment during the initial install, I like to just install the minimal system first. You would have to then use the CLI to then get the xserver and a window manager from there though. Aptitude is helpful for this as it has a nice interface and lets you browse through packages. You could go with a really lightweight window manager and build from there.

---

### Post by CJ Master on 2009-04-10
> **lemuriaX said:**
> There is a graphical installer and while you can choose to install a desktop environment during the initial install, I like to just install the minimal system first. You would have to then use the CLI to then get the xserver and a window manager from there though. Aptitude is helpful for this as it has a nice interface and lets you browse through packages. You could go with a really lightweight window manager and build from there.

Ok, I'm a pretty big newb with this, so please bear with me.

DE's and WM's are totally different things, right? If so, what WM should I install with gnome?

How would I install X?

Also, if there's any tutorials on the subject you can just point me there. :P

Edit: Gotta go to sleep. Thanks for the help everyone, I'll reply in the mornin.

---

### Post by lemuriaX on 2009-04-10
FYI you can also do a barebones install of Ubuntu:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

I'm not sure the best way to install Gnome if not just choosing the default way where it installs the whole desktop environment including lots of applications you might not need (someone else can probably offer better advice there). Take a look at this link though:
[http://wiki.debian.org/Gnome?action=show&redirect=GNOME](http://wiki.debian.org/Gnome?action=show&redirect=GNOME)

Lenny is the stable version...as time goes on the packages will get somewhat outdated for most people's tastes for a desktop install, used more for servers, but it was just released in Feb so right now things are fairly current. Most people tend to run Testing on their desktops I believe.

---

### Post by ugm6hr on 2009-04-10
I realise you said no CLI, but this might be exactly what you are after.

[http://distrowatch.com/weekly.php?issue=20081215#feature](http://distrowatch.com/weekly.php?issue=20081215#feature)

Just add Add/Remove with

```
sudo apt-get install gnome-app-install
```

after installing gnome base (Base Environment), and away you go.  Pick other bits as described.

Turns out it is Ubuntu you were looking for after all.

---

### Post by gnomeuser on 2009-04-10
Ubuntu is a fine solution to that problem, even if that dependency requirement will force you to do some clean up and there are things you can't get rid of (e.g. I cannot completely remove OpenOffice since that would remove my translated strings for the entire system).

Aside that you can look at openSUSE, there is a CD installer also SUSE Studio (susestudio.com) will let you remix your install just the way you want it. Preconfigure it and all you have to do is put in on a CD/DVD or USB stick to install.. believe me SUSE Studio is definitely where you want to go but it is invite only right now so you may have to wait a little bit. Go watch the video and drool.

---

### Post by Barrucadu on 2009-04-10
Zenwalk is very nice, I'm not sure if it comes with a GNOME version though.

---

### Post by Eisenwinter on 2009-04-10
> **CJ Master said:**
> * Does not force me to edit any configuration files that I don't give a care about (*cough*arch*cough*)

Well, see, the thing is, all the config files you edit in Arch are the ones you DO care about, if you want to have a nice usable system (fstab, rc.conf, xorg.conf, etc).

though xorg.conf, obviously, is not actually required, only if you want to use GUI ;) (and you said you do :P)

---

### Post by Mehall on 2009-04-10
> **Eisenwinter said:**
> Well, see, the thing is, all the config files you edit in Arch are the ones you DO care about, if you want to have a nice usable system (fstab, rc.conf, xorg.conf, etc).

though xorg.conf, obviously, is not actually required, only if you want to use GUI ;) (and you said you do :P)

Ergo he cares about it!!! :popcorn::lolflag:

What about Tiny Core? It's only 10MB yet has a GUI.

Their package manager is sub-par if I'm honest, but there's enough choice.

Don't know if they have Gnome though.

---

### Post by gn2 on 2009-04-10
> **Barrucadu said:**
> Zenwalk is very nice, I'm not sure if it comes with a GNOME version though.

Package management is not straightforward in Zenwalk, but they do now have a Gnome version.

---

### Post by Paqman on 2009-04-10
You could stick with Ubuntu and go for the [Minimal install CD](https://help.ubuntu.com/community/Installation/MinimalCD). IIRC the alternate CD also has a minimal install option, not sure how much the two differ.

---

### Post by CJ Master on 2009-04-10
> **Eisenwinter said:**
> Well, see, the thing is, all the config files you edit in Arch are the ones you DO care about, if you want to have a nice usable system (fstab, rc.conf, xorg.conf, etc).

though xorg.conf, obviously, is not actually required, only if you want to use GUI ;) (and you said you do :P)

I care about those, I do not care to edit them. :P

Anyway, Ubuntu minimal sounds pretty nice! Is it possible to do it with Jaunty beta? Also, how much does this minimal install, install? Just bare-bones system, right?

Thanks guys :D

---

### Post by SomeGuyDude on 2009-04-10
FWIW: Arch involves a lot less editing than it seems. If you have a spare machine on hand, just read the beginners guide on the other. Once you get the rc.conf and xorg files set that's really all there is to it.

---

### Post by Mehall on 2009-04-10
> **SomeGuyDude said:**
> FWIW: Arch involves a lot less editing than it seems. If you have a spare machine on hand, just read the beginners guide on the other. Once you get the rc.conf and xorg files set that's really all there is to it.

rc.conf is very simple, and it's internal comments tell you all you need to know, and xorg.conf is widely documented all over the internet.

---

### Post by SomeGuyDude on 2009-04-10
> **Mehall said:**
> rc.conf is very simple, and it's internal comments tell you all you need to know, and xorg.conf is widely documented all over the internet.

^ That.

Seriously, I'm just some meathead that doesn't know a bash script from a bench press. If I can do it, anyone can.

---

### Post by ugm6hr on 2009-04-10
> **CJ Master said:**
> Anyway, Ubuntu minimal sounds pretty nice! Is it possible to do it with Jaunty beta? Also, how much does this minimal install, install? Just bare-bones system, right?

Don't see why Jaunty shouldn't be possible.  Just get the AlternateCD.

A minimal install only installs the absolute minimum, and then anything you tell it to.  See my previous link.

---

### Post by CJ Master on 2009-04-10
Thanks for telling me that Arch doesn't involve too much configuration, but I still think I like Ubuntu better. I'll try Arch out someday.

alright, going to try a minimum install! Wish me luck!

---

### Post by mikeize on 2009-04-10
Re: Arch

It IS entirely possible that some detail of your hardware will require you to spend hours and hours messing with cfg files like xorg.conf, probably meaning you mess other stuff up, and have to reinstall a few times, and in the end never solve your original problem--at least, that's what happened to me 

Anyway, you never know until you try, but Arch was a lot more work than I'm willing to do right now.  I don't want tetris, or 6 integrated text editors, but I do want my touchpad to work "out of the box".

---

### Post by Simian Man on 2009-04-10
Almost all distros have some way to do a minimal install.  If you don't like the default software, that is *not* a reason to switch to another distribution.  Well, it shouldn't be the sole reason anyway.

---

### Post by Warpnow on 2009-04-10
Install a server edition of ubuntu.

then type:

sudo apt-get install gnome gdm

done.

---

### Post by SomeGuyDude on 2009-04-10
> **mikeize said:**
> Re: Arch

It IS entirely possible that some detail of your hardware will require you to spend hours and hours messing with cfg files like xorg.conf, probably meaning you mess other stuff up, and have to reinstall a few times, and in the end never solve your original problem--at least, that's what happened to me 

Anyway, you never know until you try, but Arch was a lot more work than I'm willing to do right now.  I don't want tetris, or 6 integrated text editors, but I do want my touchpad to work "out of the box".

Not to derail, but when was this and what kind of card do you have? I'm all Intel parts, so admittedly Linux is pretty painless with ANY distro I use, but if you've got ATI or nVidia things could be harder.

---

### Post by Skripka on 2009-04-10
> **SomeGuyDude said:**
> Not to derail, but when was this and what kind of card do you have? I'm all Intel parts, so admittedly Linux is pretty painless with ANY distro I use, but if you've got ATI or nVidia things could be harder.

Nvidia cards are as hard to run on Arch as pacman -S nvidia.

---

### Post by SomeGuyDude on 2009-04-10
> **Skripka said:**
> Nvidia cards are as hard to run on Arch as pacman -S nvidia.

Yeah but the beginner's guide lists a whole bunch of other steps to take, last I checked. Also wasn't the ATI mobile Radeon card notoriously difficult to deal with on Linux in general?

---

### Post by Skripka on 2009-04-10
> **SomeGuyDude said:**
> Yeah but the beginner's guide lists a whole bunch of other steps to take, last I checked. Also wasn't the ATI mobile Radeon card notoriously difficult to deal with on Linux in general?

Xorg now has autodetection on install-so all that editing or creating of a good Xorg.conf shouldn't be necessary unless you are wanting to tweak things.

ATi.  Eeeeek.  Those things are usually painful on Linux, Arch or not.

---

### Post by SomeGuyDude on 2009-04-10
Yeah, I was baffled that Mint managed to pick up a computer I had laying around with an ATI card. No idea why it got it, but Ubuntu didn't.

---

### Post by WatchingThePain on 2009-04-10
If you don't like Archie Warchie then pclinuxos is pretty good.
Have a little snoop at the hcl first as you know that helps.

---

### Post by SomeGuyDude on 2009-04-10
Isn't PCLOS a full-featured distro like Ubuntu and Fedora? Last I checked it was a Mandrake offshoot with KDE on it.

---

### Post by sertse on 2009-04-10
ubuntu Minimal, Debian Minimal.. will havewhat you want and what you're most familiar with...

Also, this thread show why Arch users can be annoying sometimes imo. The OP said no Arch, but someone still had to segue into Arch. Then all the other Archers come in...

Arch is not always the centre of discussion....

His argument I felt was pedantic anyways, and I feel that poster knew it, but *had* to make the discussion about Arch.

When I read the OP, and not liking editing conf files, I understand what he was really asking for something automated. Or to address it directly, someone who feels the degree of control provided by manually editing (and reading the relevant page on the subject, though I know most of it is straight forward) is not worth it compared to the ease of automation (which does things "good enough". 

I feel some find it hard to accept it, and must fight the point,..

Sorry for the rant, it happens to many threads, and sometimes it just  gets to me....

---

### Post by WatchingThePain on 2009-04-10
> **SomeGuyDude said:**
> Isn't PCLOS a full-featured distro like Ubuntu and Fedora? Last I checked it was a Mandrake offshoot with KDE on it.

Oh yeah lol.
It's not very bloated though, goes on fast. You can probably get gnome on it.
Well it's a tough one.
Arch is the best bet to match that. (but Arch is text based install.)
pcbsd?..only thing with that is I didn't really like the way software gets installed.

---

### Post by cardinals_fan on 2009-04-10
Paldo is quasi-source based.  I wasn't a fan of their unusual packaging, but they have the nicest GNOME implementation I've seen.

---

### Post by RedSquirrel on 2009-04-10
I've found that the [gnome-core]("http://packages.ubuntu.com/jaunty/gnome-core") meta package is a good way to get a basic GNOME.  After installing a minimal, command-line system:  ```
sudo apt-get install xorg gdm gnome-core
```

---

### Post by inobe on 2009-04-10
> **CJ Master said:**
> Dang, people are posting so fast I can't keep up! :lolflag:

Just the fact that the installer is a "DVD" is turning me away from it. Why would it require the size of a DVD to install a barebones system?

Linpus, I'll take a look, thanks!

Edit: Linpus is a no-go, way too much preinstalled. Thanks anyways though!

opensuse live cd is super bare, you will be surprised how much building is required, it all happens in yast.....

so basically theres nada

---

### Post by SomeGuyDude on 2009-04-10
I believe SOMEONE has made an Arch non-text install (although I heavily disagree with its existence).

---

### Post by CJ Master on 2009-04-10
Right now I set up my new Ubuntu... AND IM LOVIN IT! I'm trying to find ways to make it boot faster, any tips? (I'm in Jaunty Beta)

> **SomeGuyDude said:**
> I believe SOMEONE has made an Arch non-text install (although I heavily disagree with its existence).

Talking about Chakra?

---

### Post by sekinto on 2009-04-10
If you download the Debain net install CD and disable network sources a barebones system will be installed. Then you have to touch the command line, but only briefly. You log in as root, edit your /etc/apt/sources.list file adding the Debian repositories that you want to use (you can find them on the site) and then apt-get the stuff you want like gnome-core, gnome-base, gnome-minimal or whatever it is called (the main gnome package comes with Gnome's default programs like Gnome Games, AbiWord and Gnumberic).

---

### Post by handy on 2009-04-11
> **CJ Master said:**
> * Does not force me to edit any configuration files that I don't give a care about (*cough*arch*cough*)
* HOWEVER! starts out with a bare minimal gnome system and lets me add programs with a Ubuntu-like Add/Remove.
* I do not wish to install at command line, I will if forced though.

Basically: I want a distribution that only install what's required for it to simply boot up AND what I install. GNOME desktop environment is greatly preferred.

Any ideas? :)

OSX & [***_VersionTracker_***]("http://www.versiontracker.com/macosx/")

---

### Post by WatchingThePain on 2009-04-11
> **SomeGuyDude said:**
> I believe SOMEONE has made an Arch non-text install (although I heavily disagree with its existence).

Yeah, I mean what's wrong with the Arch text installer..it's straightforward and fast. In fact it's probably the best installer I have seen. Some graphical installers can be rather confusing. Ubuntu has a very good graphical installer.

---

### Post by gn2 on 2009-04-11
> **WatchingThePain said:**
> Yeah, I mean what's wrong with the Arch text installer.

It installs Arch?

---

### Post by WatchingThePain on 2009-04-11
> **gn2 said:**
> It installs Arch?

HAHA I'm not even going to comment.

---

### Post by lyceum on 2009-04-11
> **CJ Master said:**
> If I recall correctly, Gentoo involved compiling from source. No thank you. :P

That is correct. However, that just means a long install. You may want to try Nimble X. It lets you pick what you want online, so you are building your own distro.

---

### Post by Andreas1 on 2009-04-11
How about [this]("http://distrowatch.com/weekly.php?issue=20081215#feature")? I haven't tried it (yet) though.
EDIT: ok, it seems to require command line, but not too much configuring

---

### Post by WatchingThePain on 2009-04-11
Nimble x?..wow they are all coming out of the woodwork!.
How many Linux distro's are there?.

---

### Post by Mehall on 2009-04-11
Distrowatch tracks around 300, and that's just active ones, not including things like "puplets", etc.

There are, all told, probably around 350-400 active, probably in excess of 1000 in Linuxes full history

---

### Post by WatchingThePain on 2009-04-11
> **Mehall said:**
> Distrowatch tracks around 300, and that's just active ones, not including things like "puplets", etc.

There are, all told, probably around 350-400 active, probably in excess of 1000 in Linuxes full history

Interesting, thank you for that info.

---

### Post by SomeGuyDude on 2009-04-11
> **WatchingThePain said:**
> Yeah, I mean what's wrong with the Arch text installer..it's straightforward and fast. In fact it's probably the best installer I have seen. Some graphical installers can be rather confusing. Ubuntu has a very good graphical installer.

Text installers can be intimidating, it feels like you have "too much access". I mean, with Ubuntu you really can't screw it up as long as you just stick with all the "auto-prepare" options. When you're piecing together your configuration text files it you delete a line by accident or put in something with the wrong syntax things can go pretty wrong.

That said, it's not hard, you just gotta get over your initial worry. I'm really considering a Slack, Gentoo, or CRUX install now that I've kinda gotten my feet wet.

---

### Post by NightwishFan on 2009-04-11
I would say install Ubuntu-Standard + Whatever packages you want. :KS (Use minimal installer)

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by WatchingThePain on 2009-04-11
@ SomeGuyDude

I've been hearing a lot of good reports about Gentoo.
I think Sabayon is related to Gentoo and is supposed to look really slick.

---

### Post by SomeGuyDude on 2009-04-11
Gentoo is apparently beautiful if you don't mind giving it a few hours to compile everything, but to be honest that's fine by me. I can do it before I go out for a while and come back when it's done. It's not like compiling takes any work. I'm just unsure if it would make that much of a difference for me.

And, to be honest, Arch's AUR is such a crazy useful little tool I don't wanna give it up.

---

### Post by chris200x9 on 2009-04-11
> **SomeGuyDude said:**
> 
And, to be honest, Arch's AUR is such a crazy useful little tool I don't wanna give it up.

Overlays! :popcorn:

---

### Post by SomeGuyDude on 2009-04-11
Interesting! Reearch will follow. Who knows, this time tomorrow I may be on Gentoo...

---

### Post by handy on 2009-04-12
> **WatchingThePain said:**
> @ SomeGuyDude

I've been hearing a lot of good reports about Gentoo.
I think Sabayon is related to Gentoo and is supposed to look really slick.

Allocate 3 days for your Gentoo install, & you won't be disappointed.

---

### Post by lyceum on 2009-04-12
> **WatchingThePain said:**
> Nimble x?..wow they are all coming out of the woodwork!.
How many Linux distro's are there?.

Nimbel X was the first distro I every tried 3 years ago. Back then it was just a live CD based on Slackware. Now it is actually very cool.

---

### Post by SomeGuyDude on 2009-04-12
> **handy said:**
> Allocate **3 days** for your Gentoo install, & you won't be disappointed.

:shock:

Um... maybe not then.

---

### Post by lyceum on 2009-04-12
> **SomeGuyDude said:**
> :shock:

Um... maybe not then.

:lolflag:

Yeah, Gentoo is very cool, but takes a while to load. It is best to use vacation time if you want to watch it in action ;)

---

### Post by SomeGuyDude on 2009-04-12
I just don't think I could go that long without a working machine! :lolflag:

---


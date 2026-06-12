---
title: "Why Flash runs so well in OpenSolaris and so poor in Linux"
date: 2008-08-01
forum: The Cafe
---

### Post by Canis familiaris on 2008-08-01
Yesterday I recieved the OpenSolaris CD and installed it. I actually liked it as well as disliked it (mainly because of its strange terminal behaviour and keyboard shortcut issues). However I was pleasantly surprised how Flash ran so well in it. I mean it ran perfectly and did not crash at all, even in Fullscreen. And in Linux, the less said about Flash in Linux is better.(even Flash 10 Beya crashes)
So my question is WHY?

---

### Post by DeadSuperHero on 2008-08-01
I actually have an answer for this, as I noticed it as well.

Linux has many various distributions. There are so many different distros with many different library versions for different purposes. Therefore, it can affect Flash performance across the board. Since it's a proprietary app, it would be impossible to create perfectly working ports across every distribution.

OpenSolaris is derived from Solaris 10, which is backwards compatible all the way to Solaris 2. Because it has a unified system library, and all derivatives contribute back code on unified libraries, there is little to affect the performance of proprietary apps that utilize those library versions.

EDIT: Although, media playback in OpenSolaris isn't quite as great. I managed to get some GStreamer plugins to work, but it seems that not all of them are ready for Solaris. Specifically, MPEG-2, MP4, and WMV. Possibly Quicktime, too. I hope they get GStreamer and Xine fully ported by the Jericho release, as well as Firefox 3 and KDE 4.1. Once those are ported over, I might officially switch for good.

---

### Post by madjr on 2008-08-01
yea, linux sucks...

by the explanation above

no standards no unification

---

### Post by Canis familiaris on 2008-08-01
> **madjr said:**
> yea, linux sucks

:confused:

---

### Post by cardinals_fan on 2008-08-01
Solaris has been around for a long time, and remains backward compatible.  With that said, I've never had problems with Flash on Linux.

---

### Post by Canis familiaris on 2008-08-01
> **cardinals_fan said:**
> Solaris has been around for a long time, and remains backward compatible.  With that said, I've never had problems with Flash on Linux.

Surf Youtube and then you'll know. :(

---

### Post by cardinals_fan on 2008-08-01
> **Anurag_panda said:**
> Surf Youtube and then you'll know. :(
The only bug I have is the menus-behind-Flash-content thing.  Everything else works flawlessly.

---

### Post by DeadSuperHero on 2008-08-01
I will admit, Linux is definitely getting better with Flash. I think there needs to be more standardization/unification across the board for Linux distros. But, most people wouldn't want that to happen. Remember Unified Linux? Never even took off.

---

### Post by cardinals_fan on 2008-08-01
> **Mr. Psychopath said:**
> I will admit, Linux is definitely getting better with Flash. I think there needs to be more standardization/unification across the board for Linux distros. But, most people wouldn't want that to happen. Remember Unified Linux? Never even took off.
It was a fundamentally broken concept.  I don't think that everyone wants to run Arch... but I do.

---

### Post by Canis familiaris on 2008-08-01
> **Mr. Psychopath said:**
> I will admit, Linux is definitely getting better with Flash. I think there needs to be more standardization/unification across the board for Linux distros. But, most people wouldn't want that to happen. Remember Unified Linux? Never even took off.

Actually I am also among those people who are against unification in Linux.
A unified *nix based OS is OpenSolaris already. It will be interesting to see where it moves.
(I hope they make those keyboard shortcuts similar to Linux and also terminal more usable)

---

### Post by L815 on 2008-08-01
I think if Linux just made software packaging and packages UNIVERSAL ACROSS ALL DISTROS, then many problems would decrease. 
:confused::confused::confused::confused::confused::confused:

---

### Post by cardinals_fan on 2008-08-01
> **Anurag_panda said:**
> Actually I am also among those people who are against unification in Linux.
A unified *nix based OS is OpenSolaris already. It will be interesting to see where it moves.
(I hope they make those keyboard shortcuts similar to Linux and also terminal more usable)
What are you talking about?  The "terminal" could mean multiple things.  Do you mean the actual terminal emulator (GNOME-Terminal) or the shell (I think that OpenSolaris uses BASH)?

---

### Post by FuturePilot on 2008-08-01
> **Anurag_panda said:**
> :confused:

yeah :confused:

---

### Post by Alasdair on 2008-08-01
[QUOTE=L815]I think if Linux just made software packaging and packages UNIVERSAL ACROSS ALL DISTROS, then many problems would decrease. [/QUOTE]
The Linux standard base already specifies RPM as the universal package format that application vendors should target. Why? Because Novell and Red-Hat said so. Any so called 'Linux unification' will be done by large companies with no say whatsoever from anyone else in the community. And that is why it will always be ignored.

---

### Post by Canis familiaris on 2008-08-01
> **cardinals_fan said:**
> What are you talking about?  The "terminal" could mean multiple things.  Do you mean the actual terminal emulator (GNOME-Terminal) or the shell (I think that OpenSolaris uses BASH)?

Yes it uses BASH.
I meant GnomeTerminal. Sorry for not being clear.
XTerm is fine though.

> **Alasdair said:**
> The Linux standard base already specifies RPM as the universal package format that application vendors should target. Why? Because Novell and Red-Hat said so. Any so called 'Linux unification' will be done by large companies with no say whatsoever from anyone else in the community. And that is why it will always be ignored.

Yep! I say APT to be standard, but who listens.

---

### Post by cardinals_fan on 2008-08-01
> **Anurag_panda said:**
> Yes it uses BASH.
I meant GnomeTerminal. Sorry for not being clear.
XTerm is fine though.

Well, you can hardly fault OpenSolaris for that.  Most OSs that include GNOME include gnome-terminal ;)

Just look at Ubuntu.

---

### Post by Canis familiaris on 2008-08-01
> **cardinals_fan said:**
> Well, you can hardly fault OpenSolaris for that.  Most OSs that include GNOME include gnome-terminal ;)

Just look at Ubuntu.

Well actually GNOME-Terminal Works very well in Ubuntu.
My problem GNOME Terminal does not use Home and End Keys, and as a result I have use the cursor key multiple times. That is painful. :(
Dunno what they have done to the GNOME Terminal.
(As for xterm which works, but it is slow)
And No Linux distro has this problem.

---

### Post by dca on 2008-08-01
This is going to sound odd but it seemed to me like a 'planets in alignment' kind of thing when it came to Flash in GNU/Linux.
 
Hear me out, try using CentOS5.x with Firefox 2.x with latest vers of Flash and you'll get all kinds of weird issues.  Try Mandriva 2008.1 w/ FF2.x and latest Flash, it works fine.  Try Ubuntu 7.10 w/ FF2.x and latest Flash vers at that time and you get weird issues...  So far, openSUSE11 w/ their included Flash from DVD and latest FF update, Ubuntu 8.04 w/ latest FF update and Flash from 'Ubuntu Restricted Media' metapackage are the only ones that seem to work w/o any hitches.  The other side has been running 64bit OS, but that's another story.

---

### Post by armageddon08 on 2008-08-01
> **Alasdair said:**
> The Linux standard base already specifies RPM as the universal package format that application vendors should target. Why? Because Novell and Red-Hat said so. Any so called 'Linux unification' will be done by large companies with no say whatsoever from anyone else in the community. And that is why it will always be ignored.

But.....there has to be a leader in any field whatsoever. Others will follow him. Everybody can't be a leader. Then only we can have 'unification'. Having said so, its best to have a 'non-profit' organisation as the 'leader'.

---

### Post by cardinals_fan on 2008-08-01
> **Anurag_panda said:**
> Well actually GNOME-Terminal Works very well in Ubuntu.
My problem GNOME Terminal does not use Home and End Keys, and as a result I have use the cursor key multiple times. That is painful. :(
Dunno what they have done to the GNOME Terminal.
(As for xterm which works, but it is slow)
And No Linux distro has this problem.
You could change those settings ;)

---

### Post by Canis familiaris on 2008-08-01
> **cardinals_fan said:**
> You could change those settings ;)
I know but How? I have never configured GNOME Terminal before.

---

### Post by cardinals_fan on 2008-08-01
> **Anurag_panda said:**
> I know but How? I have never configured GNOME Terminal before.
[http://library.gnome.org/users/gnome-terminal/stable/gnome-terminal-prefs.html.en](http://library.gnome.org/users/gnome-terminal/stable/gnome-terminal-prefs.html.en)

Anyway, I'm not a fan of gnome-terminal.  Xfterm4 is better.  Urxvt is also nice.

---

### Post by ghindo on 2008-08-01
> **L815 said:**
> I think if Linux just made software packaging and packages UNIVERSAL ACROSS ALL DISTROS, then many problems would decrease. 
:confused::confused::confused::confused::confused::confused:Well, shoot, why didn't someone think of that in the first place?  All we have to do is decide on a packaging system that everyone can agree on.  Surely among apt, pacman, emerge, rpm and the like, the Linux community can find one packaging system that is completely superior in all ways?

Go.

---

### Post by madjr on 2008-08-01
> **Alasdair said:**
> The Linux standard base already specifies RPM as the universal package format that application vendors should target. Why? Because Novell and Red-Hat said so. Any so called 'Linux unification' will be done by large companies with no say whatsoever from anyone else in the community. And that is why it will always be ignored.

RPM is not a standard in anyway.

because RPM for 1 distro may not work on another rpm based distro

if you want real **cross-distro** installer then read here:

[http://ubuntuforums.org/showthread.php?t=857052](http://ubuntuforums.org/showthread.php?t=857052)


**cross-distro** is key, as **neither apt or rpm** thingie can create real cross-distro packages.

both **deb** and **rpm** suck

---

### Post by Canis familiaris on 2008-08-01
WoW! This thread was supposed to discuss Flash and Solaris and Flash in Linux. But it is moving to APT/RPM/Pacman/0install type of talk.

---

### Post by BDNiner on 2008-08-01
I installed the latest beta flash and it works great. shame it is only 32bit right now, i know it can be run on a 64bit firefox i just wanted to wait until a final version was released before i attempted to install it on my 64bit machine. in the latest version they have fixed the hiding menu's issue as well as not be able to use the scroll wheel when your mouse is over a flash window.

But i have never had issues with flash on sites like youtube. i can watch videos fine. every once in a while the flash sections load up and they are blank, just a white box but a refresh normally fixes that, sometimes i have to restart firefox. but this only happens like 1-2 times every 2 weeks.

---

### Post by init1 on 2008-08-01
> **L815 said:**
> I think if Linux just made software packaging and packages UNIVERSAL ACROSS ALL DISTROS, then many problems would decrease. 
:confused::confused::confused::confused::confused::confused:
Yeah, but that's never going to happen.
The problem I see with Linux is the package dependencies. In Windows, you download an exe and then double click it. In Linux, you have to worry about dependencies. A binary compiled for an old kernel/library isn't going to work on a new system. This also means that if you want a new version of an app, you're probably going to have to update your entire system if it's not in the repos. And if it is in the repos, it might be broken. You can compile it, but then you can't uninstall it as easily.

---

### Post by acelin on 2008-08-01
> **Anurag_panda said:**
> Surf Youtube and then you'll know. :(

Never had any problems with youtube and linux. It actually works better and loads quicker than Windows any day.

---

### Post by cardinals_fan on 2008-08-01
> **madjr said:**
> RPM is not a standard in anyway.

because RPM for 1 distro may not work on another rpm based distro

if you want real **cross-distro** installer then read here:

[http://ubuntuforums.org/showthread.php?t=857052](http://ubuntuforums.org/showthread.php?t=857052)


**cross-distro** is key, as **neither apt or rpm** can create real cross-distro packages.

both apt and rpm suck
That post is misleading.  RPM is not comparable to APT.  APT is a packaging tool, such as yum or urpmi.  RPM is a package **format**, and is comparable to .deb Debian packages.

In general, it's best to have at least a basic understanding of something before saying that it "sucks" ;)

/off-topic

---

### Post by madjr on 2008-08-01
> **cardinals_fan said:**
> That post is misleading.  RPM is not comparable to APT.  APT is a packaging tool, such as yum or urpmi.  RPM is a package **format**, and is comparable to .deb Debian packages.

In general, it's best to have at least a basic understanding of something before saying that it "sucks" ;)

/off-topic

yeah i meant deb

corrected :)

---


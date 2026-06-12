---
title: "Issues and answers - observations."
date: 2010-03-16
forum: Testimonials &amp; Experiences
---

### Post by Sematary on 2010-03-16
This isn't a "help" thread. Just an observation thread.
I installed Ubuntu about a month ago I guess on an older Gateway. It runs great by the way.
I have run into some problems along the way but I managed to solve them with diligent research. Some I still haven't quite puzzled out yet but I will.
Right off the bat, my daughter complained about Yoville (facebook app for those who don't know) freezing up.
I researched and discovered that the consensus SEEMED to be that I needed to remove Flash10 and manually install 9
I did that and it stopped locking up
but....
No sound from flash on any site.
More research
answer seemed to be to uninstall Pulse Audio and revert back to Alsa.
That worked! 
A friend of mine told me AFTER, that I simply needed to uninstall restricted extras (which I did)

Next thing that came up - couldn't connect to my Windows network.
That was an easy fix. I installed SAMBA and I was off and running. What I haven't figured out is why Samba doesn't start it's service automatically or how to get it to.
I thought I had this one figure out but I was wrong. Oh well. I'll get it.
FREEDOOM and PRBOOM, both installable through package manager, don't work. I STILL have yet to solve this one but I guess (from what I read) that developers are working on a solution (yay).

Tuxtype - my daughter uses this. 
The package manager has 1.7.5, not the newest - 1.8.1
I downloaded the tar ball but I can't install it - apparently I need to add some files to resolve dependency issues. Not something I really want to do so I'll wait for the Package Manager to update the program for me at some point in the future.

Canon ip2600 printer
THIS was a bear.
I learned how to start the CUPS service (not too difficult but I don't know how to get that to start at boot either - something I want to figure out when I have more time).
Unfortunately, the newest Ubuntu changed from libcupsys2 to libcups2 so I ran into a dependency issue when attempting to install the drivers.
I did my homework and found a solution and got it to work.

These are most of the issues I've come across, which is why I said yesterday that Linux isn't quite ready for the average user.
Solving these issues was time consuming and required quite a bit of research and a basic knowledge of the terminal (which I am slowly learning).
Many of the solutions I sought required me to use the terminal (or nautilus) and I still don't know what alot of the commands mean but again, I'm learning.

So anyway, I'm sort of hoping that this post will serve as sort of a guidepost to the types of problems that arise for new users to the Linux world and maybe someone can put something together that will help to make resolution of some issues easier for other new users.

BTW - I'm NOT complaining. I love the OS. I really want to add it to my better machine when I'm more comfortable with it.

---

### Post by cariboo on 2010-03-16
Moved to T&E

---

### Post by earthpigg on 2010-03-16
> my daughter complained about Yoville (facebook app for those who don't know) freezing up.

yup, flash support on linux isn't so hot. it's less efficient, and these bloated and poorly written flash games will temporarily lock up your browser (when it turns grey for a few seconds) on a non-super-powerful CPU.

better advice - if it ain't broke, dont fix it. your install of flash was never broken. flash itself, and yoville, and farmville, and the rest, are broken. nothing on your end can fix them.

> Tuxtype - my daughter uses this.
The package manager has 1.7.5, not the newest - 1.8.1

that is normally how this stuff works. ubuntu 9.10, for example, will have the most up-to-date software as of a few months before the _10_th month of 200_9_.

10.04 will have the most up-to-date software as of a few months before the _4_th month of 20_10_.

> Canon ip2600 printer
THIS was a bear.

ya, printers can be a pain.

The biggest advice i can give you is, in the future, do your [hardware compatibility homework]("https://wiki.ubuntu.com/HardwareSupport/") ***before*** making any purchases. i won't buy a wifi card, video card, or printer, unless it is listed there.

---

### Post by Sematary on 2010-03-16
> **earthpigg said:**
> yup, flash support on linux isn't so hot. it's less efficient, and these bloated and poorly written flash games will temporarily lock up your browser (when it turns grey for a few seconds) on a non-super-powerful CPU.

better advice - if it ain't broke, dont fix it. your install of flash was never broken. flash itself, and yoville, and farmville, and the rest, are broken. nothing on your end can fix them.


Bit I did manage to find a solution that actually has everything working in harmony.
:-)




> that is normally how this stuff works. ubuntu 9.10, for example, will have the most up-to-date software as of a few months before the _10_th month of 200_9_.

10.04 will have the most up-to-date software as of a few months before the _4_th month of 20_10_.

In the meantime, developers could make it easier for users to upgrade on their own by including the necessary libraries in the .deb or .rpm files so that installation is a whole lot easier.



> ya, printers can be a pain.

The biggest advice i can give you is, in the future, do your [hardware compatibility homework]("https://wiki.ubuntu.com/HardwareSupport/") ***before*** making any purchases. i won't buy a wifi card, video card, or printer, unless it is listed there.

I had the printer before I had Ubuntu. In fact, I had all of my hardware before I had Ubuntu, so that advice, while sound, doesn't help someone who is installing the OS for the first time and already has all their hardware up and running. The issue with the printer could have more easily have been solved on the developers end by keeping the libcupsys2 file and updating THAT rather than creating a brand new file that drivers won't work with.

---

### Post by earthpigg on 2010-03-16
> In the meantime, developers could make it easier for users to upgrade on their own by including the necessary libraries in the .deb or .rpm files so that installation is a whole lot easier.

if they did include those libraries, then they would replace/update your current libraries. the current libs may be tested with tuxtype, but have they been tested with ***everything*** else that depends on them? 

in linux, we typically have libwhatever installed once. in windows, yes, you very well likely have many many libraries installed several times. it isn't uncommon for 5 different programs to come with 5 different versions of the same libraries. this is part of why (ubuntu + some software) takes up much less hard drive space than win7.

example: 

[tuxtype for ubuntu]("http://packages.ubuntu.com/karmic/games/tuxtype") is 276 kb installed, in addition to whatever libs you need to download/install.

[windows tuxtype]("http://tux4kids.alioth.debian.org/tuxtype/download.php") is a 13800 kb ***download***, and likely much more after it's uncompressed and installed.


if you want the latest and greatest of everything, consider Debian Testing or Arch.

> The issue with the printer could have more easily have been solved on the developers end by keeping the libcupsys2 file and updating THAT rather than creating a brand new file that drivers won't work with.

do you see how this contradicts your last point?

before, you wanted the newest possible software... now you want old software.

three ways of doing this:

1) all the newest software. rolling release distros such as Arch. this is what breaks your printer's functionality, and who knows what else.

2) tried and true super stable, but older, software. this is Debian Stable... which is released about two or three times a decade. This is also the Windows way of doing things - which is why any windows piece of software will include it's own entire set of supporting libraries. which is why Windows requires larger hard drives, more ram, and a faster CPU to accomplish the same tasks as a Linux system. Alternatively, in a Linux implementation of this, things will be super reliable... but old. tuxtype for Debian Stable, for example, is at version 1.5.

3) healthy compromise. Ubuntu 6 month release leans more towards 1, and Ubuntu LTS leans more towards 2. 


many people think option three is the best. we all survived our entire lives without version X of software Y, so we can wait another 6 months to get it.

I assure you that your daughter will have a more recent version of TuxType every six months.

---

### Post by uRock on 2010-03-17
I am glad you are sorting out your problems. As you may know by now, most of these problems have nothing to do with Linux, but more of it falls on companies making compatible drivers. Flash works fine for me, but as you say, you have an older Gateway. I have updated the GPU and such in my daughter's Dell and it still locks up every now and again while playing games. She can't get to Facebook yet, but I am sure she will want to one day.

---

### Post by 3rdalbum on 2010-03-17
I am quite disturbed that Samba and CUPS were not running at startup. They certainly should run at boot time.

The printer problem really means that Canon isn't ready to be distributing Linux drivers, if they can't keep them up-to-date. All they really need to do is distribute a PPD; and they've already got one of those for use with Mac OS X.

Usually for later versions of programs, there are repositories or PPAs containing the later versions. A quick Google search couldn't find an up-to-date PPA for Tuxtype, but you might be able to find one with a bit more time.

BTW Linux is perfectly ready for the average user, when you consider that average users on Windows need to use the MS-DOS prompt, Regedit and Google to find and implement solutions to their problems.

---

### Post by MarcusW on 2010-03-17
Alot of times when you want a newer version of something, there's a package in "Debian Sid" which means you can get a *.deb-file from there. :)

[http://packages.debian.org/search?suite=default&section=all&arch=any&searchon=names&keywords=tuxtype](http://packages.debian.org/search?suite=default&section=all&arch=any&searchon=names&keywords=tuxtype)

---


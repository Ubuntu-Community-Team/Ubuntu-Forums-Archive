---
title: "Eyecandy Galore and desktop acceleration 1 month from now ?"
date: 2005-08-04
forum: The Cafe
---

### Post by NoTiG on 2005-08-04
Im not sure if you all have heard but there has been a recent prerelease of [xorg](http://lists.freedesktop.org/archives/xorg/2005-August/008963.html) and one imporant feature [mentioned](http://xorg.freedesktop.org/wiki/ChangesSince68) : 

>  New EXA acceleration architecture, with experimental support in sis(4) (more to come) 

which confirms other news posted [here](http://dot.kde.org/1119948104/) about exa , and how its planned to be released at the end of september with xorg.

Some relevant quotes you might find interesting [here](http://lists.freedesktop.org/archives/xorg/2005-June/008356.html) 

> 4) Following the 7 steps I outlined above will speed up the common 
desktop usage by quite a bit. Note that you don't have to be a driver 
developer to switch any of those drivers. Note that this also means 
that we can easily give the useless, but oh-so-wanted transparent 
windows to everyone right now. Not next year, not when library X will 
be ready - now, as in today. 
5) Implementing the download/upload/composite hooks will give us enough 
power to have very fancy effects that will let us compete with 
Microsoft/Apple desktops while we work on Xgl. 

and one other important tidbit:

>  Its not dependent on any toolkit, not like Evas which is part of a toolkit. It's in the Xserver and not specific to Qt. 

This is all of course, temporary for when [xgl and glitz](http://www.freedesktop.org/wiki/Software_2fXgl) are ready.

---

### Post by jasmuz on 2005-08-04
Wohooo!!! that sounds great to me!!!! :)

---

### Post by Kyral on 2005-08-04
I don't think it will make it into Breezy.

IIRC the code has been frozen....but I may be wrong and I would love to be proved wrong on this one

---

### Post by NoTiG on 2005-08-04
[QUOTE=Kyral]I don't think it will make it into Breezy.

IIRC the code has been frozen....but I may be wrong and I would love to be proved wrong on this one[/QUOTE]

from the ubuntu wiki: > Feature Freeze date for the Breezy release is 11 august 2005. 

I dont think it will make it either considering that breezy is to be released in october and xorg is not released till the end of september. They wont have enough time to test it and everything, but we will be able to upgrade to it hopefully :P

---

### Post by benplaut on 2005-08-04
[QUOTE=NoTiG]from the ubuntu wiki:  

I dont think it will make it either considering that breezy is to be released in october and xorg is not released till the end of september. They wont have enough time to test it and everything, but we will be able to upgrade to it hopefully :P[/QUOTE]

feature freeze is then. package freeze has already happened...


BTW- what's the name of the version after breezy?

---

### Post by Knome_fan on 2005-08-04
AFAIK the newest X will make it into breezy. So exa will be available to the extend it is available in the X release in September.

---

### Post by Burgundavia on 2005-08-04
From the mouth of our X guy:
<daniels> Burgundavia: the server hasn't been moved over to the modular kit yet, hence no exa. that'll happen sometime this month.

And further info:

<Burgundavia> daniels, the other question that I know will come up on the forums is binary drivers. Will those break with modular?
<daniels> Burgundavia: nvidia no, ati yes
...
<daniels> Burgundavia: iirc ati haven't yet released a fglrx that works with the libdl-based loader
<daniels> (aka 'dlloader')

Corey

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=Burgundavia]
<daniels> Burgundavia: nvidia no, ati yes
[/QUOTE]

My nvidia card just paid for itself.

---

### Post by NoTiG on 2005-08-04
Do the open source mesa driver that can be used with ATI support hardware acceleration at all? will you be able to use them with exa instead??

Why is it that ATI drivers are so bad anyway? Opengl is an open specification... shouldn't the implementation be almost identical on windows as it is on linux ?? Why are they so badly optomized? Something maybe farfetched would be to wonder if ATI and microsoft are in league together. After all they are partnered on the xbox 360.

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=NoTiG]Do the open source mesa driver that can be used with ATI support hardware acceleration at all? will you be able to use them with exa instead??

Why is it that ATI drivers are so bad anyway? Opengl is an open specification... shouldn't the implementation be almost identical on windows as it is on linux ?? Why are they so badly optomized? Something maybe farfetched would be to wonder if ATI and microsoft are in league together. After all they are partnered on the xbox 360.[/QUOTE]

The biggest thing they profit off of are highend cards for workstations and consoles. Highend graphics cards are nice but the volume is low, a lot of money is made in the lowend segment. Thats what most people want. Thats Intel's game.

Blender and Mesa.

Reasons to buy those graphics cards. But only one can survive in that market: Nvidia did it first. May Ati will get in more. I bet. Then Linux graphics would kick ass. Much better than most other parts.

---

### Post by ubuntu_demon on 2005-08-04
[QUOTE=Burgundavia]From the mouth of our X guy:
<daniels> Burgundavia: the server hasn't been moved over to the modular kit yet, hence no exa. that'll happen sometime this month.
Corey[/QUOTE]

So it will make breezy probably ? That will be so cool!!!

I also hope that it will be soon possible to make stuff easily and "permanent" transparent (I don't like transset)

---

### Post by super on 2005-08-04
so is anybody installing this from cvs?

if yes please (pretty please!!) post a howto and some info on how it works.  :grin: 

if you need me i'll be dancing in the streets with glee!!  :razz:

---

### Post by Brunellus on 2005-08-04
H'mm.  Too late for Breezy.  I'll wait for the next one (Grumpy? )

---

### Post by pmj on 2005-08-04
Ooooh I want this right now!

---

### Post by somuchfortheafter on 2005-08-04
[QUOTE=Brunellus]H'mm.  Too late for Breezy.  I'll wait for the next one (Grumpy? )[/QUOTE]

grumpy will never be released lol

---

### Post by Brunellus on 2005-08-04
[QUOTE=somuchfortheafter]grumpy will never be released lol[/QUOTE]
 kind of like e17?

badoom-PAH!

---

### Post by NoTiG on 2005-08-04
A couple of things: according to [this](http://lists.freedesktop.org/pipermail/xorg/2005-June/008325.html) it says xorg 7.0 will be released sept 30 .. so the title of this thread sould have probably been 2 months.

Secondly a couple of things I have pulled from the OSNEws article:
Frome the changelog:
>  Experimental DRI support for Radeon 9500 and above 

> It's good to see DRI development moving forward on ATI's newer chipsets. I have a Radeon 9250(the last series supported by DRI) and have been happy with the DRI(especially since the ATI fglrx drivers don't seem to work with PCI cards), not to mention it's nice to have the drivers come preinstalled with the OS(with our any fuzy licensing legality), not having to install them afterwards. 

>  The DRI drivers for Radeons 9200 and under are quite good, and if you enable S3TC (which is unfortunately patent encumbered), the performance seems to be about on par with the Windows drivers. See here for S3TC: [http://homepage.hispeed.ch/rscheidegger/dri_experimental/s3tc_index.html](http://homepage.hispeed.ch/rscheidegger/dri_experimental/s3tc_index.html)

The current support for the Radeons higher than 9200 is experimental, I have no idea of the performance because I don't own the requisite hardware to try them out. See here: [http://r300.sourceforge.net/](http://r300.sourceforge.net/)

AFAIK, there are no open source 3D accelerated drivers for NVidia cards..

>  DRI performance is quite nice. 2D and general functionality is better than in proprietary drivers. Of course people tell you that the 3D part is not that great, but it does work and gives you the ability to play most games - and it's open-source. The support for 3D DRI in eg. 9600 (R300-series) is now in X.org CVS, which is a great accomplishment, even though it still needs a lot of work (join if you know stuff about video drivers and 3D!). see [http://r300.sourceforge.net/](http://r300.sourceforge.net/) for developer information.

Anyway, NVIDIA doesn't have any working open source driver that gives you 3D acceleration. Its proprietary drivers are still better than ATI's proprietary drivers, but if you value open source and want to get rid of non-free software in your system, your best bet is ATI and the DRI development it has..

[http://r300.sourceforge.net/](http://r300.sourceforge.net/)
[http://homepage.hispeed.ch/rscheidegger/dri_experimental/s3tc_index.html](http://homepage.hispeed.ch/rscheidegger/dri_experimental/s3tc_index.html)

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=Brunellus]kind of like e17?
[/QUOTE]

You joke....but....rasterman hates releases.

---

### Post by Lovechild on 2005-08-04
[QUOTE=poofyhairguy]You joke....but....rasterman hates releases.[/QUOTE]

I thought he only hated users

---

### Post by poofyhairguy on 2005-08-04
Man...the whole Xfree Xorg split is really turning out to be a good thing.

---

### Post by drizek on 2005-08-05
[QUOTE=poofyhairguy]My nvidia card just paid for itself.[/QUOTE]
 ya. i bought a 6600gt and not a single regret. if i was still using my ati card, i probably would have gone back to windows already. 

BTW, ati doesnt just make bad drivers. their opengl performance in windows sucks as well. for linux and opengl in general, nvidia will be king for a long time.

---


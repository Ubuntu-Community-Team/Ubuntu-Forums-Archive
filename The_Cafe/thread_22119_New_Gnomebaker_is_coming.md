---
title: "New Gnomebaker is coming"
date: 2005-03-25
forum: The Cafe
---

### Post by gamehack on 2005-03-25
Hi all,

I just wanted to draw your attention. The new upcoming version of Gnomebaker is coming along... Cue & Bin support has been added and now sports a complete new artwork. If you want to see it, just take a look [here](http://www.1nsp1r3d.co.uk/tmp/gnomebaker/Screenshot.png) . Comments are welcome. You can also notice that the whole style of Gnomebaker is going towards Ubuntu's colour scheme.

Regards,
gamehack

---

### Post by ubuntu-geek on 2005-03-25
Cool cant wait!

---

### Post by BWF89 on 2005-03-25
Why did they release GBaker under the LGPL. Isn't that basically the BSD liscence?

---

### Post by totalshredder on 2005-03-25
Wow, I wonder why the color scheme is going towards ubuntu style... has everyone given in?! When are we going to get gnomebaker in the repositories? I think it's a great program, I'm excited about it!

---

### Post by ubuntu-geek on 2005-03-25
You can add this to your sources.list to pull ubuntu deb's..

 >  # GnomeBaker
deb [http://people.debian.org/~goedson/packages/ubuntu/hoary/gnomebaker/releases/i386/]("http://people.debian.org/%7Egoedson/packages/ubuntu/hoary/gnomebaker/releases/i386/") ./

---

### Post by totalshredder on 2005-03-25
Hey Hey! It works great, haha, thanks UG, I'm happily "baking" away ;). Very nice program, reminds me a lot of K3B though... HMMMMMMMM

Can anybody do the same magic for Beagle? 

Luke

---

### Post by akurashy on 2005-03-25
i kinda like graveman n_n 
though gbaker looks good :)

---

### Post by kassetra on 2005-03-25
[QUOTE=gamehack]Hi all,

I just wanted to draw your attention. The new upcoming version of Gnomebaker is coming along... Cue & Bin support has been added and now sports a complete new artwork. If you want to see it, just take a look [here]("http://www.1nsp1r3d.co.uk/tmp/gnomebaker/Screenshot.png") . Comments are welcome. You can also notice that the whole style of Gnomebaker is going towards Ubuntu's colour scheme.

Regards,
gamehack[/QUOTE]

Wow!  The new gnomebaker looks completely awesome!  Gnomebaker has moved onto my "must have" list!  I can't wait!  :)

---

### Post by TravisNewman on 2005-03-25
[QUOTE=BWF89]Why did they release GBaker under the LGPL. Isn't that basically the BSD liscence?[/QUOTE]
 Not really. They'd just call it the BSD license if it was.

<sarcasm>But you worry about licenses a lot, considering you still use Windows</sarcasm> ;) ;)

---

### Post by lukem on 2005-03-25
[QUOTE=ubuntu-geek]You can add this to your sources.list to pull ubuntu deb's..[/QUOTE]


I'm using warty and downloaded the source from a slightly different repository.

deb-src  [http://people.debian.org/~goedson/packages/ubuntu/warty/gnomebaker/releases/src/](http://people.debian.org/~goedson/packages/ubuntu/warty/gnomebaker/releases/src/)  ./

When I try to install I get:

uke@athalon:~ $ sudo apt-get build-dep gnomebaker
Reading Package Lists... Done
Building Dependency Tree... Done
Package cdbs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package cdbs has no installation candidate
E: Failed to satisfy Build-Depends dependency for gnomebaker: cdbs

I found cdbs and installed it, but still get the same error.  I would greatly appreciate any suggestions.  

Thanks
Luke

---

### Post by TravisNewman on 2005-03-26
did you install cdbs using a .deb file? If not, dpkg and apt won't show it as being installed. You can always use checkinstall, or make a dummy package to make it think you have it installed with a .deb.

If you DID install it with a .deb, then I have no clue, unless you're using an older version

---

### Post by poofyhairguy on 2005-03-26
[QUOTE=gamehack]Hi all,

I just wanted to draw your attention. The new upcoming version of Gnomebaker is coming along... Cue & Bin support has been added and now sports a complete new artwork. If you want to see it, just take a look [here](http://www.1nsp1r3d.co.uk/tmp/gnomebaker/Screenshot.png) . Comments are welcome. You can also notice that the whole style of Gnomebaker is going towards Ubuntu's colour scheme.

Regards,
gamehack[/QUOTE]


At light speed the biggest gripe against Gnome is gone. Now to work on important things, like eye candy to make OSXers hurt with jealously (wobble, wobble).

---

### Post by LongTooth on 2005-03-26
Love Gnomebaker. Question: Sometime ago I went to the Gnomebaker site and downloaded and installed per their instructions (tarball). Will I be able, when it becomes a Ubuntu package, to upgrade? That's my main concern. When I install anything via tarball. Am I 'locked' in. Do I have to delete and start all over again? I love Gnomebaker but not using Ubuntu approved repositories concerns me. Of course this applies to any tarball installed package. Not meaning to deviate from the subject at hand, just how will source installed packages be upgraded? I'd much rather get all of my programs from approved sites which makes upgrading a non issue - ala apt-get. But if I do deviate from the 'norm' will upgrading be a problem? Thanks.

P.S Tarballs have alway scared me. Don't know why but they do. I know lots of folks like them. But they scare the hell out of me. One of my many quirks.

---

### Post by dolson on 2005-03-26
[QUOTE=poofyhairguy]At light speed the biggest gripe against Gnome is gone. Now to work on important things, like eye candy to make OSXers hurt with jealously (wobble, wobble).[/QUOTE]

What was wrong with Graveman?

Not complaining about choices, I'm asking an honest question..

---

### Post by dolson on 2005-03-26
[QUOTE=gamehack]Hi all,

I just wanted to draw your attention. The new upcoming version of Gnomebaker is coming along... Cue & Bin support has been added and now sports a complete new artwork. If you want to see it, just take a look [here](http://www.1nsp1r3d.co.uk/tmp/gnomebaker/Screenshot.png) . Comments are welcome. You can also notice that the whole style of Gnomebaker is going towards Ubuntu's colour scheme.

Regards,
gamehack[/QUOTE]


I don't know if something in Ubuntu was changed in the last week or so, or just that GnomeBaker is a damn good application, but I wasn't able to burn a CD with xcdroast or Graveman OR Nautilus. I haven't tried for about a week, but I installed this and bam! First try. I'll have to try out the others again right now for comparison.

So you're a developer on this project, correct?

I have some suggestions for this program. A lot of it is cosmetic, but I think would help polish it up a bit. This is not a critique, these are ideas. You can reject them if you like, it's cool. I'm starting to teach myself Glade/GTK/C++ development, so who knows, perhaps I could join the team once I become fluent. Heh. Anyhow, onto my suggestions:

---
When Baking a CD, during the Creating data disk image part, if you click View output, the button caption should change to Hide output (or do something sorta like Synaptic when it's installing stuff).
---
[ I had another one in here, but looking at the help file, you already have on-the-fly burning planned. :) ]
---
Can you put an estimated/elapsed timer on there? Should be fairly easy to do once it hits the Burning disk part, just divide the size of the data image by the speed that you're writing at, and you'll have a fairly close estimate.
---
In line with that, you could add, on the far right side, across from "Burning disk..." you could put 450MB of 698MB or something, to show kinda a status. This is only a desire on my part for something more aesthetic than that View output thing. Again, these are only suggestions. The progress bar is nice, the dialog is simple, but I'm sure lots of users like to know more detail than that. Maybe I'm wrong. I dunno.
---
The Create Data Disk and Create Audio Disk buttons could be replaced with Create Disk or something like that in the Actions menu (the type of disk to burn could be determined by what tab is currently focused).
---
An option to disable the prompt on quitting GnomeBaker would be nice. It annoys me to no end when the application always asks me. You could, of course, expand on that, and check if they try to quit without burning a modified CD layout, and then prompt, but skip the prompt if nothing's changed, but that's probably more work than an option in the preferences.
---

Alright, those are my suggestions. Don't take them as insults. Your program rocks, and I think it could become the standard, as opposed to K3B, at least for Gnome users.

Now I just have to see about why I can't mount the freakin' disc:

> $ dmesg | tail
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x50
ide: failed opcode was 100
end_request: I/O error, dev hdb, sector 1024
UDF-fs: No partition found (1)
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x50
ide: failed opcode was 100
end_request: I/O error, dev hdb, sector 64
isofs_fill_super: bread failed, dev=hdb, iso_blknum=16, block=16

On top of that, I can't import the session that I just burned:

> Error getting session information

cdrecord: Warning: Running on Linux-2.6.10-5-k7
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: Success. test unit ready: scsi sendcmd: no error
CDB:  00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 30 00 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x30 Qual 0x00 (incompatible medium installed) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.000s timeout 40s
cdrecord: No disk / Wrong disk!

Anyhow, this is further than the other apps got me, so kudos to that, and I'm glad to finally see some decent GTK burning apps emerge, so I can stop using xcdroast (I ain't installing Qt or KDE libs just to burn CDs).

---

### Post by gamehack on 2005-03-26
[QUOTE=LongTooth]Love Gnomebaker. Question: Sometime ago I went to the Gnomebaker site and downloaded and installed per their instructions (tarball). Will I be able, when it becomes a Ubuntu package, to upgrade? That's my main concern. When I install anything via tarball. Am I 'locked' in. Do I have to delete and start all over again? I love Gnomebaker but not using Ubuntu approved repositories concerns me. Of course this applies to any tarball installed package. Not meaning to deviate from the subject at hand, just how will source installed packages be upgraded? I'd much rather get all of my programs from approved sites which makes upgrading a non issue - ala apt-get. But if I do deviate from the 'norm' will upgrading be a problem? Thanks.

P.S Tarballs have alway scared me. Don't know why but they do. I know lots of folks like them. But they scare the hell out of me. One of my many quirks.[/QUOTE]

The way to go in this case is uninstalling Gnomebaker from sources and installing a packages. If you want to uninstall it, go to the source directory where you compiled it and type
```

make uninstall

```
and you're ready to go. Then you can install a package without worrying of screwing things up.

Regards,
gamehack

---

### Post by lukem on 2005-03-26
[QUOTE=panickedthumb]did you install cdbs using a .deb file? If not, dpkg and apt won't show it as being installed. You can always use checkinstall, or make a dummy package to make it think you have it installed with a .deb.

If you DID install it with a .deb, then I have no clue, unless you're using an older version[/QUOTE]
 Thanks for the help panikedthumb.  Unfortunately I could not find cdbs among my repositories and i installed from a tarball.  For repositories I have universe, multiverse, main restricted, warty security universe, 3 marillats and the goedson site where I got gnomebaker.  Do you know where I could get a deb for cdbs?  I've thought about just waiting for hoary and trying again.
Thanks
luke

---

### Post by Buffalo Soldier on 2005-03-26
[QUOTE=poofyhairguy]At light speed the biggest gripe against Gnome is gone. Now to work on important things, like eye candy to make OSXers hurt with jealously (wobble, wobble).[/QUOTE]
Any post/reply to any anti-gnome message must be ended with -> **(wobble, wobble)** :)

---

### Post by bigzak on 2005-03-26
[QUOTE=BWF89]Why did they release GBaker under the LGPL. Isn't that basically the BSD liscence?[/QUOTE]

Not at all. The licences are as follows:

GPL - Cannot use this code, or even link to it, from non-GPL code
LGPL - Cannot use the code in non-GPL,  but can dynamically link to it from anything
BSD - Do whatever you like, but maintain credit and copyright information

---

### Post by poofyhairguy on 2005-03-28
[QUOTE=LongTooth]When I install anything via tarball. Am I 'locked' in. [/QUOTE]

Not completely. There is a way to wrap your tarball installs with a debian package label. I don't know how, I think installing packages by hand (as in from source) is the devil. If I was you I would delete the sucker when you find a deb....

I will comb Google for hours trying to find packages I want to in order keep myself from installing anything from the source (add in extra time for using alien to convert RPMs). So far, the only program I REALLY want to use that I can't find a compatible package for is Beagle. The day I find that deb is the day I throw a party....

I'm actually trying to make a beagle deb myself. Anything is better than source installs that apt-get doesn't see...

---

### Post by LongTooth on 2005-03-28
I'm so glad to know there are others that feel the same way I do about tarballs/source packages. Maybe if I was to get deeper into them I wouldn't feel this way. But I find them messy. Too messy for my taste. 

I want my system to be as easy to maintain and configure as possible. Apt-get does this for me. Source packages do not convey that same feeling. And so If at all possible - and that is not alway doable - I will stay from them when I can.

I don't know what I'm going to do when there is a new version of Gnomebaker (to get back to subject) in the Ubuntu repositories. I'll cross that bridge when I come to it. 

But to answer the question that started this thread, Gnomebaker is the one! The killer app that Gnomers were looking for.

---

### Post by Reb on 2005-03-30
Back on the license... anyone know why Luke Biddell (the lead dev) chose LGPL instead of GPL? It doesn't matter to me, either way, it's just strange.

---

### Post by jdodson on 2005-03-30
[QUOTE=Reb]Back on the license... anyone know why Luke Biddell (the lead dev) chose LGPL instead of GPL? It doesn't matter to me, either way, it's just strange.[/QUOTE]

so he could link non-free code to gnomebaker?  

if the issue bugs you that much you can use graveman.  graveman is a cool program(in hoary universe) and i use it when nautilus doesnt the way it should(audio cd ripping for instance).  i still use k3b still for video dvds.

---

### Post by Reb on 2005-03-30
[QUOTE=jdodson]so he could link non-free code to gnomebaker?  

if the issue bugs you that much you can use graveman.  graveman is a cool program(in hoary universe) and i use it when nautilus doesnt the way it should(audio cd ripping for instance).  i still use k3b still for video dvds.[/QUOTE]Nah... like I said, it doesn't bug me. And I understand the general reason, I was wondering about a specific one (e.g. what non-free code).

---

### Post by jdodson on 2005-03-30
[QUOTE=Reb]Nah... like I said, it doesn't bug me. And I understand the general reason, I was wondering about a specific one (e.g. what non-free code).[/QUOTE]

no idea, you could email the author though.

---

### Post by vaskark on 2005-04-05
[QUOTE=ubuntu-geek]
                              # GnomeBaker
 deb [http://people.debian.org/~goedson/packages/ubuntu/hoary/gnomebaker/releases/i386/]("http://people.debian.org/%7Egoedson/packages/ubuntu/hoary/gnomebaker/releases/i386/") ./
[/QUOTE]
This repository isn't currently available. Can't wait for the new version - it looks really good!

---

### Post by lukem on 2005-04-05
[QUOTE=panickedthumb]did you install cdbs using a .deb file? If not, dpkg and apt won't show it as being installed. You can always use checkinstall, or make a dummy package to make it think you have it installed with a .deb.

If you DID install it with a .deb, then I have no clue, unless you're using an older version[/QUOTE]
 I gave up and upgraded to hoary then installed it from the other source.  It's great.

---

### Post by Xappe on 2005-04-08
so when is gnomebaker 0.3.1 with bin/cue support coming? i'm in the need for easy burning of bin/cue images :)

---

### Post by mike998 on 2005-04-08
[QUOTE=Xappe]so when is gnomebaker 0.3.1 with bin/cue support coming? i'm in the need for easy burning of bin/cue images :)[/QUOTE]

I installed K3B just to burn a bin/cue image...  Now I have a bunch of KDE libs on my hdd that I don't usually use or need.  I dont see bin/cue support coming any time soon on the Gnomebaker website.

---

### Post by Xappe on 2005-04-13
well, I referred to the first post of this thread that states that bin/cue support is on it's way...and it even has a screenshot, so I thought it would be out soon...

---

### Post by goedson on 2005-04-16
[QUOTE=vaskark]This repository isn't currently available. Can't wait for the new version - it looks really good![/QUOTE]

It is available again.  And hoary packages are now available through universe.

---

### Post by goedson on 2005-04-16
[QUOTE=gamehack]Hi all,

I just wanted to draw your attention. The new upcoming version of Gnomebaker is coming along... Cue & Bin support has been added and now sports a complete new artwork. If you want to see it, just take a look [here](http://www.1nsp1r3d.co.uk/tmp/gnomebaker/Screenshot.png) . Comments are welcome. You can also notice that the whole style of Gnomebaker is going towards Ubuntu's colour scheme.

Regards,
gamehack[/QUOTE]

And for those wanting to try it right now, I've just made a package from a CVS snapshot as of yesterday at my repository. Binaries available for Hoary and Debian Sid. See [my GnomeBaker page](http://www.ubuntulinux.org/wiki/GnomeBaker)  for complete URLs.

---

### Post by escuchamezz on 2005-04-16
why don't you just copy K3B? wouldn't that be easier  :razz:

---

### Post by Psquared on 2005-04-18
Cool!!!

Gnomebaker works great for me. Graveman could not detect the CD/DVD on my laptop. Gnomebaker worked straight out of the box on Warty.

---

### Post by nharihar on 2005-04-18
[QUOTE=Psquared]Cool!!!

Gnomebaker works great for me. Graveman could not detect the CD/DVD on my laptop. Gnomebaker worked straight out of the box on Warty.[/QUOTE]
 wish I coul say the same :( The install went well (used .deb he he!!) fired up GnomeBaker.  It found both drives (Toshiba DVD and Teac CD/RW) popped in a cdrw with old data and tried to blank it... the blanking window had just one word for me "Failed" ;((  will try to work on it on wed, meantime if somebody's had a similar problem please help me.  

I've gotten hooked on GnomeBaker and cant live without it. Puhleeeease help me.

(will post the error log tomorrow)

---

### Post by ubuntu_demon on 2005-04-19
[QUOTE=nharihar]wish I coul say the same :( The install went well (used .deb he he!!) fired up GnomeBaker.  It found both drives (Toshiba DVD and Teac CD/RW) popped in a cdrw with old data and tried to blank it... the blanking window had just one word for me "Failed" ;((  will try to work on it on wed, meantime if somebody's had a similar problem please help me.  

I've gotten hooked on GnomeBaker and cant live without it. Puhleeeease help me.

(will post the error log tomorrow)[/QUOTE]
 did you try starting it up with sudo ?

---


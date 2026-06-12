---
title: "Burning .CDI (Dreamcast) Games"
date: 2010-07-28
forum: Wine
---

### Post by DaftPyramid on 2010-07-28
I am attempting to burn Dreamcast games in the .cdi format. I've been unable to find any method of doing this within Linux. 

I've resorted to using DiscJuggler with Wine. The program seems to work perfectly, and the discs burn without issue, but they never work. The console seems to recognize the disc (i.e. it doesn't just say 'Insert Game Disc'). When I try to play a burned game, the screen fades to black like normal, you can hear the disc "spin up", and then promptly "spin down", and the console resets (show's the Dreamcast logo, etc). 

At this point, I don't know whether it's a problem with my DiscJuggler settings, with Wine's emulation of DiscJuggler, with my burner, with my Dreamcast, or with something else. 

My Dreamcast was manufactured in September 1999, which supposedly makes it capable of playing burned games. I'm using standard 700mb CD-R discs as you're supposed to. I've tried just about every combination of settings within DiscJuggler. I honestly have no idea what the problem is. 

I would ultimately like to find a way to burn .cdi files within Linux, rather than using DiscJuggler via Wine.

Any help would be greatly appreciated, thank you in advance.

Note: I only intend to burn free, homebrew games and backups of games that I already own.

---

### Post by 2Karl on 2010-07-28
try turning the DC upside down (This is a serious suggestion). I had a similar issue with a variety of consoles. I don't know what difference it makes, but it seems to make SOME difference.

---

### Post by linux18 on 2010-07-28
dd if=(your file) of=(your cd drive)

maybe

---

### Post by DaftPyramid on 2010-07-28
Thanks for the replies, I'll try the upside down thing later.

linux18, how do I determine the name of my CD Drive?

---

### Post by linux18 on 2010-07-28
its usually /dev/sr0 but you may need to check the path in its properties/ right click icon > properties

---

### Post by DaftPyramid on 2010-07-28
Well none of the above tricks worked, and now the burning process stops at 100%. It just continually stays in the "finalizing discs" part of the process, and it won't let me eject the disc.

So I really need a new method. I'm sick of wasting CD-Rs.

---

### Post by DaftPyramid on 2010-07-30
Bump

---

### Post by DaftPyramid on 2010-08-03
Okay, so I burned a couple of games with my friend's Windows PC, and they work. So that rules out any problems with my Dreamcast or the CD'Rs that I'm using. The problem is either with DiscJuggler or my burner. I'm leaning towards DiscJuggler right now. 

I'd still love to find a way to burn .cdi files from within Linux. Either that, or figure out how to get Alcohol 120% to work in Wine.

---

### Post by weihenstephan on 2011-01-10
I know, this answer is way too late, but as new Dreamcast software is still released you may be still interested in it for burning another project :-)

A few years I've written ago I've had exactly the same problem, so I decided to port cdi2nero by DeXT to Linux ([http://digitalimagecorp.de/software/cdi2nero/](http://digitalimagecorp.de/software/cdi2nero/)). The downside is that you need the commercial Nero for Linux to burn the resulting image.
The same author has also written an application called CDIrip which is basically the same application, but extracts the tracks to individual files instead. Those can be used to burn the CD manually from the command line. There's a good tutorial at [http://poptix.net/CDI-HOWTO.txt](http://poptix.net/CDI-HOWTO.txt) - the patched cdrecord doesn't seem to be necessary any more though.

---


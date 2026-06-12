---
title: "Aquatic Desktop Eyecandy"
date: 2005-09-07
forum: The Cafe
---

### Post by Arktis on 2005-09-07
[http://xdesktopwaves.sourceforge.net/](http://xdesktopwaves.sourceforge.net/)

Screenshots are included on that page.  Runs nice, highly configurable.  All it needs is a gui config tool.  I think it should be included with future ubuntus.

---

### Post by klepas on 2005-09-07
Whoa! Thanks for the link. :)

---

### Post by xmastree on 2005-09-07
How does one get it working? According to the readme, I just type 'make'
Presumably in the same directory... but I just get a bunch of errors. Loads of errors.
```
xdesktopwaves.c:31:22: X11/Xlib.h: No such file or directory
xdesktopwaves.c:32:23: X11/Xutil.h: No such file or directory
xdesktopwaves.c:33:23: X11/Xatom.h: No such file or directory
xdesktopwaves.c:34:34: X11/extensions/shape.h: No such file or directory
xdesktopwaves.c:64: error: syntax error before "xdwOptEnd"
xdesktopwaves.c:64: warning: data definition has no type or storage class
xdesktopwaves.c:76: error: syntax error before "xdwOptDoubleBuffer"
xdesktopwaves.c:76: warning: data definition has no type or storage class
xdesktopwaves.c:78: error: syntax error before "xdwOptIdle"
xdesktopwaves.c:78: warning: data definition has no type or storage class
xdesktopwaves.c:83: error: syntax error before "xdwOptWavesByMouse"
xdesktopwaves.c:83: warning: data definition has no type or storage class
xdesktopwaves.c:84: error: syntax error before "xdwOptWavesByWindows"
xdesktopwaves.c:84: warning: data definition has no type or storage class
xdesktopwaves.c: In function `xdwSetDefaultOptions':
xdesktopwaves.c:138: error: `False' undeclared (first use in this function)
xdesktopwaves.c:138: error: (Each undeclared identifier is reported only once
xdesktopwaves.c:138: error: for each function it appears in.)
xdesktopwaves.c:150: error: `True' undeclared (first use in this function)
xdesktopwaves.c: At top level:
xdesktopwaves.c:169: error: syntax error before "xdwParseInt"
xdesktopwaves.c: In function `xdwParseInt':
xdesktopwaves.c:178: error: `False' undeclared (first use in this function)
xdesktopwaves.c:189: error: `True' undeclared (first use in this function)
xdesktopwaves.c: In function `xdwParseOptions':
xdesktopwaves.c:256: error: `True' undeclared (first use in this function)
xdesktopwaves.c:337: error: `False' undeclared (first use in this function)
make: *** [xdesktopwaves.o] Interrupt
```That interrupt was me hitting ctrl-c so that I could see the first errors, otherwise it spews out loads.
 ](*,)
I searched synaptic for those three missing files, but the closest I got was xutils, which doesn't contain any of them.

---

### Post by drummer on 2005-09-07
hehe... neat...
installed fine for me, just a make, sudo make install. Maybe a bad/corrupted download or something? all the readme says is it needs gcc by default, not much else there :(

---

### Post by GeneralZod on 2005-09-07
[QUOTE=drummer]hehe... neat...
installed fine for me, just a make, sudo make install. Maybe a bad/corrupted download or something? all the readme says is it needs gcc by default, not much else there :([/QUOTE]

Based on those error messages, it looks like it also needs the x11 development headers. 

I'm not at my Kubuntu machine right now, but search synaptic for 

x11 dev

or something like that.  Is there no "configure" script provided? It's unusual to see source packages without one.

---

### Post by drummer on 2005-09-07
Could be it.. looked in synaptic and saw i have libx11-dev installed already can't remember what for??)

---

### Post by xmastree on 2005-09-07
Looking at the source, xdesktopwaves.c
```
#include <sys/times.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <time.h>
#include <errno.h>
#include <signal.h>
#include <unistd.h>
#include <math.h>
[COLOR=Red]#include <X11/Xlib.h>
#include <X11/Xutil.h>
#include <X11/Xatom.h>
#include <X11/extensions/shape.h>[/COLOR]
```Do you have those files anywhere on your system? I don't.  :neutral:

---

### Post by jobezone on 2005-09-07
Install **apt-file**, then do:
```
sudo apt-file update
apt-file search Xlib.h
```
It will tell you which package in your repositories contains that file.

---

### Post by drummer on 2005-09-07
Those 4 files are located at:
/usr/X11R6/include/X11/Xlib.h
/usr/X11R6/include/X11/Xutil.h
/usr/X11R6/include/X11/Xatom.h
/usr/X11R6/include/X11/extensions/shape.h

They are installed by the libx11-dev package.. apt-getting that _should_ do the trick.

---

### Post by xmastree on 2005-09-07
[QUOTE=drummer]Could be it.. looked in synaptic and saw i have libx11-dev installed already[/QUOTE]Aha... that was it. Thanks  :grin:

---

### Post by cnayak on 2005-09-07
[QUOTE=Arktis][http://xdesktopwaves.sourceforge.net/](http://xdesktopwaves.sourceforge.net/)

Screenshots are included on that page.  Runs nice, highly configurable.  All it needs is a gui config tool.  I think it should be included with future ubuntus.[/QUOTE]

 The insallation went o.k. But on running xdesktopwaves, I get the following error:

 [I]X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  15 (X_QueryTree)
  Resource id in failed request:  0x1400018
  Serial number of failed request:  136
  Current serial number in output stream:  136[/I]

 Any idea of what's missing?

---

### Post by minio on 2005-09-07
apt-get install xdesktopwaves ? :)

---

### Post by cnayak on 2005-09-07
[QUOTE=minio]apt-get install xdesktopwaves ? :)[/QUOTE]

  I guess that won't solve it. I had installed Scilab using apt-get. Got a similar error.

---

### Post by N8MAN1068 on 2005-09-07
nice!

my only problem, is that i have icons on the desktop and a black background.
when running this, the background gets greenish (probably need to try all of the color options), but the desktop icons get fuzzy.....any suggestions on settings?
i've already tried all of the listed transparency switches.

---

### Post by GoA on 2005-09-07
It wasn't so nice after all. Got it working easily. Used it, looked quite ok. Removed it. Not beatiful enough and made basic desktop usage a big mess.

---

### Post by crun on 2005-09-07
thanks for the apt-file tip jobezone, you learn something new every day on these forums

---

### Post by poofyhairguy on 2005-09-07
Neat concept....but its more one of those "make all of your Windows friends jealous when they are over at your house and turn it off right afterwards" type things. Like Luminocity.

---

### Post by byen on 2005-09-07
hey poof. just did that... you have no idea..what this did to my roomie.. 
I just left my laptop lyin around on my couch...made him just see it himself....
-takes a glance
-Eyes widen   0.0
-Eyes narrow down with focus ^.^
-jaw starts dropping 
-denial --says it may not be stable
-realises --says..that is the coolest
-withdrawl and acceptance  - "would it run on my graphics card too?"

LOL...UMMM Im lovin it! thanks for the link!
PS- seems to be taking a ton of Processor share...not sure if it would work for daily use...only time will tell.

---

### Post by poofyhairguy on 2005-09-07
[QUOTE=byen]hey poof. just did that... you have no idea..what this did to my roomie.. 
I just left my laptop lyin around on my couch...made him just see it himself....
-takes a glance
-Eyes widen   0.0
-Eyes narrow down with focus ^.^
-jaw starts dropping 
-denial --says it may not be stable
-realises --says..that is the coolest
-withdrawl and acceptance  - "would it run on my graphics card too?"
[/QUOTE]


My favorites for that are the 3D Desktop switcher and E16's minimize trick!

---

### Post by Arktis on 2005-09-07
After reading about people's difficulties (and easy successes) as well as critiques, I want to add a few things.

1.)  This is a toy.  If you are worried about performance, you definately shouldn't have it on all the time.  Personally, I have two vid cards and a 2 ghz athlon.  On the AGP 128 MB NVIDIA card, it runs smooth and wonderful and loverly.  On the PCI 64 MB NVIDIA card, it's laggy and clunky (especially when trying moving a window).  Also I am unable to get good performance out of 3d games unless I turn it off.  Anyhow, this leads me to believe that it's more reliant on your video card's muscle power than your cpu's, but a low-end cpu would probably still be able to hurt performance; just not as much as a low-end card.

>  my only problem, is that i have icons on the desktop and a black background.
 when running this, the background gets greenish (probably need to try all of the color options), but the desktop icons get fuzzy.....any suggestions on settings?
 i've already tried all of the listed transparency switches.

2.)  It appears to put horizontal bars across your desktop.  My desktop is also black with no wallpaper and when I run xdesktopwaves, it it creates the same effect.  I don't know if this is configurable or not.  I haven't really played with any of the options.  I didn't know about the icon problem though, because I have no icons on my desktop.

3.) It's highly flexible.  Just looking at what you can do by adding arguments to the command is neato, and may yeild noticable performance boosts.  But it isn't perfect and IMHO it's not finished and needs more features/methods of drawing itself.

4.)  Suprisingly, it IS stable.  This came as a shock to me personally.

5.)  Sorry to those who had install troubles.  I didn't have any, but then again I always load my system with all the extra libraries and dev packages I come across.

As development on this continues, you can bet your sweet bippy I'll be following it.  Hopefully my next computer is going to kick so much butt that running xdestopwaves won't even make it blink.

---

### Post by ubuntopia on 2008-11-08
I'm a newbie to Ubuntu so very much loving all the desktop effects available to this OS.

It comes as a bit of a disappointment that horizontal bars appear across the desktop wallpaper with xdesktopwaves. This app would be perfect if it functioned similar to the Compiz Water Effect.

Looks like the app hasnt been updated for some time. The info at SourceForge shows the following:
  xdesktopwaves - 1.3
  Last Update: Dec 18 2004 
So it's either on the back burner or abandoned. Hopefully one day we'll see some modifications.

However if you use the Opaque option with Color then it looks okay. So if you have a plain desktop (no wallpaper) then this may work for you, although you'll lose your desktop icons. :(

---


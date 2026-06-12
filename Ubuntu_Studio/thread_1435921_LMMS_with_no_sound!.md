---
title: "LMMS with no sound!"
date: 2010-03-22
forum: Ubuntu Studio
---

### Post by RamenNoodles on 2010-03-22
My LMMS has no sound ,that's like a pool with no water.

I'm obviously too new to know what i'm doing as far as this wikki link goes. This is the only real information on how to troubleshoot this that iv found but iv only been using Linux for a few days and this seems ridicules compared to the windows installation. 

LMMS working using the alsa driver...

[http://lmms.sourceforge.net/wiki/index.php?title=Installation](http://lmms.sourceforge.net/wiki/index.php?title=Installation)

I just don't understand why this installs easier in a windows OS than on a linux distro that it was meant to be run on.

LMMS Version 0.4.5 (Linux/!386, Qt 4.5.2, GCC 4.4.1)

OS: Ubuntu Studio ISO

My System Monitor: Release 9.10 (karmic) Kernel Linux 2.6.31-9-rt GNOME 2.28.1

Is there any other way of doing this?

---

### Post by cchhrriiss121212 on 2010-03-22
If you are using studio then you already have LMMS installed, you just need to get it working. You can run LMMS using two different sound servers: ALSA or jack. Jack is the best option for audio work on linux but alsa will be simpler in the short term.
I have tried using LMMS with jack on my machine without much trouble, so try starting it up from the applications menu. It will likely give errors when it starts but that is normal, just post what you get in the message window.
To use ALSA: it looks like you have already posted the solution in that link. What part of it do you not understand?

---

### Post by RamenNoodles on 2010-03-22
I'm kind of stuck hear...
In aplay -l ; arecord -l my device reads 0



2. Now in terminal type gksu gedit /etc/pulse/default.pa 

 #load-module module-alsa-sink
 #load-module module-alsa-source device=hw:1,0

TO...

load-module module-alsa-sink device=hw:x
load-module module-alsa-source device=hw:x
-------------------------------------------------
???????????
device=hw:0
device=hw:0

this can also be hw:x,x

iv done the rest of the steps and nothing?

---

### Post by cchhrriiss121212 on 2010-03-23
Ok so what you need to do is change these two lines:
#load-module module-alsa-sink
 #load-module module-alsa-source device=hw:1,0

to these:
load-module module-alsa-sink device=hw:0[COLOR=blue][FONT=monospace]
[/FONT][/COLOR][COLOR=Black]load-module module-alsa-source device=hw:0

Is that what you have done? Make sure you delete the # symbols.
[/COLOR]

---


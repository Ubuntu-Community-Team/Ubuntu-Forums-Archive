---
title: "ardour plugins cause system lockup"
date: 2009-04-18
forum: Ubuntu Studio
---

### Post by musicmatt on 2009-04-18
I just recorded my first session in ardour, and am in the processes of mixing it down. I have been having a lot of problems with plugins in Ardour causing my system to lock up.  (I'm new to linux, and not very good with command line, so please be very specific about any advice concerning it);
here is what happens:

The plugins will work fine for the most part,  but sometimes when I adjust a parameter on them, the audio tracks they are applied to and my system monitor will hit the roof, and even moving the mouse will become extremely sluggish. The system usually stays functional enough for me to quit programs, and I find that when I kill Jack (which will be xrunning like crazy by then), the system functions normally again. This makes me suspect the problem lies in the interaction between jack and the plugins.  

 I'm mainly using steve Harris' Multband EQ and the c* compressor, although I have had the problem with other plugins too.  

Occasionally, the glitch will just cause the tracks with the plugins to go into perpetual peak, and not affect the system.  I can fix this by disabling the plugins.  Also, in this case, when I delete and replace the problem plugin (with the same one) the problem goes away for a while.

help?

---

### Post by thorgal on 2009-04-18
you may need to protect your session against denormals. When plugins are fed with data approaching extremely small values (~ 0), they will just blow out your CPU :lol: 

There are ways to avoid this, ardour has implemented a few denormal tricks. Which version of ardour are you using ? the latest (2.8 ) has a track option when you right-click on the track name in the mixer strip called "protect against denormals". The global option about denormals (method used) can be found in the main menu Options -> Denormal Handling -> methods.
You can also try the "Stop plugins with transport" option: Options -> Misc -> Stop plugins ...

It could also be a whole different problem though.

---


---
title: "Musician switching from Windows"
date: 2009-05-23
forum: Ubuntu Studio
---

### Post by The Switch Blade on 2009-05-23
Hi,

I have been using Windows my entire life but have recently switched to Ubuntu 9.04. Winehq tells me that guitar pro works okay, but sibelius and finale do not. Reason, as expected, is apparently very slow and crashes.

Guitar pro works pretty badly on my machine, and tuxguitar isn't nearly as versatile as guitar pro is. For what I do, I need to be able to write midis in guitar pro and export them to Sibelius for score writing, and also through Reason to generate MP3s.

Are there no ubuntu equivalents for what I want to do? It seems that I will have to reinstall Windows. =/

Thanks.

---

### Post by NE Key on 2009-05-23
Without any knowledge of your particular preferred music programmes...

I expect that you can find a number of substitutes but you may have to kiss a few frogs before you find a prince.

---

### Post by B4RR13N705 on 2009-05-23
If what you need is write midis, and then get mp3s, you maybe like rosegarden to write midis, or maybe a keyboard with a synth. Then recorded it to mp3 trough Ardour :)
Oh, in google, there are a lots of tutorials to make Guitar Pro work fine in Ubuntu, and how to increase perfomance :P

---

### Post by barisurum on 2009-05-24
For finale with wine you should follow [this]("http://www.tipsfor.us/2006/12/26/run-finale-2007-on-linux-with-wine/") page. It works on my machine quite good.

Its highly recomended that you use JACK+wineasio to be able to sync and connect finale and other win32 programs with your audio+midi hardware and linux programs (such as ardour, rosegarden, hydrogen). Otherwise you'll experience sound/gfx weirdness.

For Reason 3 I tried it too and the result was same (too slow, garbage), but I heard that Reason 4 works flawlessly with wine, but I can't confirm this, you'll have to try.

---


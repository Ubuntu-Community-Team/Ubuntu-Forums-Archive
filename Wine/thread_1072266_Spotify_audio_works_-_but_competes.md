---
title: "Spotify audio works - but competes"
date: 2009-02-17
forum: Wine
---

### Post by methodmarvel on 2009-02-17
I think this is a pulse audio problem, or ALSA - I'm not certain as audio on linux is very confusing for me

I am running ubuntu 8.04, wine 1.1.14 and spotify 0.3.10 (it installed really easily).

The problem is I loose audio across by system (flash videos, songbird, totem) after starting spotify. On stopping spotify I get my audio back.

If audio is running from my general system (songbird, flash video, totem) spotify can't play music.

I had a similar problem with flash which is fixed by installing "libflashsupport" which I still need to do even for flash 10.

Any ideas? Is there a "libwinesupport" for audio?

---

### Post by methodmarvel on 2009-02-17
So - I kind of solved my own problem with a "work around".

I changed my wine audio settings to use EsounD instead of alsa so I guess my system uses alsa through pulse audio and then wine is using EsounD through pulseaudio?

If anyone could explain that to me it would be cool. Also if there is a better way (I mean, should I be using ALSA?) that would also be awesome.

Thanks

[IMG]http://lh3.ggpht.com/_N0d9xGSt9-M/SZqsOLogZmI/AAAAAAAAAJs/UfaUrHYuESc/s800/Screenshot-1.png[/IMG]

---

### Post by dirtylobster on 2009-03-25
Much love for the Esound "fix".

---

### Post by giacomolg on 2009-05-11
yeah, thanks a lot! I wish I could help but the matter is quite confusing for me as well.

---


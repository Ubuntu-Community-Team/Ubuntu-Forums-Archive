---
title: "Playing an MP3 Audacity sounds choppy"
date: 2012-06-24
forum: Ubuntu Studio
---

### Post by MrBalloonHands on 2012-06-24
So I imported an MP3 into Audacity, but I play it, it's very choppy. Please keep in mind that I choose JACK in the drop down menu right underneath editing tool bar. I also have a choice to select ALSA, but now sound comes out that way. Maybe someone can show me how to set that up if needed. 

If your thinking that CPU usage and memory use may be an issue, I checked that and they are both in the mid teens % when I'm running the program and playing the file. 

IF anyone has any ideas, they would be greatly appreciated.

Thanks ahead of time

---

### Post by CrocoDuck on 2012-06-25
If you need Audacity working with jack try to tweak Audacity preferences (Ctrl+P). Matching them with jack settings is enough for good performances in my system.

Have a look at your imported mp3 sample rate. Resample the file if the sample rate is different from the jack sample rate (dunno if you have to do it, but the files that matches sample rates are working great with me). You can select project frequency in the bottom menu. You could install Sound Converter. It can convert audio files menaging a lot of formats and you can also specificate the sample rate (or give a look to "man ffmpeg").

You can also use Audacity without jack, select the right in end out device setup in the menu that you said (ALSA should be the choice if you don't have jack running).

---


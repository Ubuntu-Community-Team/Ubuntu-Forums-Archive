---
title: "Toggen .ogv to avi"
date: 2008-12-19
forum: Ubuntu Studio
---

### Post by ClarkePeters on 2008-12-19
I use Thoggen to rip my dvds for backup (with .ogv extension). It's great in that I can rip a whole two hour dvd down to just over 300mb file size and it still plays great on the computer (although for files I might burn back to a Dvd I save them around 695mb).

Now I need to burn them and I'm having a time of it because the files convert back at too large a size.  I tried using mencoder converting from ogv to avi, but the avi is 840mb so by the time I get it in iso form, it's over five or six gigs.

```
mencoder -o out.avi -noidx -oac copy -ovc copy SpongeBob.avi
```

I need it to be around 650 -700mb as I have always had success at this size going from avi to iso (Using ffmpeg, dvdauthor, then mkisofs). Is there something I can add to the above code to reduce the resulting output, say reduce the bitrate or something?

The other option I used was using VLC to convert the .ogv to .mpg (mpeg-ps) and then using ffmpeg to get it dvd ready, then dvdauthor, then mkisofs, but that iso was too large too.  I also used avidmux to try converting the avi and also the mpg (each individually converted from the ogv) but again too large. 

Any advice would be appreciated.

---

### Post by eye208 on 2008-12-19
> **ClarkePeters said:**
> I tried using mencoder converting from ogv to avi, but the avi is 840mb so by the time I get it in iso form, it's over five or six gigs.
If you have an Ogg video file that you want to turn into an MPEG-2 file for DVD, why do you turn it into an AVI file first? You are inserting an additional encoding step that is totally unnecessary. Waste of time, waste of quality.

> I need it to be around 650 -700mb as I have always had success at this size going from avi to iso (Using ffmpeg, dvdauthor, then mkisofs).
If the MPEG-2 file turns out too large for a single-layer DVD-R, it's because the chosen bitrate is too high. The bitrate of the input file doesn't matter at all.

---

### Post by ClarkePeters on 2008-12-19
Thanks eye208, I think you hit the nail on the head. It's the bitrate I need to change for the output file, let me give that a try.

---

### Post by ClarkePeters on 2008-12-19
AvideMux has a bitrate calculator;
for me, one dvd-r one-layer 4.7gb disc, I just set it to mpeg and dvd5 and it adjusted the bitrate. It's converting now, we'll see how that works.

Here is the flash tutorial that walked me through it.
[http://mulder.dummwiedeutsch.de/etc/adm_wink/avi2dvd.htm]("http://mulder.dummwiedeutsch.de/etc/adm_wink/avi2dvd.htm")

---


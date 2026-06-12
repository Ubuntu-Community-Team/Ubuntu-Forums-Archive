---
title: "how come gnash and swfdec have the same bugs Flash has..."
date: 2008-04-29
forum: The Cafe
---

### Post by madjr on 2008-04-29
i just tried gnash and swfdec. They work...

but both have most of the same bugs Flash does...:
[http://bugs.adobe.com/jira/browse/FP-120](http://bugs.adobe.com/jira/browse/FP-120)
[http://bugs.adobe.com/jira/browse/FP-114](http://bugs.adobe.com/jira/browse/FP-114)


i support both initiatives, but **is incredible how they copy almost everything from flash, even the bugs they were trying to fix**...

i even got a lockup in firefox with swfdec, because it got too slow... (just like v9,0,124)

gnash is a bit faster than swfdec but not faster, nor less buggy than v9,0,48 at this time....

so, how come these bugs? we now have 3 buggy flash players... :confused:

if gnash and swfdec can't fix it being open, who will?

or maybe the culprit is not flash of these bugs?

Note: this is not a rant but some tests I've been doing to compare and get to the bottom of these bugs. The bugs in flash are not showstoppers, but they're only present in linux and not in other OSs

---

### Post by saulgoode on 2008-04-29
Perhaps because Flash is a poorly-designed format?

---

### Post by jespdj on 2008-04-29
Maybe because those bugs are not bugs in Flash at all, but bugs in the rendering engine of your browser (which places the Flash on top of everything) or in your graphics card driver?

Regarding the video performance bug: What graphics card do you have, and what driver are you using? Can you play other videos (not Flash) with good performance? Or is your Internet connection too slow, so that it can't download the streaming video fast enough?

---

### Post by madjr on 2008-04-29
> **jespdj said:**
> Maybe because those bugs are not bugs in Flash at all, but bugs in the rendering engine of your browser (which places the Flash on top of everything) or in your graphics card driver?

Regarding the video performance bug: What graphics card do you have, and what driver are you using? Can you play other videos (not Flash) with good performance? Or is your Internet connection too slow, so that it can't download the streaming video fast enough?

i too wonder if it's mozilla rendering engine, but it happens in opera also...

i got an dell inspiron 1420, dual-core 2.0ghz, Nvidia 8400M GS, 2 gb ram.

i got ADSL 756 kbps (more than enough)

so it's not my laptop, because in windows it goes smooth.

you tried fullscreen youtube? u get any drop in framerate ?

---

### Post by jespdj on 2008-04-29
I have a Dell XPS M1530 (2.5 GHz Core 2 Duo, nVidia 8600M GT) and a 20 Mbit/s ADSL connection (very fast!).

A normal format YouTube video plays completely smoothly, but full-screen it is indeed not completely smooth, with Adobe Flash on FF 3b5.

My laptop is more than powerful enough to play full-screen video, so it looks very likely that there's a problem in the Flash software...

---

### Post by madjr on 2008-04-29
> **jespdj said:**
> I have a Dell XPS M1530 (2.5 GHz Core 2 Duo, nVidia 8600M GT) and a 20 Mbit/s ADSL connection (very fast!).

A normal format YouTube video plays completely smoothly, but full-screen it is indeed not completely smooth, with Adobe Flash on FF 3b5.

My laptop is more than powerful enough to play full-screen video, so it looks very likely that there's a problem in the Flash software...

yea the linux v9,0,48 goes extremely well in full screen, no hic ups or drop in frame rate.

Even higher def like veoh.com runs extremelly well.

v9,0,115 and 124 are really steps backwards in flash for linux development.

each time flash has more bugs (but only ours.. even the mac version with an extremely similar architecture does not have these bugs):mad:

If we don't vote or file the bugs (get their attention), who knows what other bugs they'll throw at us in the next versions....

---


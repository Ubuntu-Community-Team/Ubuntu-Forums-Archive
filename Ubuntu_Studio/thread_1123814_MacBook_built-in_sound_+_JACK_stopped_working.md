---
title: "MacBook built-in sound + JACK stopped working"
date: 2009-04-12
forum: Ubuntu Studio
---

### Post by Aurora on 2009-04-12
Greetings,

Has anyone found a way for Jack to work with the Intel HDA sound on a first generation MacBook?

I have a v1 MacBook with Ubuntu Studio 8.04, rt kernel, Alsa 1.0.18 ( Alsa just upgraded; did not affect problem).  I used to be able to run Jack with the built-in sound (unless my memory is lying--a slight possibility)  Now no amount of tweaking the settings gets a stable running Jack.  AFAIK it will work with my USB sound device, but I would like to sometimes work with Rosegarden and Hydrogen when I'm away from home, without dragging the interface along.

For example, if I use 256 frames/period and 4 period/buffer, I get this error:

late driver wakeup: nframes to process=512

scrolling by over and over, with things like

delay of 5620.000 usecs exceeds estimated spare time of 5695.000; restart..

on occasion.

Increasing the frames/period will yeild the same error, with "nframes to process" always twice the frames/period.  At 1024 frames/period, it shuts down.  If I decrease periods/buffer to 2, I get massive xruns.

I've been searching these forums and Googling the error messages, but haven't found a solution yet.  Any ideas?  Maybe I just need to find a nice, portable USB soundcard?

--Paul in Seattle

---


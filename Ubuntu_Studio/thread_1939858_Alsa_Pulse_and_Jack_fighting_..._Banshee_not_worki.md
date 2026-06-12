---
title: "Alsa Pulse and Jack fighting ... Banshee not working."
date: 2012-03-12
forum: Ubuntu Studio
---

### Post by randomas on 2012-03-12
I'm using lucid.
Jack works, and programs with direct pulse-audio plugins work, audacious works. 

The generalist ubuntu gstreamer powered programs don't. Gst is working perfectly because all its tests work. 

Totem gives: 

failed to connect to stream no such entity.

I started having these problems after installing the kxstudio ppa, which I have since removed.

I know this depends on per user settings, I created a new user and and there banshee works fine. 


Any help or a link to where this has already been solved would be great. I looked but didn't find a solution.

TIA

---

### Post by randomas on 2012-03-13
Ok, solved the issue was in the Gconf system gstreamer default settings ...

I posted a png of my non-working settings, to get it back working I changed all the audiosinks to autoaudiosink and the descriptions to Default. Now everything is working as normal.

Jack does however suffer from more xruns ... I need to find a way to switch from one to the other ...

---

### Post by BcRich on 2012-03-13
Hi randomas
glad to hear you got it sorted out :) I remember having a problem with JACK starting when I added some software from the kxstudio PPA a while back. Also had to uninstall the software and decided not to use that PPA anymore. I can't remember the exact details of how I managed to fix JACK but I remember that it had something to do with my original settings being changed to use an onboard audio chip instead of my external USB sound device, I subsequently had to use a pulseaudio tool to disable the onboard sound (might have been pavucontrol). JACK seems to work fine for me now with about a 5-8msec latency, and xruns only occur when I have a span of effects and tracks (in ardour) or for certain synth sounds. I'm using U.Studio 10.10 x64

---


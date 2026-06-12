---
title: "xruns from usb sound card"
date: 2011-01-18
forum: Ubuntu Studio
---

### Post by halfbeing on 2011-01-18
My USB sound card has been performing very badly recently. When I used it before, which was a long time ago, I didn't have this problem.

It is an Edirol UA-1EX (i.e. pro audio). It used to perform much better than my internal HDA adapter, but now it generates huge numbers of xruns even at very high latencies while the HDA adapter, strangely, seems to be performing much better than I remember it. If it weren't for audio quality issues using the internal audio would be an acceptable alternative.

I presume that the problem is something to do with interrupts, but I've no idea how to diagnose it or deal with it. One thing I have tried has been to boot with acpi=off, but this rendered the adapter completely incapable of producing sound beyond some rhythmic clicking.

One thing that may be pertinent is that the audio apps I am having trouble with are both Windows apps (Reaper and Tracktion). I am connecting them via a very old version of wineasio for 64-bit because recent versions make my applications freeze. I didn't seem to get the same problem when I did a little test with Rosegarden, although I didn't put it under heavy load. Then again, the same set-up worked fine with the internal adapter.

How can I get my audio interface working properly again?

many thx

---

### Post by bapoumba on 2011-01-19
Moved to Ubuntu Studio.

---

### Post by halfbeing on 2011-01-19
But surely Ubuntustudio is the same stuff?

One thing I am going to try is using 32-bit instead of 64-bit Ubuntu. I've not been having the same problem with Rosegarden, so it looks like it is just to do with the Windows apps and I've been having problems with 64-bit wineasio. In any case that should enable me to build Ardour with VST enabled.

---


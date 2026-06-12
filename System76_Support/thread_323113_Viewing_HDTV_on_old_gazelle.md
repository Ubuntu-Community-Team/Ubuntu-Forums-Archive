---
title: "Viewing HDTV on old gazelle"
date: 2006-12-21
forum: System76 Support
---

### Post by newlinux on 2006-12-21
Hello,

I have the old gazelle 12.1"

I've recently got a somewhat working mythtv setup going, and I'm trying to use my laptop as a mythfrontend. Using mythfrontend I am able to view any non Hidef station just fine on my laptop, but all HDTV stations simply show a blue screen? Is this a hardware limitation (screen  or graphics) or is there something I can configure to allow me to display HDTV content from mythtv? I'm sure it is not a network problem because I can stream HDTV to another one of my PCs using the same connection.

When I get home tonight I'll probably run a few more tests to see if I can isolate the problem, but if anyone has suggestions (or I'm trying something that won't work) let me know.

---

### Post by superm1 on 2006-12-22
> **newlinux said:**
> Hello,

I have the old gazelle 12.1"

I've recently got a somewhat working mythtv setup going, and I'm trying to use my laptop as a mythfrontend. Using mythfrontend I am able to view any non Hidef station just fine on my laptop, but all HDTV stations simply show a blue screen? Is this a hardware limitation (screen  or graphics) or is there something I can configure to allow me to display HDTV content from mythtv? I'm sure it is not a network problem because I can stream HDTV to another one of my PCs using the same connection.

When I get home tonight I'll probably run a few more tests to see if I can isolate the problem, but if anyone has suggestions (or I'm trying something that won't work) let me know.

This is typically hardware limitations.  Some cards do allow for overrides in their xorg.conf device section to use more video ram.  If your card supports this sort of thing, I have heard it can help the situation.  You can also use X11 playback instead of Xv, but you won't have video that is even close to smooth.  You will drop about 7/11 frames.

---

### Post by newlinux on 2006-12-23
Thanks - it does appear to be a hardware issue. I tried to play a local HDTV stream and got an "insufficient resources" error message. I can always transcode...

---


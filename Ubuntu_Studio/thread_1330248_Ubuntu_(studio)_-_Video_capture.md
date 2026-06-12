---
title: "Ubuntu (studio) - Video capture"
date: 2009-11-18
forum: Ubuntu Studio
---

### Post by x86-64-Scotland on 2009-11-18
Hi,

I'm looking to setup either ubuntu 9.10 or ubuntu studio, purely to capture data from VHS (and some other legacy video formats). I wish to capture the audio and video, and store it digitally. Does anyone have any suggestions to which video capture devices and software I should be looking at?

Also are there any known problems using AMD CPUs rather than Intel for such things?

TIA

---

### Post by TheShader on 2009-12-18
I'm going to ask the same question... Bump :confused:

---

### Post by wkulecz on 2009-12-18
Unfortunately, support for analog video capture hardware is pretty poor.  In fact I don't know of any that are supported and are still in production.

My only suggestion would be to try and find an analog video to DV firewire converter like the old Canopus ADVC-100 and capture the DV stream it outputs with Kino.  Some DV camcorders with external A/V inputs can do on the fly analog to DV over firewire conversion.

Another work around might be to get a standalone DVD Recorder box and make your tapes into DVDs which you could then rip and end up with MPEG2 files.  These would be 3-4X smaller than analog to DV captures over firewire.  

Another possibility would be to look for a TV card that has external video and/or S-video aux inputs that works with MythTV. You could then use MythTV to record your tapes.

If your quality demands are modest, any video4Linux TV tuner card (BT8x8, SAA71xx, etc.) can capture a passable MJPEG file with XawTV or TVTime viewer software.

HTH,
--wally.

---

### Post by lisati on 2009-12-18
> **wkulecz said:**
> 
Another work around might be to get a standalone DVD Recorder box and make your tapes into DVDs which you could then rip and end up with MPEG2 files.   

+1. After experiencing some frustration with a capture card that I put in one of my boxes, even with the Windows software that came with it, this is my choice for one of my cameras that doesn't have a digital connection and for VHS.

---


---
title: "Help with Ardour and recording from USB (Zoom H4)"
date: 2009-09-15
forum: Ubuntu Studio
---

### Post by texla on 2009-09-15
I'm not finding a way to get Ardour to recognize my USB mic (Zoom H4) in the Input section for a recording track.  It is recognized and works well in Audacity.  I have it selected in JACK as the device to use but all I seem to get are the PC mics.   I've read several posts that say they have an H4 running well with Ardour but no how - to's.  I'm running Ubuntu Studio in Jaunty.    Anyone got any ideas?

For now I'm recording in  Audacity and converting them to FLAC files to import into Ardour for editing - it works but would like to see Ardour do the whole job if possible.

edit: found the fix by adding the audio user permissions here:
[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

---

### Post by texla on 2009-09-16
more info:
Jack seems very flawed - won't open in default without an error and doesn't do anything to aid a usb device for Ardour either. Been racking the forums at Ardour with this to no luck. Also, various sound programs don't seem to open at all (don't know if this is because of Jack):
Meter Bridge, Patchage, Jack Time Machine and others (Audacity, Hydrogen and Ardour do open)

And the Real Time Kernel is very slow... but that could be because of my 512 MB RAM 
(but Jaunty in the vanilla kernel is lightning fast with same RAM) - will be upgrading RAM shortly but just testing out apps until I do with this...

OK just wondering if anyone has any experience with these issues - seems I've been striking out with my questions now for a while, tons of looks and no replies - hope this breaks the trend!

---


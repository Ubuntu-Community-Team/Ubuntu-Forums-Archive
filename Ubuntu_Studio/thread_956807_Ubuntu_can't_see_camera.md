---
title: "Ubuntu can't see camera?"
date: 2008-10-23
forum: Ubuntu Studio
---

### Post by Wilson1990 on 2008-10-23
I've only had Ubuntu for about a week so I'm pretty much a noob.

My problem is I can't get my camera(Nikon D80) to connect to my comp.
Ubuntu knows it's there because a folder shows up in "Computer" called USB Drive but when I try to open it an error message appears saying "Unable to mount location, can't mount file"

---

### Post by tacticalbread on 2008-10-24
try looking in /media for the removable drive.

---

### Post by skullmunky on 2008-10-31
I just plugged in my D80 and it automounted at /media/sdc1.  However, it doesn't work 100% of the time; sometimes when I go to copy files off it, I get a similar error about the location not existing, sometimes in the middle of a copy.  Other times it works fine.  I'm not sure why, exactly.  Sometime a reboot helps.

Also you can run ```
dmesg
``` in the terminal.  It should tell you that it's found a new USB storage device, that it's a SCSI direct access Nikon D80, things like ```
[sdc] 3932160 512-byte hardware sectors (2013 MB)
``` which tells you that the device is /dev/sdc and will probably be mounted at /media/sdc1, etc.

If it does have errors connecting that'll help you track it down.

---

### Post by dunkar70 on 2008-10-31
I would recommend you simply get a USB card reader. This will eliminate your problem and will not wear down your camera's battery. Just don't forget to put it back into your camera when you're done copying files. I know I hate it when I leave home and all of my cards are on my desk.

---


---
title: "Ubuntu server 10.04 32 bit doesn't boot only passes bios"
date: 2011-05-04
forum: Server Platforms
---

### Post by clmbngbkng on 2011-05-04
I've been running 10.04 server for 3 months from a fresh install. I have been installing updates while Bind9, Apache2 and Samba worked just fine. The last time I installed updates was 3 weeks ago and it worked just fine.

Today I ran into problems where the system stopped doing its DNS stuff and wouldn't respond to pings over the network. Since I couldn't get it to respond with a keyboard and monitor attached to it I shut it down through the power switch. I then tried to restart the machine and all it would do was go through the bios and show a cursor flashing in the upper left or this odd color pattern on the screen and then reboot

I have tried pulling the HD and loaded it into my Ubuntu desktop and loaded the file system just fine. I then tried using the "rescue a broken system" option Ubuntu 10.04 32bit install disk and it seems to just sit at a flashing cursor.

I've seen some odd things pop up on the screen at times but mainly would be a flashing cursor in the upper left part of the screen.

[http://img689.imageshack.us/i/photo8e18f2043103735ee9.jpg](http://img689.imageshack.us/i/photo8e18f2043103735ee9.jpg)
[http://img20.imageshack.us/i/photob42584601d593b4d98.jpg](http://img20.imageshack.us/i/photob42584601d593b4d98.jpg)

Any ideas on what I can do?
Thanks!

---

### Post by volkswagner on 2011-05-04
Seems like a hardware issue.

From your post it seems you can't even boot a live CD.

Time to check all hardware.

Run Memtest for a full pass with your liveCD, reseat all cards, try removing as much auxialary equip, drives, modems, usb connected stuff, etc.  

From the screen shot seems likely a video card issue.

---

### Post by HugoSerrano on 2011-05-04
Yep... I agree with "Seems like a hardware issue."

Try to replace GPU

---

### Post by clmbngbkng on 2011-05-04
> **HugoSerrano said:**
> Seems like a hardware issue.

That is what I was thinking and of course it is a problem we all hate to have. 

If it shows the live CD prompt just fine before I select any settings is that still a GPU problem?

I'll run a memory test of it soon and report back here.

Thanks for you help!

---

### Post by clmbngbkng on 2011-05-05
Tested the memory, found a problem and took it out. Things seem to be working as they should. 

Thanks for the help!

---


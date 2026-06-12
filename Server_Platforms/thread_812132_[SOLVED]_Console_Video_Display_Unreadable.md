---
title: "[SOLVED] Console Video Display Unreadable"
date: 2008-05-29
forum: Server Platforms
---

### Post by tim.n9puz on 2008-05-29
I updated a small server from 6.06 LTS to 8.04 LTS earlier today. Everything seems to be working well except for the console. I can ssh into the machine just fine.

The machine has a VIA motherboard and an old VGA display. The console is rarely used *but* now that I've upgraded to 8.04 just before the login prompt appears the video mode changes, the screen changes to light blue, and it is left trying to use some mode that either the integrated display adapter or my old monitor do not support.

How do I configure the system to just stay in "plain old" 80x25 monochrome video mode?

Thanks,

Tim

---

### Post by quelx on 2008-05-29
Here is a discussion regarding framebuffers and console resolutions

[http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2007-09/msg01670.html](http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2007-09/msg01670.html)

---

### Post by tim.n9puz on 2008-05-30
> **quelx said:**
> Here is a discussion regarding framebuffers and console resolutions

[http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2007-09/msg01670.html](http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2007-09/msg01670.html)

I've tried various vga=<something> settings seen here and elsewhere. The result is always the same so far: the message says whatever I entered is an undefined video mode then a list is presented. There are 8 items on the list. I've tried them all and the result is always a scrambled, blue, unreadable screen.

I sure don't want to revert back to 6.06 LTS just in case I ever need to use the console.

Tim

---

### Post by tim.n9puz on 2008-05-30
Just an update to the problem. I have still not resolved this. Just to be on the safe side I have now tried the system with 3 other monitors. All have the same results.

Tim

---

### Post by tim.n9puz on 2008-05-30
The system is working although I am not totally happy with my solution. After the upgrade from 6.06 LTS to 8.04 LTS the 2.6.24-17-386 kernel was loaded and set as the default. My video problems seem to all be related to using this particular kernel with the VIA motherboard and chipset.

I changed the default kernel in grub to 2.6.15-51-386 (the next most recent in the list) and the server now boots fine and displays a nice, simple monochrome console should I ever need it.

I wish I had time to delve into this further but a) I'm not a kernel guy, and b) I need to move on with productive work. I have plenty of time invested in this upgrade at this point.

Tim :confused:

---


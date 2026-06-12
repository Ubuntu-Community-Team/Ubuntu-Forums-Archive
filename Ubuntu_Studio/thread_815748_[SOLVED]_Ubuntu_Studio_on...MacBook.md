---
title: "[SOLVED] Ubuntu Studio on...MacBook?"
date: 2008-06-01
forum: Ubuntu Studio
---

### Post by Aurora on 2008-06-01
Greetings,

I run Ubuntu Studio Gutsy on my desktop, but I have this 1st gen MacBook I bought for college audio production coursework, and just thought I'd try installing Ubuntu Studio on it.

Turns out Apple hardware is allergic to realtime kernels, so I ended up with regular Ubuntu.  I would like to get Ubuntu Studio on this thing instead of generic Ubuntu. Is there a way to get a choice of kernels with Hardy?  My Gutsy install gives me a whole slew of them in the GRUB menu, but Hardy gives only one choice.

Thanks,

Paul

---

### Post by Stochastic on 2008-06-01
Just install the new kernel (or entire ubuntustudio-audio package).  The new choice should appear in the grub menu on reboot.

---

### Post by Aurora on 2008-06-05
Since I had a working Hardy install, I just installed some of the Ubuntustudio packages into it. Oddly, it gives me kernel choices that neither a clean Ubuntu Studio nor a generic Ubuntu install gives me.  The default kernel doesn't boot, but I can scroll down to one that does.  Eventually I'll figure out how to make that the default; I've edited GRUB menus before.

My outboard sound/MIDI device works right off, no tweaking or compiling drivers:)  I was playing with software synths and even recorded a little bass line.  In Feisty and Gutsy I have struggled with this to no avail, but they put a fix in the Hardy kernel, so now it just works.  This is just too cool.

--PD

---


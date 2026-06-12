---
title: "Virtualization cpu usage"
date: 2008-02-03
forum: Virtualisation
---

### Post by arphaus on 2008-02-03
I dipped my toes in Ubuntu for a month last spring, and went back to XP when I was in dire need of some hard drive space, and after another annual XP reinstall, I'm sick of it.

There are some non-gaming Windows apps that I need to use - some seem to work with WINE (Photoshop CS 2) and others (Flash) will probably need to be used in a virtualized OS.  I'd originally considered waiting til I got a new laptop in summer to make the move (setup the new one while the old one was available for working, etc), but as XP's performance is decaying faster than usual, I'm itching to make a switch.

My main Q is what kind of a cpu hit does virtualization involve?  I know that RAM can be allocated (I've got 2gb now vs 1gb last spring), but I wonder if my 2ghz Centrino can handle a guest OS to run Flash or something else periodically.

Right now, it seems I use RAM more than the CPU, so perhaps making a switch wouldn't be that big a deal.


thanks,

Arp

---

### Post by hyperair on 2008-02-04
I run Windows XP, happily photoshopping on my Virtualbox. It runs on a P4 2.66GHz without HT, and no VT-extensions and whatnot. The CPU usage for the whole computer put together is approx 25%

---

### Post by arphaus on 2008-02-04
That sounds perfect!  I don't play games (and I think I'll keep a dual-boot for that), and my CPU hit is rarely above 30%.  RAM usage otoh is variable, though affected way too much by Firefox and Photoshop memory leaks.

Now to find some free time to reformat, reinstall and keep my wife from getting to irritated by the whole process :-P

---

### Post by arphaus on 2008-02-06
Doh - I realized that I can get an idea of cpu usage by virtualizing Ubuntu inside my current XP install.  I feel like I just bumped my head and saw the word 'eureka' by chance...

---

### Post by hyperair on 2008-02-06
I'm not sure, but I reckon virtualizing Ubuntu in Windows is quite different from virtualizing Windows in Ubuntu.

---

### Post by arphaus on 2008-02-06
I'm sure it's not exact, but I should get an idea of what my cpu hit will be.  The main thing I'm curious about is what the cpu hit for VirtualBox itself will be.

---

### Post by fjgaude on 2008-02-06
From my experience with both VBox and VMware server there is no "CPU hit", unless you are using the virtual for something. When in Ubuntu you can't tell that vmware is loaded and working, of course nothing is running in the background.

You can change the NICE for the virtual if you find that necessary.

---

### Post by arphaus on 2008-02-06
NICE?  I'll give VirtualBox a go next week.  After that, I'll try to revive an old Thinkpad P166 that's been closeted for a few years :-P

---

### Post by fjgaude on 2008-02-06
NICE is a priority setting for CPU and memory. Use the man pages to understand the command usage.

---

### Post by arphaus on 2008-02-06
Thanks for explaining.

---

### Post by VMan on 2008-02-07
As to CPU utilization, I couldn't answer.  However, flash playback is choppy on my machine in a virtual XP.  I'm using a Toshiba A135-S4467 (upgraded to 2G RAM, 250G HD).  This laptop has a rather crappy video card (may be the problem) and a 1.6G Core 2 duo CPU.  Hope this give you an idea of what to expect.

---

### Post by arphaus on 2008-02-07
Thanks.  My hope is that I can use Flash like hyperair mentioned using Photoshop.  Thankfully, I don't use it too frequently but it is an unfortunate necessity.

---


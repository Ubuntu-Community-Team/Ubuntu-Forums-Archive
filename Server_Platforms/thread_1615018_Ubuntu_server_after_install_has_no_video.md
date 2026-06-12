---
title: "Ubuntu server after install has no video"
date: 2010-11-06
forum: Server Platforms
---

### Post by holocene on 2010-11-06
Greetings,

Problem:
When it boots up, there is no video. 

Sequence of events:
1. Install ubuntu server 10.04 from cd iso. 
2. finish installation, no problems detected.
3. reboot and no video from Ubuntu. I do get video from the motherboard splash etc.
4. Press shift and e, added nomodeset 
5. rebooted, still no video.
6. OS does boot, and I can hear it accept my id and password. And I can shutdown with sudo shutdown -h now.
7. try ubuntu 10.10 server and go to step 2. (No change)

For the fun of it, tried Puppy Linux without issues. 

Hardware environment:
motherboard Asus A7N8X.
Ram: 512MB
Video: card from around 2002 (not pci, can not recall the name of the slot)
Frustration level: high.
Note: years ago this box ran win without issue. 

Any tips or pointers to doc appreciated.
Regards
Steve.

---

### Post by Vegan on 2010-11-06
I usually use integrated video with Linux as I prefer to use highly integrated boards even in the early days.

My old P4 before it croaked had integrated video and it was fine.

Now I have a slightly newer machine that has a newer chipset. It also works fine and I can use high-res text on it.

---

### Post by holocene on 2010-11-07
No integrated video for me so no answer I guess. 

> **Vegan said:**
> I usually use integrated video with Linux as I prefer to use highly integrated boards even in the early days.

My old P4 before it croaked had integrated video and it was fine.

Now I have a slightly newer machine that has a newer chipset. It also works fine and I can use high-res text on it.

---

### Post by arnavk007 on 2010-11-07
you have an agp card
btw what do you mean by video
ubuntu server has no gui

---

### Post by holocene on 2010-11-07
> **arnavk007 said:**
> you have an agp card
btw what do you mean by video
ubuntu server has no gui

AGP, that's what I could not remember...

no video output on the monitor.

---

### Post by arnavk007 on 2010-11-07
try checking vga port and everything
also is video working with some other os

---

### Post by P4man on 2010-11-07
try adding

```
vga=0 nomodeset
```

to your kernel options.

---

### Post by holocene on 2010-11-07
> **P4man said:**
> try adding
 
```
vga=0 nomodeset
```
 
to your kernel options.
 
Fantastic info. will try and report back.
Best Regards
Steve.

---

### Post by holocene on 2010-11-07
> **holocene said:**
> Fantastic info. will try and report back.
Best Regards
Steve.

Tried all options mentioned on this thread without effect, except this one. I did get screen output this time. Instead of booting into the OS like I had before (albeit without video output), I got some obscure error. 

I am giving up on U Server on this old hardware and trying something else. 

But this hardware seems destined for the trash. 

What else does not work:
Freenas (will install and video works, but hangs up on boot after hard drive install because it does not "recognize" cd drive ???)
Freebsd - same error as above, no mystery to that. 
U Server - nope.
Fedora - getting video only after vga=0 nomodeset for live cd boot. We will see what happens. EDIT: Did install and boot!

Thanks to all for the tips.
Steve.

---


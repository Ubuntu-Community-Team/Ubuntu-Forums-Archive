---
title: "ServalP Keyboard stopped working this morning"
date: 2009-11-14
forum: System76 Support
---

### Post by Replicon on 2009-11-14
Hi folks,

After last night, it seems my keyboard isn't working on my Serval Performance. I'm running 8.04, FWIW, but it was working fine until this morning after I booted up. I did notice that the system76 driver was updated a few times since. Running it on command line (sshing into my laptop) just says everything is up to date.

I don't think it's a hardware problem, because the keyboard seems to work fine BEFORE Ubuntu starts loading. So, during the GRUB countdown, I can hit caps lock and see it flashing, or I can hit escape and select from different modes, etc. Even if I select the latest "recover mode", it still doesn't seem to work.

---

### Post by Replicon on 2009-11-14
Quick update (this started to work right after I submitted the thread)

After some searching, it seems that adding i8042.reset to the kernel command line in grub fixes the problem.

I'll add it to my menu.lst for now, to retain sanity, but I'd like to know if anyone knows the root cause of this? The only updates that came through yesterday were tzdata and the system76-driver, and only one of them seems like it could be a culprit. ;)

Also, maybe I am failing at google this morning, but there doesn't seem to be lots of info on what "i8042.reset" really is. Am I just telling it to reset some devices after kicking off the kernel, so they start up properly in the environment?

Thanks!

---

### Post by Replicon on 2009-11-15
...and now it mysteriously started working (I forgot to add it to menuu.lst). I guess all it needed was a good night's sleep. Sounds like some kind of hardware issue.

---

### Post by thomasaaron on 2009-11-16
Which Serval version do you have? The System76 Driver will tell you.

---

### Post by Replicon on 2009-11-17
> **thomasaaron said:**
> Which Serval version do you have? The System76 Driver will tell you.

serp4

---

### Post by thomasaaron on 2009-11-17
Hmmm... Well, let me know if it happens again, and we'll dig deeper.

---

### Post by Replicon on 2009-11-18
I added it to my menu.lst, since it started happening again. It's almost like there's a race condition or something.

---

### Post by thomasaaron on 2009-11-18
So, are you saying that since adding the flag to your kernel line you're good? Or has it happened *since* then?

I'm definitely not familiar with that as a fix, and I'm definitely not seeing this problem across the board.

Does it happen if you boot into a *previous* kernel?

---

### Post by Replicon on 2009-11-20
> **thomasaaron said:**
> So, are you saying that since adding the flag to your kernel line you're good? Or has it happened *since* then?

I'm definitely not familiar with that as a fix, and I'm definitely not seeing this problem across the board.

Does it happen if you boot into a *previous* kernel?


Adding the flag seems to have fixed it consistently. Not once did I experience the problem with the flag being there.

I haven't tried with a previous kernel, but I think the current one's been around for a long time. (current == 2.6.24-25-generic)

I'll play around with the previous kernel this weekend if I have time. Very rarely, I encounter a case where it freezes entirely right after grub. Other rare times, I get the "no keyboard" but it's been good for a long, long time. Then it started acting up, and I lucked out and found that fix. I tried going back and forth with and without it, and it correlated 100% with it being there. But like I said, I'm having trouble tracking down exactly what it's supposed to do. I just know that it fixed someone else's keyboard on this forum a long time ago. :)

---


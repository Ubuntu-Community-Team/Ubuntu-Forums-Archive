---
title: "Things I don't like about 9.04"
date: 2009-08-15
forum: Testimonials &amp; Experiences
---

### Post by fred! on 2009-08-15
Hey guys,

Just a shot summary of things I don't like about 9.04.

- Getting pulseaudio to work is a pain. I believe this was much easier using 8.04 and with 9.04 I finally gave up.

- And without pulseaudio getting sound from flash is no sure thing. 

- Backlight switched off after suspend. Switching to another tty and back temporarily solves the issue.

- Ctrl-Alt-Backspace is disabled. Why?

- Screen gets blurry after restart. This seems to happen only after a restart. Booting the system from scratch never resulted in this problem. Check out the login menu I get after a restart:
[IMG]http://img35.yfrog.com/img35/2450/blurryloginmenuafterres.png
[http://img35.yfrog.com/i/blurryloginmenuafterres.png/]("http://img35.yfrog.com/i/blurryloginmenuafterres.png/")

I'll be happy to hear your experiences (and solutions) 

Cheers,
Fred!

---

### Post by moster on 2009-08-15
Did you before had problems? Did you upgrade or clean install?

---

### Post by fred! on 2009-08-15
I upgraded from 8.04. Getting pulseaudio to work under 8.04 was not easy (in my opinion), but I managed in the end. 
The screen problems only occurred with 9.04. 

Fred

---

### Post by wojox on 2009-08-15
Have you gotten Pulse-audio working yet?

Ctrl+Alt+backspace was disabled to prevent new users from accidentally losing data by invoking this combo. Doesn't really make sense.

Anyway you can:
```
sudo apt-get install dontzap
```

Then 
```
sudo dontzap --disable
```
To turn Ctrl+Alt+backspace back on to kill X server.

Don't have answers for back light or screen blur.

---

### Post by HappyFeet on 2009-08-15
I would run hardware diagnostics software if I were you. Video issues like that are usually hardware related. Why does everyone assume every problem is software related? I do pc repair for a living, and can tell you that 20% of all computers I see have some kind of hardware issue. Please don't tell me that windows runs well and it can't be hardware related. Until you do run diagniostics and eliminate hardware as the issue, I stand by what I say.

---

### Post by harry2006 on 2009-08-15
some features are disabled/removed to avoid any accidental misuse...

---


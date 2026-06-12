---
title: "Audacity only shows the first six hours of any file."
date: 2008-07-16
forum: Ubuntu Studio
---

### Post by pi.boy.travis on 2008-07-16
Hi.  I am new to Audacity and this is something I noticed through my time playing around with it.  I don't think that I will ever need to edit more that six hours (it is actually somewhere around six hours and eleven minutes) of sound, but it's still bizarre.  Is there just a setting I can change, or is this really a bug?  I am using version 1.3.4 beta, and I have plenty of disk space in my temporary directory.  Any suggestions?

Thanks!

---

### Post by pi.boy.travis on 2008-07-24
anyone?

---

### Post by thorgal on 2008-07-24
it sounds like a limitation due to the conversion uint to time. I see the same in ardour, except that it is exactly twice the time you are reporting. Ardour uses uint32 (or nframes_t) in its code. And the maximum it translates into time is 12h25 or something like that. I don't think this is a coincidence.

---

### Post by pi.boy.travis on 2008-07-24
Is there any way to remedy this?

---

### Post by aeiah on 2008-07-25
according to this page:
[http://www.audacityteam.org/wiki/index.php?title=Recording_length](http://www.audacityteam.org/wiki/index.php?title=Recording_length)

it is to do with a 32bit limitation (although its reportnig 13 hours, so i guess you're using a higher sample rate?) either way, this limitation was remedied in 1.3.3b. either you have some weird configuration or they took the feature out of 1.3.4.

---

### Post by pi.boy.travis on 2008-07-25
I installed right out of the Ubuntu repository.  I am running 32 bit Ubuntu 8.04 on a Dell Insipron 1520 with 2 GB RAM and an Intel Core 2 Duo.  Any way I can fix this?

---


---
title: "odd serval resume noises?"
date: 2008-07-24
forum: System76 Support
---

### Post by majoridiot on 2008-07-24
i was just wondering if anyone else had noticed an occasional issue when resuming from suspend on the
serval...

occasionally, after resuming and popping up the password login, it will make a series of fast, high-
pitched beeps... maybe 7 or so total, that sound kind of like an alarm.  it does not do this every 
time and i've tried in vain to reliably reproduce it.  there doesn't appear to be anything out
of order with the logs i've looked at, either.

other than the random "alarm", the unit resumes just fine.  it's merely a minor annoyance, but enough
of one at times that i thought i'd ask.

i'm still absolutely **loving** this serval... it's a very solid machine!

(running 8.04 with system76 drivers and all updates applied)

---

### Post by thomasaaron on 2008-07-24
We've had this one pop up before on a number of different computers (both System76 machines and otherwise). I believe it is a glitch Ubuntu's resume scripts somewhere. We've not been able to find anything in the logs either that point to a particular problem.

I believe you can turn the beeping off via System > Preferences > Power Management > General. Deselect the "Notify with sound in event of error" checkbox.

Also, you can deselect the checkbox in System > Preferences > Sound > System Beep.

---

### Post by majoridiot on 2008-07-24
> **thomasaaron said:**
> We've had this one pop up before on a number of different computers (both System76 machines and otherwise). I believe it is a glitch Ubuntu's resume scripts somewhere. We've not been able to find anything in the logs either that point to a particular problem.

I believe you can turn the beeping off via System > Preferences > Power Management > General. Deselect the "Notify with sound in event of error" checkbox.

Also, you can deselect the checkbox in System > Preferences > Sound > System Beep.

thanks for the quick reply, thomas!  i did a search before posting, but obviously was too narrow ;)

i'll play with your two suggestions and see if i can find a good solution.  i do use the system
beep for a couple things, so i don't want to totally disable it.  hopefully, the power management 
setting will fix it.

---

### Post by asmiller-ke6seh on 2008-07-26
I've been having this, too - precisely the same symptoms.

---


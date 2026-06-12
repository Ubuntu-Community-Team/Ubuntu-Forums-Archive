---
title: "Random Power Down"
date: 2010-08-04
forum: System76 Support
---

### Post by dysonsphere23 on 2010-08-04
Clean install of Ubuntu 10.04 on Pangolin Performance with i7 cpu.

The laptop will power down randomly while idle. Does not occur while I am working on it or with media running.

I checked Power Management and made sure that it is set to do nothing in response to idle time.

Does not occur when running Windows 7 (dual boot). 

Any thoughts on this issue.

---

### Post by joereith on 2010-08-04
monitor the system log at /var/log/syslog



About Monitoring:
In the terminal start: sudo tail -f /var/log/syslog >> /home/username/Desktop/log.doc

that should record the error into a document to read after you reboot if my memory serves me correctly.

---

### Post by isantop on 2010-08-04
Yep, monitor the log.

What exactly are the results. Is the system completely off, or has it simply rebooted, logged off, or locked the screen?

---

### Post by dysonsphere23 on 2010-08-04
> **isantop said:**
> Yep, monitor the log.

What exactly are the results. 


Haven't been able to reproduce the problem with the log monitoring process running.

> **isantop said:**
> Is the system completely off, or has it simply rebooted, logged off, or locked the screen?

The system completely turns off.

---

### Post by dysonsphere23 on 2010-08-06
ok, so I ran this in terminal:

sudo tail -f /var/log/syslog/home/username/Desktop/log.doc

and it did shut down

however there was no document on the desktop to read

(yes i did substitute my username)

is there something I am doing wrong or is there somewhere else that I can find the log?

---

### Post by thomasaaron on 2010-08-09
Here's what you need to do.

First, remove your battery and re-seat it, making sure the lock tabs are in the locked position. Does that fix the problem.

If not...

The next time it happens, please reboot your machine and *make note of the time when your system is all the way up*. Then, please go to System > Administration > System76 Driver > Support (tab) > Create (button). This will create an archive called logs.tar in your home directory. Please attach that archive to this thread.

I'll have a look at it and see what I can figure out.

---

### Post by dysonsphere23 on 2010-11-10
sorry the long delay.

still having the problem after checking battery and upgrade to 10.10.

here is the log.

up time was 9:44 10 november.

thanks

---

### Post by hansen55 on 2011-01-24
I had the same problem. It sounds like your computer is overheating.  Just to check, if you have it in a cabinet, take it out. Then take the  side panel off and use it for as long as you need. If it stays on longer  than it is now, it's an overheating issue. If that is the problem,  don't leave the cover off instead of addressing the issue. It's not good  for the computer. Instead, take the heat sink off of your processor,  clean it thoroughly, then since you'll be able to see your processor  clean all of the old paste off the top of it, then reapply some new  thermal paste to it. I used "Arctic Silver Thermal Paste" on mine. All  you need is the size of a grain of rice on your processor then smear it  evenly across all sides.
=============
[business opportunity](http://www.starscapes.com)
[orlando airport transportation](http://www.alwayssuperb.net)

---

### Post by dysonsphere23 on 2011-01-24
looks like it was over-heating.

sent the laptop back to system76, they changed the heat sink.

seems to work better now.

---


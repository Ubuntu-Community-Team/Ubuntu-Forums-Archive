---
title: "Whoa, that's a first ... PanP5 hard locked."
date: 2010-02-16
forum: System76 Support
---

### Post by samalex on 2010-02-16
Hi everyone,

In my years of using Linux a hard lock has only happened a hand full of times, and for the first time last night it happened on my PanP5.  I wasn't doing anything out of the ordinary, but the laptop froze and on the front left, the right two lights just binked.  

I had to pop out the battery and disconnect power from the wall to get it off, and powering it back on didn't show anything odd in /var/log/messages before the lock.  

This was the first time and it hasn't happened since, but if this occurs again are there any other logs I can checkout to see what might have happened? 

What's neat is I've had Windows systems do this hours after coming out of the box or right after a clean install, so having my PanP5 for over 6 months and this being the first time I've had to do a hard restart is pretty good in my opinion :)

Take care,

Sam

---

### Post by jdb on 2010-02-16
> **samalex said:**
> Hi everyone,

In my years of using Linux a hard lock has only happened a hand full of times, and for the first time last night it happened on my PanP5.  I wasn't doing anything out of the ordinary, but the laptop froze and on the front left, the right two lights just binked.  

I had to pop out the battery and disconnect power from the wall to get it off, and powering it back on didn't show anything odd in /var/log/messages before the lock.  

This was the first time and it hasn't happened since, but if this occurs again are there any other logs I can checkout to see what might have happened? 

What's neat is I've had Windows systems do this hours after coming out of the box or right after a clean install, so having my PanP5 for over 6 months and this being the first time I've had to do a hard restart is pretty good in my opinion :)

Take care,

Sam

On most computers if you hold the power button down 20 seconds or so they will power down.

jdb

---

### Post by thomasaaron on 2010-02-16
Yeah, the power button should do it. The blinking LEDs indicate you had a kernel panic. 

If you go to System > Administration > System76 Driver > Support > Create, you can pretty much all necessary logs in one swoop.

/var/log/syslog is a better indicator of what causes kernel panics than /var/log/messages is.

---

### Post by samalex on 2010-02-16
I held down the power button for about 10 seconds but didn't think to do it longer.  

As for logs, I've already rebooted a few times since then so if it happens again I'll check the syslog and the System76 support logs to see what happened.  Probably a one-time thing since it's never happened before, but I'll post back if it happens again.

Thanks --

Sam

---


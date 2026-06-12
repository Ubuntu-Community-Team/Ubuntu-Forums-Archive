---
title: "Pangolin panp4 beeping and shuting down on boot."
date: 2009-10-17
forum: System76 Support
---

### Post by Guille Damke on 2009-10-17
Hi guys,

I just was using my Pangolin panp4 for web browsing, and after around 5 minutes it just shutted down. Then, I turned it on again but now it stars beeping and flashing the Num Lock and Caps lights (at the same rate of the beeping) right after the first BIOS screen at a frequency of around 2 beeps every 3 seconds. It loads the OS (Ubuntu 9.04 64) and displays the login screen, but it turns off automaticaly (after around 30 seconds from turning on) and I cannot login for checking the system. It shows the whole amount of RAM in the first screen (4096 MB) and I tried to run a memtest but it turned off too, automaticaly after around 30 seconds. I also tried to log in with no XServer (ctrl+alt F1), but it turned off too. Finally, I took the battery off and turned it on, but I had the same problem.

Now, right after I wrote the first part of the post, I turned it on again and it worked for around five minutes (I could create the log.tar file and email it to me), but it just turned off with no notice. The temperature was in the normal range (below 65 celcius). Do you have any clue what might be causing this fail? I really need the laptop working!

Thanks,
Guille.

---

### Post by betrunkenaffe on 2009-10-17
> **Guille Damke said:**
> Hi guys,

I just was using my Pangolin panp4 for web browsing, and after around 5 minutes it just shutted down. Then, I turned it on again but now it stars beeping and flashing the Num Lock and Caps lights (at the same rate of the beeping) right after the first BIOS screen at a frequency of around 2 beeps every 3 seconds. It loads the OS (Ubuntu 9.04 64) and displays the login screen, but it turns off automaticaly (after around 30 seconds from turning on) and I cannot login for checking the system. It shows the whole amount of RAM in the first screen (4096 MB) and I tried to run a memtest but it turned off too, automaticaly after around 30 seconds. I also tried to log in with no XServer (ctrl+alt F1), but it turned off too. Finally, I took the battery off and turned it on, but I had the same problem.

Now, right after I wrote the first part of the post, I turned it on again and it worked for around five minutes (I could create the log.tar file and email it to me), but it just turned off with no notice. The temperature was in the normal range (below 65 celcius). Do you have any clue what might be causing this fail? I really need the laptop working!

Thanks,
Guille.

Processor fan failing?

---

### Post by thomasaaron on 2009-10-19
The most interesting thing in your logs was this line...
Clocksource tsc unstable (delta = -64359505 ns)
...before every restart.

But, since the shutdown occurs in memtest86 too (i.e. before booting into the OS), I'm leaning more towards hardware than any of the various in-the-OS bugs that can cause that message.

My two biggest suspects are memory, your ac adapter, and the cmos battery.

Please remove the ac and battery from your system and then remove the larger of the panels on the bottom. Remove and reseat your memory. 

If that doesn't fix it, can you get your hands on another ac adapter to test with? I know the green light is probably on, but that doesn't mean much. The jack on the PanP4 is pretty standard, so just about any ac adapter should work.

If it's not giving you a message on boot-up about clock settings being lost, though, I guess it's *probably* not the cmos battery.

---

### Post by Guille Damke on 2009-10-20
Hi guys,

I solved the problem just a few hours after I posted the problem. I suspected of a temperature-related issue, because the error appeared sooner if I had already tried to use the laptop. I opened the rear cover (following the instructions posted by Thomas Aaron when people have troubles with the fan) and I realized that it was stuck, but not too dirty though. I just cleaned it with some air and it could spin freely again. Now, the laptop is working as it used to do :D

Thanks for the support.
Guille.

---

### Post by betrunkenaffe on 2009-10-20
That's why I thought processor fan was failing. Too much heat and auto shutdown happens.

---

### Post by betrunkenaffe on 2010-01-01
> **Guille Damke said:**
> Hi guys,

I solved the problem just a few hours after I posted the problem. I suspected of a temperature-related issue, because the error appeared sooner if I had already tried to use the laptop. I opened the rear cover (following the instructions posted by Thomas Aaron when people have troubles with the fan) and I realized that it was stuck, but not too dirty though. I just cleaned it with some air and it could spin freely again. Now, the laptop is working as it used to do :D

Thanks for the support.
Guille.


Literally same thing just happened to me. Same deal, opened back, pulled fan, cleaned a little and found it was a little stuck. Put back together and all working again.

Thank you!

---


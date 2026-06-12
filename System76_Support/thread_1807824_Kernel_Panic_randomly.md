---
title: "Kernel Panic randomly?"
date: 2011-07-19
forum: System76 Support
---

### Post by turbotron on 2011-07-19
Hi all, 
Having a problem with my system76 pangolin performance laptop (the machine is less than a year old). For about a month now it's been crashing at random times. The system locks up completely, the caps lock lights start flashing, and I have to do a hard reset with the button. When the machine powers on again, nothing comes on the screen, and the speaker beeps 3 times - then i have to hard reset again to get the system to boot again normally.
From what I've read this indicates a kernel panic. I'm not sure where to look (which logs, etc) to figure out how or why this is happening. It doesn't seem to have any relationship to what applications or devices I'm running (as far as i can tell). Any ideas for how I can figure this out or where to investigate further? The random crashes are pretty much crippling my productivity :\

Any help you guys can offer would be greatly appreciated - thanks in advance!

---

### Post by Bleak888 on 2011-07-19
Not to hijack your thread, turbotron but this happened to me today as well. The exact same symptoms. lights in front flash, the beeps, having to reboot twice (I went to a boot screen the first time) My device is 6 months old. I won't worry about it unless it happens again but it might be helpful for them to know it might not be random. Good Luck!

---

### Post by turbotron on 2011-07-20
Came across this, which seems to be describing the same issue.

[https://bugs.launchpad.net/system76/+bug/417348](https://bugs.launchpad.net/system76/+bug/417348)

---

### Post by Plecebo on 2011-07-20
I have a panp7 that has been experiencing this issue for over a year now, and pretty much since day 1.

I've contacted system76 support and even sent the laptop back to them. 

They replaced the network card (due to another issue) and we thought that would fix the issue of the Kernel Panic, but it didn't. 

The whole laptop has been a frustration, when it works it is great, and when it doesn't it is very frustrating. Especially since it is my girlfriends laptop who is a newer linux user and feels like she should have purchased a Mac :(

I'd be very interested in hearing if anyone finds a resolution to this issue.

---

### Post by isantop on 2011-07-22
Barring a hardware issue, kernel panics are usually caused by corrupt software. how long can you usually go without having it reset?

---

### Post by Plecebo on 2011-07-25
I went digging through the boot log after one of the recent crash on boots and found a cryptic error pointing towards the ati graphics. 

I checked and despite having used the "Install Drivers" option in the system 76 tool the generic ATI graphics driver was used. 

I updated to the fglrx driver to see if the it would change the problem and it seems to have made things more stable. 

I had avoided installing the proprietary drivers since I thought when I sent the laptop back to system 76 they would have noticed that (or noticed it in the logs I sent to them) and installed it/had me install it.

Oh well, at least things are not crashing anymore, which is a step in the right direction. Now if I could only figure out the crazy long boot times.

---

### Post by turbotron on 2011-07-30
plecebo,
Can you give me some info on where you looked to find that error in the boot log and what it looked like? The next time my crash occurs, I'd like to check and see if I can find anything amiss, but I'm not sure what logs to look in and what to look for.

---

### Post by Plecebo on 2011-08-01
@ turbotron

I found my hint in the /var/log/boot log file. Many of the issues, and especially the kernel panics tended to happen at startup. 

I looked through the log knowing what time the panic happened for events around that time stamp and saw the last entry in the boot log to be related to the graphics system, and specifically a driver crash. 

That got me researching different drivers and I discovered the binary driver was recommended for the laptop, and also that it wasn't installed by the system76 driver restore feature. 

I checked and sure enough the binary driver was not installed, so a little apt magic later and it seemed more stable. 

The stability improvements have continued, I suspect the last bit of strange behavior has more to do with Unity then it does with the mis-configuration of software or failure of hardware. 

Look for gaps in your log files around the time of the crash. Start from where the logging stops from your last boot (before the crash) and ready backwards a few lines (probably not need more then 20 lines to tell if the issues were logged) then check the other files. Anything that looks suspicious focus your google lens on and see what you can find. 

Good luck !

---


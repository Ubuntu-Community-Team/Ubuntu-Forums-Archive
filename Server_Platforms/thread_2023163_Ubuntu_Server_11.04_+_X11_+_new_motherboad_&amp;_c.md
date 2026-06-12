---
title: "Ubuntu Server 11.04 + X11 + new motherboad &amp; cpu = problem"
date: 2012-07-12
forum: Server Platforms
---

### Post by Sorky on 2012-07-12
I have had X11 working on my Ubuntu Server for quite a while previously, however I had to update the motherboard & cpu and that are slightly newer and now I have an issue...

On the old system I ran "xinit" and on exit it dropped back to the command line perfectly!

Now that the system has been updated, "xinit" runs fine, but when I exit the display goes blank and the console does not show... About all I can do is to SSH in and reboot the server.

Only thing I see of note through SSH is "ps -A" before has "tty1 ... getty" and after exiting X has "tty1 ... login" and "tty1 ... bash". If I "sudo pkill login" I get back to "tty1 ... getty" but the screen is still blank.

As an experiment I tried to relaunch "xinit" from the blank screen [typing blind] and via SSH I saw "tty1 ... xinit", etc, so it seems that the console was active, but the display was somehow still incorrectly set. Unfortunately, even though I'd re-started xinit, the screen remained blank - display mode seems to have somehow stuck in limbo :-(

Would be great to hear from anyone with ideas [other than not running xinit] - Guessing something around the graphics mode that remains after X closes or the  console resolution

PS: New = **Gigabyte - GA-H77M-D3H **&**Intel - BX80637I73770**

---

### Post by Sorky on 2012-07-14
Bump...

Anyone understand enough about X11 to help?

---

### Post by CharlesA on 2012-07-14
Is the video card different between the two mobos?

As a sidenote: Why are you running X on a server?

---

### Post by Sorky on 2012-07-14
> **CharlesA said:**
> Is the video card different between the two mobos?

Video is provided by the CPU and handled by the motherboard - 2 years newer, so I expect the CPU graphics has changed and a different chipset on the motherboard

> **CharlesA said:**
> As a sidenote: Why are you running X on a server?

Yes - Ubuntu Server 11.04 - normally just console but occasionally I want to run X on it

---

### Post by CharlesA on 2012-07-14
Ok. If you don't have all that much stuff installed on it, I would suggest backing up your data and doing a clean install of 12.04. Support for 11.04 ends in October 2012.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by oldfred on 2012-07-14
I do not know servers, but you often need the newest distribution to support new hardware and sometimes it still takes a few months before it is fully supported.

[http://www.phoronix.com/scan.php?page=article&item=intel_ivybridge_redux&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_ivybridge_redux&num=1)

> While any modern release will do,  you generally want the latest compiler, kernel, and graphics packages for the  best performance. Ubuntu 12.04 LTS has been tested the most and it has shaped  up extremely well for this new Intel hardware."

---


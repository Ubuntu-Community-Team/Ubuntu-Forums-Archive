---
title: "Increasing involuntary fsck on boot"
date: 2009-09-13
forum: System76 Support
---

### Post by cmnorton on 2009-09-13
The bottom line of this post is should I be running an HD or other diagnostic on my Gazelle Ultra?

In the past two days, on my Gazelle Ultra has run fsck with increased frequency. One one of the boot-ups, part of the file system was repaired; on another boot I've gotten a message about date/time. 

I have found that plugging or unplugging the unit during boot results in the set date/time message, so I've avoided that for a long time. I did not plug or unplug the power during boot this time.

---

### Post by thomasaaron on 2009-09-14
> In the past two days, on my Gazelle Ultra has run fsck with increased frequency.

How often? 
Are you doing a lot of heavy file downloads with it?
Is it throwing any interesting messages when it runs fsck?

---

### Post by cmnorton on 2009-09-14
Only one message about fixing part of the root parition at the same time during post I got a check date-time messgage. Fixing this also seemed to create a deja-vu condition, which resulted in a redo of the fsck. I have no problem packing up and shipping the unit to you, if there are no diags I can run remotely.

---

### Post by thomasaaron on 2009-09-14
Can you try running fsck from a live cd?

fsck -y /dev/<whatever drive>

---

### Post by cmnorton on 2009-09-14
I'll try tonight when I get home and report back.

---

### Post by cmnorton on 2009-09-15
Ran fsck from Knoppix. Everything was clean. This appears to be an issue booting from battery.

Edit:
Booted Knoppix from being plugged in.

---

### Post by thomasaaron on 2009-09-16
Hi, Charles. Sorry, I'm still a bit confused. Is it trying to run fsck every time? If so, try running...

sudo rm /forcefsck

...and see if that fixes it. Also, please verify that you're running 9.04.

---

### Post by cmnorton on 2009-09-16
It was not running every time I was booting off battery, but the frequency was increasing. Also, one of the times included a burp over date/time. This is also with the larger battery. I should try running with the original battery that came with the unit, and I'll do that soon.

---

### Post by cmnorton on 2009-09-21
This problem has not re-occurred.

---


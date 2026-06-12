---
title: "My Thinkpad X1 Carbon won't suspend in 16.04"
date: 2016-03-01
forum: Ubuntu Development Version
---

### Post by cdysthe on 2016-03-01
Hi,

I'm running fully updated 16.04. My Thinkpad X1 Carbon does not suspend. When I hit 'Suspend' from the desktop or close the lid the screen turns off but it gets stuck there. The red suspend LED doesn't pulse, and when I open the laptop again the only way to get it to work is to hold the power button for several seconds. The screen then comes on. It's a balance act since if I hold the power button for too long I get a hard reboot. Anyone else seeing this, and is there anything I can do except for reporting a bug?

---

### Post by Doug S on 2016-03-01
Starting from the fresh boot, does your Computer suspend properly the first time and then not thereafter?
My question is an attempt to determine if your issue might be related to [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1504584").

---

### Post by cdysthe on 2016-03-01
> **Doug S said:**
> Starting from the fresh boot, does your Computer suspend properly the first time and then not thereafter?
My question is an attempt to determine if your issue might be related to [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1504584").

You are absolutely right! I got two normal suspends right after I booted. Now, a couple of hours later I'm not able to suspend. I get the black screen, steady suspend led on the laptop, and need to press the power button for a few seconds to get back to my desktop. I will tag on to that bug. Thanks!

---


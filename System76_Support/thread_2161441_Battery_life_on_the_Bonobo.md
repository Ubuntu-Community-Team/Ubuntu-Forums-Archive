---
title: "Battery life on the Bonobo"
date: 2013-07-10
forum: System76 Support
---

### Post by Murukesh on 2013-07-10
I was under the impression that Optimus allows us to switch between an integrated gfx card and a discrete one. I read somewhere that the Core i* processors have an "integrated" graphics card with them. If that's true, is it disabled on the bonx6? Can I enable it and use Optimus without tinkering with the hardware? The battery life so far is good (about 3 hours/200 minutes of watching videos while charging a Nexus 4, about 80 minutes of playing Assassin's Creed III at max graphic detail), but I'm looking at ways to improve things about the bonx6. So far I have got Arch Linux to boot to an E17 desktop in ~35s where Ubuntu takes near about a minute and Windows 8 about 50s. That's okay, still improvable, but I want to see how I can improve the battery life. The graphics card, drawing a minimum of 22W all the time, seems like an obvious target.

Also, the capacity of the battery when full has gone down from 89.2 Wh to 86.1 Wh, according to gnome-power-statistics. That's a loss of 3.1 Wh in a little over 3 months of usage. Is that normal? If not, what can I do about it?

---

### Post by isantop on 2013-07-10
All System76 computers do not have Optimus, and systems with discreet GPUs can't utilize the integrated GPUs at all.

---

### Post by Murukesh on 2013-07-10
Yes, but what is the nature of the block? How does System76 prevent utilization of the integrated card? Are you saying that the motherboard doesn't support it? No hack, software or hardware, can enable it? (I realize I might void warranty, set the laptop and puppies on fire, etc., etc., but I am curious about this.)

---

### Post by 3Miro on 2013-07-11
> **Murukesh said:**
> Yes, but what is the nature of the block? How does System76 prevent utilization of the integrated card? Are you saying that the motherboard doesn't support it? No hack, software or hardware, can enable it? (I realize I might void warranty, set the laptop and puppies on fire, etc., etc., but I am curious about this.)

Nvidia doesn't really support Optimu for Linux. There are hacks and some partial support, but it requires an effort to get it working.

I don't know if Optimu is disabled or simply non-extent on Bonobo, but using Optimus is probably not a good idea.

---

### Post by isantop on 2013-07-11
It cannot be enabled. The integrated GPU is disabled at the firmware level.

---


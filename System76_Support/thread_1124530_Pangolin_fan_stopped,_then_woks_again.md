---
title: "Pangolin fan stopped, then woks again"
date: 2009-04-13
forum: System76 Support
---

### Post by 3Miro on 2009-04-13
I had some unpleasant experience today:

I was at work, using my Pangolin when it suddenly shut off (no warning, like an unplugged desktop) (I was only browsing and listening to music)

I turned it back on and heard a very loud repeated beep (good I was using headphones), then ubuntu started to load, got to the load screen, I entered name and pass and started loading Gnome. Then it shut off again.

At this point I was thinking "heat". I started it again and listened for the fan. No fan and no air flow, just the beep. I couldn't get to gnome to check the temps and BIOS has no PC Health section. After about a minute in the BIOS is shut off again. Plugged/Unplugged cable/battery made no difference.

I went home and opened the back panel. Disconnected the fan (carefully of course) and placed the opened laptop on a fan-mat. It booted normally and I started watching the temp. With the mat on, it was OK (CPU/GPU 20/50), then I decided to push it a bit. I started a video and played with the cube while watching the temps, those went to 45-50/65, then it shut off again (my theory, it tried to turn on the fan, did not find it, paniced and correctly decides to shut off)

The fan had just a few dusty lines, I cleaned those. There was little dust on the north-bridge heat-sink (I am assuming it is the NVIDIA NB, the biggest heat sink anyway)(I've had the laptop less than 2 months). Then connected back the fan and the thing ran. Fan is now working and the temp stays below 40/60.

There was too little dust to make a difference and the fan looked well connected. There is no issue right now, just want to give a preliminary report. If it starts to happen regularly, I will ask for the problem to be repaired.

One extra note: I don't think it is sys76 fault, but there are very few vents on the bottom. Also the fan is small and it could definitely be made to provide more air flow. Normal operation temps are fine, but CPU intensive work tends to push (50+/65+). I have not tried wine games on it (and am afraid to). My issue is that I cannot benefit from an fan-mat, I am always stuck with the small internal fan.

Precise stats: NV 9300M, 2.4Ghz CPU, 4GB ram, the rest was standard.

---

### Post by thomasaaron on 2009-04-13
Two questions:

1. Have you installed 32-bit Ubuntu?
2. Is there a suspend-resume cycle involved?

---

### Post by 3Miro on 2009-04-13
> **thomasaaron said:**
> Two questions:

1. Have you installed 32-bit Ubuntu?
2. Is there a suspend-resume cycle involved?

1. No I am using the 64-bit that came on it. I have 4GB of RAM.

2. I rarely turn the ting off, I use suspend/hibernate. When it happened, the laptop had gone trough several suspend/resume - hibernate/resume sessions. However, I had been working on it for several minutes before it shut off (i.e. suspend - resume - work for a few minutes - shut off). By considering how fast the comp was shutting off, I would assume that the fan stopped during normal operation, but I might be wrong. Also, after shut-off the computer was going trough complete boot up and no resume.

One other note, there was CD activity involved. I had been using the cd-rom with an old video game, but upon resume I only ejected the CD. I rarely use the cd-rom, but have no trouble before.

---

### Post by thomasaaron on 2009-04-13
None of the temperatures you mentioned are anywhere near hot enough to shut the machine down.

There is a possibility that multiple suspend-hibernate cycles caused a problem. Such a bug existed in 32-bit, but I've not heard of it yet in 64-bit.

Is it possible that your ac adapter wasn't connected well (check it at the jack and at the brick) and your battery went dead?

If it happens again, though, let me know. We can get a new fan to you if necessary.

---

### Post by 3Miro on 2009-04-13
Temps were fine, which was a relief. However, if the system doesn't recognize the fan, it may shut off as well. I know that if the CPU fan on a desktop stops, the system would shut off without waiting to overheat.

I will make sure to keep an eye on the AC adapter and battery if it happens again, however, I don't think this was the issue. The battery was well in the socket (I disconnected and connected it back) and it was showing as charged afterwards.

In either case, it is no reason to loose our sleep over it. I will blame it on a "evil gremlin loosening the fan connector". I just hope it doesn't happen again.

---

### Post by betrunkenaffe on 2009-04-13
I remove my battery from the laptop when I'm using it plugged in. Saves any problems due to battery from happening during regular use (just when I rely on battery :P)

---

### Post by jdb on 2009-04-14
> **betrunkenaffe said:**
> I remove my battery from the laptop when I'm using it plugged in. Saves any problems due to battery from happening during regular use (just when I rely on battery :P)

I kind of like having the battery there, it's a UPS (Uninterruptible Power Supply) when there's a glitch on the AC line.

LION batteries do great when they are plugged in all the time, they have a built in processor that controls the charging.

jdb

---

### Post by Dok on 2009-04-15
I just received my Pangolin Performance today and experienced the same problem. The system ran for about 5min and shut down. On reboot I got the beep beep beep. Shut it down and checked out the laptop, sure seemed hot. On removing the back panel I found the fan power connector wasn't fully seated and the fan wasn't spinning at all. I plugged the fan power connector back in and it is working fine now. Maybe whoever is adding the RAM isn't double checking the fan power lead when they put the back cover on? 
Brad

---

### Post by thomasaaron on 2009-04-15
Thanks. I'll report that to the manufacturing manager.

---

### Post by 3Miro on 2009-04-15
Odd thing is that mine worked fine for a month before I had a problem.

Is it possible that it just gets loose over time (or is it the evil gremlin).

---


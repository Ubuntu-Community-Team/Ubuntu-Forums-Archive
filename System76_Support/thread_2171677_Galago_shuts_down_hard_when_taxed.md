---
title: "Galago shuts down hard when taxed"
date: 2013-09-01
forum: System76 Support
---

### Post by Neil_Toronto on 2013-09-01
Disclaimer, though it shouldn't matter: I've installed [tlp]("https://wiki.archlinux.org/index.php/TLP") to manage laptop power.

I've had a Galago for three weeks now, and it's shut down hard four times while playing Kerbal Space Program in a window. I thought it might be overheating, so I installed Psensor and intend to watch the graphs while I play to catch it in the act.

In the meantime, I have a few questions.

1. How can I find out why it shuts down? I tried looking through /var/log/syslog this last time, but it shows nothing weird happening, just my reboot afterward. Similarly, "last -x" shows only the reboot.

2. How hot should this thing allow itself to get? Core 0 and Core 1 can get up to 80C while playing KSP, Core 2 and Core 3 get to 75C, and I've seen "Physical id 0" (the GPU?) get to 83C. (It's 35C to 50C when browsing and other light usage.)

3. Shouldn't the hardware be scaling back if it's overheating?

I had a similar problem with my old Gazelle: a hard shut down when working hard; in that case, using all 8 cores in a long parallel compile. I couldn't compile with more than 6. But that laptop didn't have any trouble with KSP.

---

### Post by isantop on 2013-09-03
This sounds like a failure in the cooling system. We'll need to have it serviced. The repair will be covered under your warranty, so it will be a free repair. 

Go ahead and log in to your account on our website, then click on "Open Support Case" under your Galago, and we'll get it all set up.

---


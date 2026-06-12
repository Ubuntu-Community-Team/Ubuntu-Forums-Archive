---
title: "How To Diagnose System Crash?"
date: 2011-04-17
forum: Server Platforms
---

### Post by ThePol1 on 2011-04-17
I am running Ubuntu 10.10 (amd64) on an Intel Atom 525 motherboard. I have a 5-bay SATA enclosure connected to my system through a Syba SD-SATA2-2E2I PCI card (uses the SIL3124 chipset).

Under small to moderate load (transfer speed: ~25 Mb/sec), this setup works perfectly.

Under heavy load (transfer speed: ~40 - 70 Mb/sec), the system crashes. By crash I mean I loose SSH connectivity, I can't ping the system, etc. The only solution is a hard reset.

Initially, I thought this was a SAMBA problem so I logged into the system and tried doing a copy directly from the SATA enclosure to the system disk (connected directly to the motherboard). After 100 GB copied (at ~75 Mb/sec), the system crashed.

**My question:** I am fairly new to Linux and Ubuntu. How would I go about diagnosing this problem? What logs or other resources would you suggest?

---

### Post by usatonycuba on 2011-04-18
[http://askubuntu.com/questions/19538/how-do-you-diagnose-constant-crashing-issues]("http://askubuntu.com/questions/19538/how-do-you-diagnose-constant-crashing-issues")

It may help ?

---

### Post by ThePol1 on 2011-04-18
> **usatonycuba said:**
> [http://askubuntu.com/questions/19538/how-do-you-diagnose-constant-crashing-issues](http://askubuntu.com/questions/19538/how-do-you-diagnose-constant-crashing-issues)
 
It may help ?
 
That link provides some good resources. Thank you! I'm going swap out the hard drive later this week and see if that is causing the problems. The next step will be to follow the debug steps listed in the link.

---

### Post by usatonycuba on 2011-04-18
> **ThePol1 said:**
> That link provides some good resources. Thank you! I'm going swap out the hard drive later this week and see if that is causing the problems. The next step will be to follow the debug steps listed in the link.
No problem... U R Welcome... That link is from a trusted source , give a try ...GL

---

### Post by hymerman on 2011-09-07
Did you ever get to the bottom of this? I'm having similar problems.

---

### Post by ThePol1 on 2011-09-07
> **hymerman said:**
> Did you ever get to the bottom of this? I'm having similar problems.

Yes. This ended up being an Intel driver problem. Intel mentions a Linux issue with the older BIOS somewhere... Anyhow, I flashed the motherboard BIOS with the newest drivers and everything has been working great with no crashes.

---


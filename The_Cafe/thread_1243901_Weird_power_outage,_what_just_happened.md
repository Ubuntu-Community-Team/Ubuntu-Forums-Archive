---
title: "Weird power outage, what just happened?"
date: 2009-08-18
forum: The Cafe
---

### Post by Yes on 2009-08-18
My house suddenly lost power for just a second, and then it came back on (there's a thunderstorm passing through, I assume that's why).  When that happened my computer and monitor of course turned off, but when the power came back on a second later everything was still running fine - all the windows I had open before were still up, and everything seemed fine.

The only thing that was odd was MPD was running, but mpc and ncmpcpp couldn't connect to whatever port it normally ran on.  What happened when the power went out to cause this?

---

### Post by schauerlich on 2009-08-18
RAM doesn't clear instantly when it loses power. It may retain its contents for a second or two before clearing. How long was the power out? Was it just a flicker?

---

### Post by tom66 on 2009-08-18
Most PSUs are rated for around 10-30 ms drop-out: they can keep a computer stable for that long if AC is lost. Your monitor probably switched off because it is less rated (5 ms probably). You could also get lucky if you have a good motherboard as the caps around the CPU and RAM could keep them running for longer (The HDD & CD-ROM isn't really a problem and those can keep running on momentum and aren't required to keep a computer stable). We had an old DVR/Freeview box which would run for two whole seconds without AC: Not sure if this was a designer decision (so brief power outages don't cancel recordings) or just a good PSU... but it was interesting.

These brief outages in the UK aren't really outages, but they tend to be 'undervolts'. The lights dim briefly occasionally, especially on stormy days. The reason, as I was told, at a power station, is because when a lightning bolt strikes a line, the power is switched to reduce the output to compensate. It also occurs in ground faults, because a ground fault puts a lot of load on the line it causes a brief reduction in voltage.

Also, some motherboards power the RAM from the clock battery if power is lost. On resume the computer behaves as if nothing happened.

---

### Post by Yes on 2009-08-18
It was only a second.  I'm more wondering why MPD got screwed up.  I guess when the RAM started clearing it got messed up?

---

### Post by tom66 on 2009-08-18
Partially corrupted RAM would cause a kernel panic, instantly, especially on a modern OS with tons of pointers and simultaneously operating processes, unless it hit an area not in use. But corruption is usually random and will hit important areas.

RAM takes about 10-20 seconds before it's useless at storing data without power (the data is still readable but it does get significantly corrupted). But you have to remember that you still have the CPU's state (registers, execution), along with the PCI and AGP card states (their internal RAM and processors need to be considred as well) attached which would have been lost without power. Internal cards like network cards could reset, but a graphics card could not without a complete reboot.

---

### Post by doas777 on 2009-08-18
The PSU makes all the difference. your circuit was likely reclosed inside a few hundred ms, so the caps in the PSU and the mobo were able to keep it going. seems like if your only drawing 300w off your 750w psu, then your caps should be full up most of the time.

I've had boxes that are both more and less suceptible to this effect. with 4 PCs running 2 will get rebooted.

---

### Post by tom66 on 2009-08-18
Capacitors are never full (it's technically impossible - it's also impossible for them to be completely empty). But they can be at a low capacity and still power a PC if the switch-mode PSU is designed well.

---


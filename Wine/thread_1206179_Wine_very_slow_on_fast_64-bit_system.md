---
title: "Wine very slow on fast 64-bit system"
date: 2009-07-06
forum: Wine
---

### Post by rogblake on 2009-07-06
Quad core AMD Phenom-II CPU, 8GB DDR3 memory, solid-state system drive, this system runs very fast -- except when running wine. In fact, wine fires up much faster on my 6-year-old Pentium-4 laptop. (In comparison, notepad takes over 30 seconds to come up on the "fast" system, under 10 seconds on the old P4.)

Both systems are running Ubuntu 9.04 and both have Nvidia graphics cards running the Nvidia binary driver; same version of wine as well. However, the new system is running Ubuntu 64-bit edition.

Any ideas what might be causing the slowdown?

---

### Post by christoff2008 on 2009-07-09
try updating wine

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by 3Miro on 2009-07-09
What are the video cards and what game/program are you working with.

My wine runs perfect under 64-bit, the issues must be with the settings/hardware.

---

### Post by rogblake on 2009-07-18
> **3Miro said:**
> What are the video cards and what game/program are you working with.

My wine runs perfect under 64-bit, the issues must be with the settings/hardware.

The program is notepad as bundled with wine 1.0.1, run as a test. Video card is an Nvidia 7200 running the binary driver downloaded from the Nvidia web site.

I tried updating from 1.0.1 to development release 1.1.25. This fixed the speed problem, but unfortunately soon afterwards wine stopped working properly. At first it would abend and the debugger would finger the video driver. I uninstalled/reinstalled the Nvidia driver which permitted wine to run, but its drives still cannot be accessed and the drives cannot be configured through winecfg. (The error is "failed to open mount manager.")

I then uninstalled the binary Nvidia driver, purged out wine and my .wine directory, and re-installed wine with the system running on the open source nv driver. Still the same problem, "failed to open mount manager" diagnostic. The only other major things that have been installed on this system are VirtualBox and Samba server (the latter built from source).

This is with wine 1.1.25, have not yet had time yet to try out the 1.1.26 version that was released yesterday.

---

### Post by rogblake on 2009-07-19
I installed wine 1.1.26 and that appears to have fixed the problems. Installed it first with X running the open-source nv driver and that worked fine. Then I re-installed the Nvidia binary driver and wine continues to function properly. (At least for the moment!)

---

### Post by NightMKoder on 2009-07-19
If you're using proprietary nvidia drivers, you need to install 32-bit versions as well (wine is a 32-bit app).

---

### Post by rogblake on 2009-07-21
When you install the 64-bit Nvidia driver it offers to also install a 32-bit compatibility library. Wine 1.1.26 seems to be getting along well with it.

---


---
title: "System Monitor"
date: 2009-09-18
forum: Security
---

### Post by sopadeajo on 2009-09-18
System Monitor tells me the 2 CPU are at 60 % work and Processes (in System Monitor) tells me Firefox is using 20 % and gnome system monitor 15% and nothing more in Processes.
Who is using the rest?

---

### Post by lovinglinux on 2009-09-18
Probably Remote Desktop. It loves to eat CPU without showing up on the monitor.

Go to "System >> Preferences >> Startup Applications" and disable the Remote Desktop. Then reboot.

---

### Post by sopadeajo on 2009-09-18
> **lovinglinux said:**
> Probably Remote Desktop. It loves to eat CPU without showing up on the monitor.

Go to "System >> Preferences >> Startup Applications" and disable the Remote Desktop. Then reboot.

Nothing changes : a 25 % CPU is used by one or several unknown processes

---

### Post by lovinglinux on 2009-09-18
> **sopadeajo said:**
> Nothing changes : a 25 % CPU is used by one or several unknown processes

Run the **top** command from terminal.

---

### Post by sopadeajo on 2009-09-18
> **lovinglinux said:**
> Run the **top** command from terminal.

I had forgotten to restart.Now the CPU usages  is 40 % and gnome+firefox=25 %

top command in Terminal shows me Xorg at root with a 35 % (i do not know what is Xorg)

---

### Post by lovinglinux on 2009-09-18
> **sopadeajo said:**
> I had forgotten to restart.Now the CPU usages  is 40 % and gnome+firefox=25 %

top command in Terminal shows me Xorg at root with a 35 % (i do not know what is Xorg)

[http://en.wikipedia.org/wiki/Xorg](http://en.wikipedia.org/wiki/Xorg)
[http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)

If your computer is idle and you get 35% usage from Xorg, then you might have a graphics card driver issue. Have you installed the latest proprietary drivers? Do you have Intel graphics card?

---

### Post by sopadeajo on 2009-09-18
> **lovinglinux said:**
> [http://en.wikipedia.org/wiki/Xorg](http://en.wikipedia.org/wiki/Xorg)
[http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)

If your computer is idle and you get 35% usage from Xorg, then you might have a graphics card driver issue. Have you installed the latest proprietary drivers? Do you have Intel graphics card?

I have not installed any driver in Windows or in Linux .I might have an Intel graphics card but  i do not know in fact.

---

### Post by lovinglinux on 2009-09-19
> **sopadeajo said:**
> I have not installed any driver in Windows or in Linux .I might have an Intel graphics card but  i do not know in fact.


Go to "System >> Administration >> Hardware Drivers" and check if there is any available.

---

### Post by sopadeajo on 2009-09-19
> **lovinglinux said:**
> Go to "System >> Administration >> Hardware Drivers" and check if there is any available.

No proprietary drivers are in use on this system

---

### Post by lovinglinux on 2009-09-19
> **sopadeajo said:**
> No proprietary drivers are in use on this system

Are they available?

Check this tutorial [Jaunty Intel Graphics Performance Guide](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by sopadeajo on 2009-09-19
> **lovinglinux said:**
> Are they available?

Check this tutorial [Jaunty Intel Graphics Performance Guide]("http://ubuntuforums.org/showthread.php?t=1130582")

What should be or not available? If you are talking of drivers i have never installed drivers on this computer.

---

### Post by lovinglinux on 2009-09-19
> **sopadeajo said:**
> What should be or not available? If you are talking of drivers i have never installed drivers on this computer.

When you see the message that "No proprietary drivers are in use on this system" you should also see some options available to install. See attached screenshot.

---

### Post by sopadeajo on 2009-09-19
> **lovinglinux said:**
> When you see the message that "No proprietary drivers are in use on this system" you should also see some options available to install. See attached screenshot.

I just get this:  No proprietary drivers are in use on this system

---


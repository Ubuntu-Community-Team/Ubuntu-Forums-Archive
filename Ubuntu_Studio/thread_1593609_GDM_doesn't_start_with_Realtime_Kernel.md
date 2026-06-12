---
title: "GDM doesn't start with Realtime Kernel"
date: 2010-10-11
forum: Ubuntu Studio
---

### Post by halfpower on 2010-10-11
I installed the realtime kernel and headers on my Xubuntu system, which has both ALC850 and Emu-1212m.  I booted to it, but there were problems probing the hardware.  The also never got to the GDM login screen.  I only had a command line prompt.  Am I doing something wrong?  I'm trying to reduce the CPU load with Rosegarden.

---

### Post by halfpower on 2010-10-11
Disabled cool 'n quiet.  Rosegarden doesn't pop and click and CPU does not change when synths are added.  Problem is semi-fixed.

---

### Post by trulan on 2010-10-11
Which Ubuntu distro are you using?  And which RT kernel?  Also, what kind of video card do you have?

---

### Post by halfpower on 2011-07-12
I'm using a real time kernel I installed with apt-get.  It didn't dawn on me that there is more than one.  I'm using Ubuntu 10.04.2 LTS(Xubuntu), and I'm using a GeForce4 MX 4000 dual head card with only one monitor.  At the moment when I try to launch GDM from the command line, I get error messages about the monitor either not being configurable or not having a configuration.

---


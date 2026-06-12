---
title: "UPS connection"
date: 2008-12-04
forum: Server Platforms
---

### Post by any.linux12 on 2008-12-04
Hi!

Does anybody knows a good application to manage one UPS on Ubuntu 8.04 Server with no GUI??

---

### Post by aurelieng on 2008-12-04
[http://www.networkupstools.org/compat/stable.html](http://www.networkupstools.org/compat/stable.html) ?

---

### Post by any.linux12 on 2008-12-04
I said without GUI

---

### Post by CrucifiedEgo on 2008-12-04
In my experience (with a couple of different USB UPS devices) ubuntu sees is at a battery, so information about it is located in /proc/acpi/battery/BAT0  What exactly are you wanting to manage?  UPS devices are pretty much ON/OFF affairs.

---

### Post by any.linux12 on 2008-12-05
The thing that I want to do is to connect an UPS to Ubuntu 8.04 server without Graphical Interface. Then program the system to shutdown the server when the UPS runs with 30% of power.

This is the beggining couse when this runs ok I have something more...but later.

Any idea?
Thanks

---

### Post by aurelieng on 2008-12-29
No GUI with networkupstool... just a config file and a daemon doing exactly what you want to do, just check the links :)

---

### Post by cariboo on 2008-12-29
It depends on your ups, I have a Belkin and an APC. I have not been able to setup the belkin in either Windows or Linux. The APC uses apcupsd available [here]("http://www.apcupsd.org/"), you can control the ups from the command line and there is a webmin plugin for it.

Jim

---


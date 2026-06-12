---
title: "[SOLVED] Computer speed policy"
date: 2008-10-31
forum: System76 Support
---

### Post by Vadi on 2008-10-31
How can I make the computer speed policy appear in power management preferences? I've reinstalled fresh (to get encrypted hd), and don't see the option now.

---

### Post by thomasaaron on 2008-10-31
In Hardy, you had to go open gconf-editor and go to Apps > gnome-power-manager > ui to turn it on.

It looks like that option is not available in Intrepid. I don't know if it is an omission or by design. At any rate, you might want to file a bug against Ubuntu on it.

In the meantime, you can set your cpu preferences by left-clicking the cpu scaling applet.

---

### Post by Vadi on 2008-11-01
Okay, I will. But unfortunately I don't see the option in the applet either (see screenshot)

---

### Post by Vadi on 2008-11-01
> Thanks, but upstream have removed all of the cpufreq code in gnome-
power-manager for Intrepid. There is an explanation of the reason for
doing this from an upstream developer somewhere, but I can't find it at
the moment.

Well... that is dissapointing.

---

### Post by hvacr on 2008-11-01
[http://www.acquiringsatellites.com/wp/2007/11/30/take-control-of-cpu-frequency-scaling-in-ubuntu](http://www.acquiringsatellites.com/wp/2007/11/30/take-control-of-cpu-frequency-scaling-in-ubuntu)

---

### Post by Vadi on 2008-11-02
That didn't help, unfortunately. Tried with root on and off.

---

### Post by hvacr on 2008-11-02
> **Vadi said:**
> That didn't help, unfortunately. Tried with root on and off.

Did you left click the applet?

---

### Post by Vadi on 2008-11-02
Ohh. Thanks

---

### Post by mr_raider on 2008-11-02
Since it disappeared from gconf-editor, any way to toggle ignore niced processes?

---


---
title: "System76 Driver Won't Load on Lemur UltraThin 2 Running Oneiric"
date: 2011-10-19
forum: System76 Support
---

### Post by stillnotcool on 2011-10-19
I just upgraded to Oneiric on my Lemur UltraThin (2), and, as always, performed a clean installation.  I downloaded the System76 driver, double-clicked the package, allowed the Software Center to do its thing, and then tried to activate the driver so I could "restore" my system.  When I attempt to load the driver application, it flashes on screen for an extremely brief moment, then immediately closes.

Has anyone else experienced this issue?  More importantly: Has anyone found a solution?

---

### Post by Tart on 2011-10-19
Hello, 

I have same problem. I posted it here with little bit more details.

[http://ubuntuforums.org/showpost.php?p=11345444&postcount=16]("http://ubuntuforums.org/showpost.php?p=11345444&postcount=16")

---

### Post by isantop on 2011-10-19
This appears to be an issue with the driver. There aren't any drivers required for the LemU2 in 11.10, so you should be fine for now. I'll forward the issue on to the Driver engineering team to get this fixed.

---

### Post by isantop on 2011-10-20
If you have the driver installed, we've just released a new version (2.7.0) that resolves this issue. You should be able to update your system from the update manager to install it, after which it should run just fine.

---

### Post by stillnotcool on 2011-10-20
Fantastic!  Works like a charm.  My thanks to System76 support which is, as always, outstanding.

---

### Post by Tart on 2011-10-21
Hey Isantop,

Since you've mentioned that driver is not needed, and as far as I can tell,everything works fine. What will driver do? Do I need to run it?

Thanks

---

### Post by stillnotcool on 2011-10-22
> **Tart said:**
> Since you've mentioned that driver is not needed, and as far as I can tell,everything works fine. What will driver do? Do I need to run it?

I suspect isantop meant that the driver wasn't needed to restore any specific functionality (hence easing my frustration at not being able to run it after a fresh installation).  However, but running it anyway, you ensure that your software sources are modified to fetch updates from System76.

---


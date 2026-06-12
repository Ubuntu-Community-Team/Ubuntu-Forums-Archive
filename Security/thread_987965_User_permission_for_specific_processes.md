---
title: "User permission for specific processes"
date: 2008-11-20
forum: Security
---

### Post by leo_unbut on 2008-11-20
I have in my Panel the CPU-frequency-applet. I have configured to change the frequency On Demand for AC, and PowerSave for Battery-Modus.

Any time I turn of the AC, the system request the PWD to have access to change the settings. Which is somehow OK. But sometimes this really sucks, especially when I go to Hibernate in AC, turn during the Hibernate-process the AC off and the question about the PWD pops up and blocks the Hibernate-process.

Is there a simple way to give the CPU-frequency-applet the permissions to change the frequency-policy by itself without asking for system-permissions (=PWD-request)?

---

### Post by The Cog on 2008-11-20
I think the proper way to do this might be to create a new group where you can add in the users who are allowed to change the frequency, perhaps called "changefreq". Then change the group for the executable that gets called. On Hardy this is probably /usr/bin/cpufreq-selector but I think it's changed in Intrepid. Something like this perhaps:
> sudo groupadd changefreq
sudo chgrp changefreq /usr/bin/cpufreq-selector
sudo adduser username changefreq

---


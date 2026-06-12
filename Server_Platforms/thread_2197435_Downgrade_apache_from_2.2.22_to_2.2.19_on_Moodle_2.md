---
title: "Downgrade apache from 2.2.22 to 2.2.19 on Moodle 2.5 in the distro Ubuntu 12.04"
date: 2014-01-03
forum: Server Platforms
---

### Post by camila.s8t on 2014-01-03
Hi People,
I need help!

I'm doing my graduation dissertation and I making a scenario business continuity using DRBD mirroring solution to provide continuity to Moodle.
I am creating an environment of business continuity and I need to attack a vulnerable environment and return the operation to the secondary environment in order to demonstrate that the business continuity plan will be effective in a time of disaster secondary environment.

Apache 2.2.19 has a vulnerability and exploit that I can use to attack the environment, so I intend to carry out the attack and even after using the most updated apache.

I can downgrade from apache 2.2.22 to 2.2.19, the apache worked successfully but the moodle environment did not work. How Can a make the moodle environment work with the apache downgrade ?

Thanks!

---

### Post by lykwydchykyn on 2014-01-04
Tell us a bit more about how it didn't work, how you went about installing things and downgrading them.  Were you working strictly with packages from the repo, installing from source, or something else?  Did you install Moodle from the repositories or from source?

---

### Post by camila.s8t on 2014-01-15
The main page Moodle didin't load. 
I installed Moodle from source.

Thanks

---

### Post by lykwydchykyn on 2014-01-15
If the page doesn't load, you should check /var/log/apache2/error.log for some information on why.

---

### Post by cariboo on 2014-01-15
Moved to Server Platforms, as you will more than likely get more help here.

---


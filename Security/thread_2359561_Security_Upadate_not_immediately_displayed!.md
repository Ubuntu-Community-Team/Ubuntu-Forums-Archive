---
title: "Security Upadate not immediately displayed!"
date: 2017-04-25
forum: Security
---

### Post by xipho2 on 2017-04-25
In "Updates": "Display immediately" set. I assumed, after starting the  OS, they would be displayed-no! Starting the updater-they are displayed.  What does that mean?
People are asking me frequently, if updates could be installed automatically, without clicks or further ado. Solution?
Thanks!

---

### Post by ian-weisser on 2017-04-25
Your system normally checks for updates once each day.
In 16.04, the check runs at a random time each day. If your system is suspended/off during that time, the check will run several minutes after the system becomes available again.

Yes, updates can be installed automatically if you wish. The setting is in /etc/apt/apt.conf.d/50unattended-upgrades

---

### Post by xipho2 on 2017-04-26
Do you assume, I simply lean back, till something is displayed? In Win, after starting the machine, I check for updates at first. 
But I do not know, if it is necessary in Ubuntu. 
What, exactly, I have to do here:  /etc/apt/apt.conf.d/50unattended-upgrade? What might be the disadvantages doing so?

---

### Post by deadflowr on 2017-04-26
> What, exactly, I have to do here: /etc/apt/apt.conf.d/50unattended-upgrade?
Nothing if you want.
The default setup should be to install security updates.
at most you can uncomment the lines for the other updates (such as the -updates or backports or -proposed, I do not recmmoend enabling any of these, but that's up to you, really)
Beyond that every setting in the page has an explanation of what it is suppose to do. comment or uncomment which settings you want and do not want, again all up to you.
>  What might be the disadvantages doing so?
Updates running while on the system might cause problems for you if you try installing something at they same time.
There's also the blind faith involved, since it won't simply show you the updated packages beforehand.
The upgrader simply sees updated packages and installs them. It leaves you no real chance to stop or pause it.
>  In Win, after starting the machine, I check for updates at first. 
And no need to change a good behavior.
If this system of checking upon startup has worked well for you so far, keep doing it.
You can do both, check manually and have auto-updates enabled.
No need to rely on just one.

---


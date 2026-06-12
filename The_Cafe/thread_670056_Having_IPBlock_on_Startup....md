---
title: "Having IPBlock on Startup..."
date: 2008-01-17
forum: The Cafe
---

### Post by SZF2001 on 2008-01-17
So basically, I installed IPBlock and am happy with it. I added it to my start up programs (System -> Preferences -> Sessions), and here is the command in doing so:

```
gksu -u root "/usr/sbin/ipblock -g"
```

Every time I boot up Ubuntu for the first time, or log out and log back in, I end up having to put the root password in. Which I don't mind.

But....

Will this root password stay throughout an entire session? Lets say I leave my computer on for a week without turning it off and having IPBlock going. Will it still have the root privileges it needs or will it be locked out and I won't even know it?

---

### Post by rowanparker on 2008-01-17
Why don't you use /etc/init.d instead?
This will make things start at boot as root without you having to do anything.

But in answer to your question, no, it expires after a certain amount of time (forgotten what).

---

### Post by SZF2001 on 2008-01-17
How would I go about using /etc/init.d? just sudo gedit /etc/init.d?

Seems like the program has locked out... Argh.

---

### Post by FuturePilot on 2008-01-17
I'm not sure but since IPBlock is just a way to interact with IPtables, don't the settings stay in effect once they are set? Meaning that you don't need to keep it running to be blocking IPs?

---

### Post by uljanow on 2008-01-17
The *latest* version has an AUTOSTART option, which can be set in the GUI. 

> Will this root password stay throughout an entire session?
Yes.

---

### Post by SZF2001 on 2008-01-17
> **uljanow said:**
> The *latest* version has an AUTOSTART option, which can be set in the GUI. 


Yes.

I thought I had the latest version... Guess I'll go look stuff up.

---

### Post by areteichi on 2008-01-17
The latest version only "autostarts" (enables) the filter when ipblock is executed. In other words, this option does not make ipblock automatically run upon OS boot.

The latest version that I'm referring to is 0.18.

---

### Post by uljanow on 2008-01-17
> **byagietera said:**
> The latest version only "autostarts" (enables) the filter when ipblock is executed. In other words, this option does not make ipblock automatically run upon OS boot.

No. There is an init script **/etc/init.d/ipblock** which starts IPblock if autostart is set. The GUI however can detect if IPblock has already been started and will show the log and status.

Try a "sudo ipblock -l" after boot.

---


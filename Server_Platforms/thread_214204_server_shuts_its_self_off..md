---
title: "server shuts its self off."
date: 2006-07-12
forum: Server Platforms
---

### Post by ExMachina on 2006-07-12
Well no idea why but it seem my server had been shutting itsself off recently. Ill wak up to ssh into it and edit html and notice not connection wlak over and see it off. Only way to get it back on it to physially reset by takign teh PS plug form mobo repacing and hitting start..

What is causing this?
It it a safe measure?

its a crappy 300-400mhz celeron , 265ram, 20gig hdd.

---

### Post by simonn on 2006-07-12
Turn off **ALL** the power saving stuff and see if that makes a difference.

---

### Post by ExMachina on 2006-07-12
were are those?
You mean in the config ? or bios?

---

### Post by MJN on 2006-07-12
Have a look in /var/log/syslog around for events prior to the shutdown - any clues? (post here if you're not sure). An intended shutdown would always produce some log output, whereas a sudden hardware/power failure is unlikely to.

Mathew

---


---
title: "System is running in low graphics mode error after 12.04 update"
date: 2012-06-14
forum: System76 Support
---

### Post by Rich_S on 2012-06-14
I have a Gazelle that I bought about 10 months ago.  Upgraded to 12.04 about a month ago.  Ever since the update I've intermittently (maybe 1 out of 3 boots) been getting the "system is running in low graphics mode" dialog on startup.

Googling shows this to be a pretty widespread problem for those running the nVidia chipset.

I've done the:

sudo apt-get purge fglrx
sudo apt-get install fglrx

thing a few times.  It seems to work sometimes, but then again, just rebooting usually works after 2 or 3 tries so who know.

Is there a definitive answer to the cause of this and hopefully a solution that actually works?

Thanks.

---

### Post by isantop on 2012-06-14
> **Rich_S said:**
> I have a Gazelle that I bought about 10 months ago.  Upgraded to 12.04 about a month ago.  Ever since the update I've intermittently (maybe 1 out of 3 boots) been getting the "system is running in low graphics mode" dialog on startup.

Googling shows this to be a pretty widespread problem for those running the nVidia chipset.

I've done the:

sudo apt-get purge fglrx
sudo apt-get install fglrx

thing a few times.  It seems to work sometimes, but then again, just rebooting usually works after 2 or 3 tries so who know.

Is there a definitive answer to the cause of this and hopefully a solution that actually works?

Thanks.

I would go ahead and run this command first: 
```
sudo apt-get purge fglrx
```
FGLRX is the AMD proprietary graphics driver, which shouldn't be installed on your Gazelle. That may be causing problems.

---

### Post by tru_k on 2012-06-27
try running** sudo apt-get install gdm** worked on my inspiron 1525

---

### Post by Carborundum on 2012-06-27
> **tru_k said:**
> try running** sudo apt-get install gdm** worked on my inspiron 1525
GDM (GNOME Display Manager) is a login greeter, similar to LightDM which is already installed by default in Ubuntu 12.04. Installing it is unlikely to have any effect other than possibly breaking LightDM.

---

### Post by Carborundum on 2012-06-28
Interestingly, this just happened to me, on my almost* fresh-out-of-the-box GazP7. I will see if I can investigate it further if it keeps happening.

*I'm running kernel 3.4 to avoid the system freeze issue reported elsewhere.

---


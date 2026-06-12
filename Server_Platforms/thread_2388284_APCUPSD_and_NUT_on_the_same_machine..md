---
title: "APCUPSD and NUT on the same machine."
date: 2018-03-31
forum: Server Platforms
---

### Post by isidoro4 on 2018-03-31
Hi, I’d like to know if I can install APCUPSD and NUT on the same machine to handle different ups. I have tried with Debian 8 but installing a package remove the other.

---

### Post by volkswagner on 2018-03-31
It seems like they should be used one or the other but not both.
Why do you need both?
Can you explain your environment and  reasoning?

---

### Post by isidoro4 on 2018-03-31
> **volkswagner said:**
> It seems like they should be used one or the other but not both.
Why do you need both?
Can you explain your environment and  reasoning?

Thanks for reply. I have a mini server. I want use it to manage three ups. I have a Nas, a Workstation with Ubuntu and an iMac. Nut is a better solution for linux-based machines while Apcupsd is better for Mac. So I&#8217;d like to have Nut and APCUPSD working together...

---

### Post by volkswagner on 2018-03-31
I've had no issues with apcupsd on Linux. I use it on systems sharing UPS and on systems with "dumb" UPS (connects to machine via IP to be aware of power loss/state).

I still don't know why you need both servers on one machine.

---

### Post by isidoro4 on 2018-04-01
In the next days I try APCUPSD with multiple instances. I must do a few of tweak on my Nas. Can you tell me if gapcmon-gui is working for the new version of Ubuntu?

---

### Post by volkswagner on 2018-04-01
I don't know about gapcmon-gui. I haven't been running any Linux desktop environments.

---


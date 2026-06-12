---
title: "managing our shared internet service"
date: 2013-02-01
forum: The Cafe
---

### Post by bananaboatcoat on 2013-02-01
We have a huawei e583 mobile hotspot for our internet use.
 
We have limited bandwidth per month. Several people are sharing this internet.
 
 
 
Questions
 
Is there some way to give each person only his share, and then cut them off when they reach their maximum?
 
Is there a way to monitor how much bandwidth each MAC address has used?
 
 
is there a way throttle the bandwidth speed?

---

### Post by mips on 2013-02-02
Yes all this is possible. Do you have a spare PC or other router available though?

[MikroTik]("http://wiki.mikrotik.com/wiki/Main_Page") is ideal for this but needs dedicated router hardware or you can run [RouterOS]("http://www.mikrotik.com/download") in a [VM]("http://www.techonia.com/218/install-mikrotik-virtualbox") on one of you existing PCs but this PC would have to stay on 24/7.
Another option are things like Gargoyle router which installs new firmware on a [existing router]("http://www.gargoyle-router.com/wiki/doku.php?id=supported_routers_-_tested_routers").
Also things like pfSense etc. Squid proxy is another way.

There are many ways to do this, you just have to decide which method suites you best.

---

### Post by bananaboatcoat on 2013-02-02
Thanks, mips, for your reply.

Will your solutions work for this device that only has WiFi, and no ethernet jatk?

---

### Post by bananaboatcoat on 2013-02-11
Mips, we don't really have a spare PC. 

Yes, we have a D-Link router. Why do you ask if we have another router?

---


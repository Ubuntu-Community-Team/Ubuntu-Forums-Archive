---
title: "Ubuntu 16.10 Lags when using VirtualBox"
date: 2016-12-18
forum: Virtualisation
---

### Post by orestis-0 on 2016-12-18
Hello, 

I am running Ubuntu 16.10 on my laptop(i5-7200U, SSD, 8 GB ram) and I have windows 10 on virtualbox. When I start the virtualbox Ubuntu(host) lags but windows(guest) are fine. I gave 5gb of ram for windows,so I still get 3gb + swap for my ubuntu. Same settings with a 5-6 year old laptop and I had no problems. Can you help me?

Thanks, Orestis

---

### Post by howefield on 2016-12-18
Thread moved to the "*Virtualisation*" forum.

---

### Post by ajgreeny on 2016-12-18
> **orestis-0 said:**
> Hello, 

I am running Ubuntu 16.10 on my laptop(i5-7200U, SSD, 8 GB ram) and I have windows 10 on virtualbox. When I start the virtualbox Ubuntu(host) lags but windows(guest) are fine. I gave 5gb of ram for windows,so I still get 3gb + swap for my ubuntu. Same settings with a 5-6 year old laptop and I had no problems. Can you help me?

Thanks, Orestis
I always get an error message in the VBox Manager window if I try to use more than 50% of my machine's RAM for a guest.
Do you really need 5GB for Windows 10?  I suggest you reduce that in the VBox Manager to 4GB and see if that speeds up your host.

---

### Post by orestis-0 on 2016-12-19
The ram I gave is the maximum acceptable(after 5G&#914; it goes to red). The point is that with an Intel M370 and 8GB of ram I had the same configuration(3gb host and 5 gb ram) and it would run MatLab with no lags in the host or guest. Now it lags even when I try to start the virtual machine. I tried OpenBox it lags even when I am using openbox!

---

### Post by ynota on 2017-01-06
check your process memory usage with 'system monitor'. Depending on what you have running on your host you may be leaving yourself short with 3Gb ram, My Ubuntu 16.10 uses just over 1.3 Gb by itself...

---


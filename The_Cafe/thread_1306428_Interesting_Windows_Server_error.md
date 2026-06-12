---
title: "Interesting Windows Server error"
date: 2009-10-30
forum: The Cafe
---

### Post by Golem XIV on 2009-10-30
The place where I work is a Windows-only place.  Although I'm not in charge of the servers, it is usual for me to get warning mails from the server monitoring software whenever something goes wrong.  However, the one I got this morning made me laugh my butt off:

```
Severity:  Error
Status:  New
Source:  System:  System Up Time:  
Name:  Server has been up for 90 days.
Description:  :  :   value = 
Domain:  OURCORPORATEDOMAIN
Agent:  OUR2K3SERVER
Time:  10/29/2009 22:00:00
Owner:  IT_SRVC
```

I guess that an uptime of 90 days or more is such a rare ocurrence in the Windows world that it generates an error :-)

---

### Post by PatrickBoyle on 2009-10-30
If your server guys are worth more than the air they consume, they will patch the machines before uptime reaches 90 days.

It *is* rare for Windows servers to be up more than 90 days. Not because of instability, but the need for security patches.

---

### Post by pwnst*r on 2009-10-30
> **PatrickBoyle said:**
> If your server guys are worth more than the air they consume, they will patch the machines before uptime reaches 90 days.

It *is* rare for Windows servers to be up more than 90 days. Not because of instability, but the need for security patches.

^^exactly this.

---

### Post by Exodist on 2009-10-30
> **PatrickBoyle said:**
> If your server guys are worth more than the air they consume, they will patch the machines before uptime reaches 90 days.

It *is* rare for Windows servers to be up more than 90 days. Not because of instability, but the need for security patches.
Patching doesnt always mean completely restarting the server. Even windows doesnt need to restart for each item anymore, only driver, kernel or system stuff brought up at runtime.

+1 for the IT guys keeping it up for 90days.. Thats actually a small challenge to keep windows from going quirky.

---

### Post by maflynn on 2009-10-30
definitely, we patch our servers every month or sooner depending on what MS releases.

---

### Post by jdrodrig on 2009-10-30
well, I cannot laugh about it yet...I have not kept my box running uninterrupted for 90days yet....so far, my current record is 40 days. 

With some luck, I will re-write here in two months to laugh about this...
:D

---

### Post by PatrickBoyle on 2009-10-30
> **Exodist said:**
> Patching doesnt always mean completely restarting the server. Even windows doesnt need to restart for each item anymore, only driver, kernel or system stuff brought up at runtime.
MS Server patches almost always request a reboot. Again, if your server guys have even the slightest interest in their job security, they will reboot when a patch suggests it.

> +1 for the IT guys keeping it up for 90days.. Thats actually a small challenge to keep windows from going quirky.
It actually *is* a small challenge. The bigger challenge would be convincing someone to pay you to manage their Windows servers when you so clearly haven't the slightest idea what you're doing, to the point you find it challenging to keep those mysterious boxes from going quirky.

---

### Post by ukripper on 2009-10-30
Simply amazing uptime on windows server! Is it WS 2003?

---

### Post by Bachstelze on 2009-10-30
> **PatrickBoyle said:**
> MS Server patches almost always request a reboot.

Not true, in 2k8 at least. My 2k8 machine currently has an uptime of 56 days, and there have been quite a few patches since I last rebooted it (which, by the way, was due to a kernel update of the Linux Xen dom0 it runs under).

---

### Post by falconindy on 2009-10-30
I babysat a Win2k Advanced Server box that played host to a Unisys NX series mainframe. It was the back end to a credit union. In 2 years, I rebooted it three times (3am on a Sunday ftl), and it crashed once when a hard drive failed. So much for RAID-10.

Give Microsoft **some** credit.

---

### Post by clonne4crw on 2009-10-30
It's not unheard of.

My Windows XP rig has been running for 120 days without reboot, and since last January with a few reboots. Works like a charm.

---


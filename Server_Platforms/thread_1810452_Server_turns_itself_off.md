---
title: "Server turns itself off"
date: 2011-07-23
forum: Server Platforms
---

### Post by bigmonmulgrew on 2011-07-23
Hi guys
I have a ubuntu 11.04 LAMP server
I got up this morning and it was off.
Its set to restart after a powerfailure and it does this ok if i test it by turnign the plug off.

Any ideas why it would turn itself off.

---

### Post by 2F4U on 2011-07-23
Is there some kind of power management enabled? Did you install a desktop or server version of Ubuntu?

---

### Post by bigmonmulgrew on 2011-07-23
There isnt any power management enabled as far as I'm aware.
The server has been running a couple of months and has never turned itself off. I've rebooted it a couple of times obviously but its never turned itself off.

Its the server version of ubuntu

---

### Post by clrg on 2011-07-23
I suspect someone turned it off deliberately.

---

### Post by bigmonmulgrew on 2011-07-23
Somehow I doubt that.
Its a home server. Theres only me and my other half here.

---

### Post by headvampyre@hotmail.co.uk on 2011-07-23
Have you checked the BIOS battery? If there was a powercut and the batteries out, that would explain why its not restarted.

---

### Post by bigmonmulgrew on 2011-07-24
Bios bateery is fine. It still has the settings i set.
I dont think there was a power cut.

---

### Post by Entilza on 2011-07-24
Check the logs? /var/log/sysconfig   /var/log/messages    Look for the date/time it turned off.

---

### Post by Gyokuro on 2011-07-24
Maybe a power problem or too much heat, check cpu fan, memory and psu

---


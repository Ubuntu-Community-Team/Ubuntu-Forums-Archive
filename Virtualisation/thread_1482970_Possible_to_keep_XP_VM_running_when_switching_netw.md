---
title: "Possible to keep XP VM running when switching networks?"
date: 2010-05-14
forum: Virtualisation
---

### Post by hantms on 2010-05-14
I have a Win XP Virtualbox VM running on my Ubuntu Lucid Laptop.. The office IP range is different from my home IP range. 

If I keep the VM running when going home, the network on the VM stops working.

Is there any way around this?   Could I reset the network / DHCP somehow on XP so I don't have to reboot?  Just logging off doesn't do it, I have to do a full reboot.

---

### Post by dcstar on 2010-05-15
> **hantms said:**
> I have a Win XP Virtualbox VM running on my Ubuntu Lucid Laptop.. The office IP range is different from my home IP range. 

If I keep the VM running when going home, the network on the VM stops working.

Is there any way around this?   Could I reset the network / DHCP somehow on XP so I don't have to reboot?  Just logging off doesn't do it, I have to do a full reboot.

If you are using bridged networking then all you should have to do is release/renew the IP address in XP.

---


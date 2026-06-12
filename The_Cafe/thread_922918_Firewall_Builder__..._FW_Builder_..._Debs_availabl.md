---
title: "Firewall Builder  ... FW Builder ... Debs available.  Anyone seen this or used it?"
date: 2008-09-17
forum: The Cafe
---

### Post by sefs on 2008-09-17
[http://www.fwbuilder.org/](http://www.fwbuilder.org/)

---

### Post by Ocxic on 2008-09-17
i use it, very nice easy to plan and setup a firewall, just have to install the firewall setup after every reboot. there a way to fix that I'm just too lazy to find out how, and i don't restart my computer enough to worry about that anyway.

great app

---

### Post by ekh on 2008-10-14
> **Ocxic said:**
> i use it, very nice easy to plan and setup a firewall, just have to install the firewall setup after every reboot. there a way to fix that I'm just too lazy to find out how, and i don't restart my computer enough to worry about that anyway.

great app

Copy your fwbuilder script to /etc/init.d/ directory

$ chmod +x your_fwbuilder_script

$ update-rc.d your_fwbuilder_script defaults

---


---
title: "KVM and load balacing"
date: 2011-05-09
forum: Virtualisation
---

### Post by Babushko on 2011-05-09
Shalom , everybody!!!
Sry for dummy question, but i`m newbie in the KVM.



KVM supports VM`s load balncing like VMware DRS. But you have to buy **RHEVS **(Red Hat Enterprise Virtualizaton for Server) or **[COLOR=black]ConVirt Enterprise Edition[/COLOR]**, `cause in the Open Source Edition this features is unavailable - [http://www.convirture.com/products_compare.php](http://www.convirture.com/products_compare.php)  ...


So question, does anyone know any **free alternate management tool** for KVM for using load balancing (Dynamic Workload Management), High-Availability, Backup&Restore


thank you a lot in advice!!!



b.r.,  Azamat Kyrykbayev

---

### Post by Dedoimedo on 2011-05-09
If you're willing to script, you could have your virtual machine snapshot every few seconds/minutes and keep the secondary copy in standby. Have the host heartbeat the running copy every few once in a while - say a combination of ping and ssh uptime, and if it detects a problem, launch the second instance. Use two disks in each virtual machine, one for os and one for data, so that you can come up without losing your stuff.

Not the most elegant solution, but it's free :)

For load balancing, you could have several virtual machines running and serve them via round robin, again using a single disk for storage of data.

Does this make sense to you?

Cheers,
Dedoimedo

---


---
title: "VMware server can't find my VMs"
date: 2009-05-20
forum: Virtualisation
---

### Post by ant2ne on 2009-05-20
Using the web console, virtual machines tab, add virtual machine to inventory, shows servername.com and a standard, expanding standard shows nothing. Probably because my MVs are in a different path. (A different partition even) how do I change/add the path to my VMs.

---

### Post by veloce on 2009-05-20
> **ant2ne said:**
> Using the web console, virtual machines tab, add virtual machine to inventory, shows servername.com and a standard, expanding standard shows nothing. Probably because my MVs are in a different path. (A different partition even) how do I change/add the path to my VMs.

On the right hand side of the web console is a little window headed "Commands". You want the "Add Datastore" command.  (A datastore is where vms are stored in new vmware terminology).

---

### Post by ant2ne on 2009-05-21
Thanks, got it!

---


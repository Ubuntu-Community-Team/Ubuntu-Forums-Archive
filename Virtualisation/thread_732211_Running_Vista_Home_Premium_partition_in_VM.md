---
title: "Running Vista Home Premium partition in VM"
date: 2008-03-22
forum: Virtualisation
---

### Post by DarkW0lf on 2008-03-22
Which VM would be easier to run an existing Vista HP in ?
Machine is Compaq F572US AMD64 X2 with xubuntu 7.10

I have only read VirtualBox docs so far, the migrate_windows howto 'seems' easy enough. I only have to worry about HAL and the IDE check.

What sort of work would the others take ?

---

### Post by dcstar on 2008-03-23
> **DarkW0lf said:**
> Which VM would be easier to run an existing Vista HP in ?
Machine is Compaq F572US AMD64 X2 with xubuntu 7.10

I have only read VirtualBox docs so far, the migrate_windows howto 'seems' easy enough. I only have to worry about HAL and the IDE check.

What sort of work would the others take ?

WMware provides a free utility to convert an existing Windows install (including all the apps etc.) into a VM.

All you need to do afterwards is re-register Windows (because of the changed environment) and it works fine.

I used this with the free VMware server and I don't bother to boot into Windows any more, I just fire up that particular VM whenever I need it (which isn't that often).

---

### Post by DarkW0lf on 2008-04-05
Just remembered the other questioned I had with VM's

Can either VirtualBox or VMWare (or others) load an ISO file in a VM ?
If I had a live cd could I run that in the VM without burning to a cd ?

---


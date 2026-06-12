---
title: "Control # of CPUs in VirtualBox"
date: 2008-11-19
forum: Virtualisation
---

### Post by shahgols on 2008-11-19
Hi all,

I am running VB 1.5.6 and want to tell VB to only use 2 of the quad cores.  How is that done?

---

### Post by shahgols on 2008-11-20
For those who are looking for the same solution as me, I think that there is no way of telling VirtualBox how many CPUs to use.  I checked the user guide from their site and looked and looked and searched by keywords and didn't find anything.  Perhaps in a later release they'll include this capability.

---

### Post by Amorget on 2008-11-20
I believe you can "pin" the VBox backend to a processor core.  My understanding is that VBox doesn't do any sort of multi-threading.

---

### Post by shahgols on 2008-11-21
Thanks for the clarification.  VB still feels faster than Vmware in booting up or shutting down or even starting applications, even without multi-threading.  There are times that one of my applications spikes the CPU to 100% due to sorting of data and what not, it would have been great if VB could use all 4 processors on my machine.  Hopefully they'll add that functionality in the near future.

---


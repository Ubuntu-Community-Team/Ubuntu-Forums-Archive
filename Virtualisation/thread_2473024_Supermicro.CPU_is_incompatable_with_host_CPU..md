---
title: "Supermicro.CPU is incompatable with host CPU."
date: 2022-03-21
forum: Virtualisation
---

### Post by civilpolisen on 2022-03-21
We've been running the servers for quite some time. Today a few servers were closed (switched off) for no obvious reason.
The error message showed: "the CPU is incompatible with host CPU: Host CPU does not provide required features".
On a working server, the settings: Configuration. "Model: qemu64".

From within the broken server, "Model: qemu32" is the only option.
Is it possible that a server forgets the types of CPU it is hosting...!? Sound strange for me! What am I missing??

---

### Post by MAFoElffen on 2022-03-22
Not usually(???) That is very strange. 

Are you saying the VM Domain XML has changed? Has the last modified date on the Domain XML file change recently? As if something has changed it since it's creation or last known modified date? 

That would be where that setting is stored... /etc/libvirt/qemu/<domain_name>.xml

---


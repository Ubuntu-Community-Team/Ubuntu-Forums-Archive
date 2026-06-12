---
title: "Problems with hardy 64b + vmware 2"
date: 2008-05-12
forum: Virtualisation
---

### Post by s_raghu20 on 2008-05-12
Hi,

I have this hardy 64b server running inside vmware 2 on hardy. 

I have encountered a problem though.  I planned to install Oracle 11g inside the vmware server.  For that I "enlarged" the virtual disk of the virtual machine by 3 GB (from original 8 to 11). 

But the system never shows the enlarged hard disk. It still shows the original 8 GB.  Though I had switched on the "dont allocate all the space now". I am not sure if its because of this !!

Furthermore, I copied the installation files to the vm (which I dont like myself).  But when I launch the installer it behaves a bit weird, giving me a message about a file called unzip... here's the original text...

```
Preparing to launch Oracle Universal Installer from /tmp/OraInstall2008-05-12_11-56-19AM. Please wait ...sh: /data/oracle/database/install/unzip: not found

```

Anybody experienced this ?

On the sidelines, another question : 

Is there a way to launch the installer from my host system (without having to copy all the installer files to the vm).  I understood that if I open a shell either way (from host to vm or vice versa), I would be switching the systems itself. ?? I guess nfs should come into play... but dont know exactly how... suggestions pls...

---

### Post by raidensix on 2008-05-12
You need to configure your guest OS to recognize the new available space. Check your inside the guest for a new unused disk.

---

### Post by s_raghu20 on 2008-05-13
> **raidensix said:**
> You need to configure your guest OS to recognize the new available space.

How exactly could I "configure" the guest OS ?  Normally I would look for a device made available and then I could plan to mount it, but there is no new disk added ?  (When I was trying to add space by adding a new virtual hard disk )  Could I force it somehow ?

> 
 Check your inside the guest for a new unused disk.

I normally use df -k for checking for space etc.
Anything else ?

---

### Post by raidensix on 2008-05-13
See if this helps:

[http://alt-j.com/200707/resize-linux-vmware-partitions/]("http://alt-j.com/200707/resize-linux-vmware-partitions/")

[http://communities.vmware.com/thread/126149]("http://communities.vmware.com/thread/126149")

---


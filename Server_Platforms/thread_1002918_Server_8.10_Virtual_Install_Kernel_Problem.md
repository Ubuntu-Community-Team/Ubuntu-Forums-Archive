---
title: "Server 8.10 Virtual Install Kernel Problem"
date: 2008-12-05
forum: Server Platforms
---

### Post by Jeff_Illingworth on 2008-12-05
All,

     I am trying to get my feet wet with Ubuntu Server, so I've attempted to set up a virtual instance on my 8.10 Desktop system using VirtualBox. The install of Server 8.10 from the cd image went fine, but once I try to run from the virtual disk, I get an error that states: "This kernel requires the following features not present on the CPU: pae"

     I am confused as to whether this is really a kernel problem or if it is a problem with VirtualBox (I have had no issues with any of my other VirtualBox installs, though none of them are servers). Any guidance would be appreciated.


Thanks,

Jeff.

---

### Post by aos101 on 2008-12-06
You just need to enable PAE in Virtual Box for the virtual machine.  Go to the settings for the virtual machine and in the general section under the advanced tab make sure "Enable PAE/NX" is checked.  It should then boot.

---

### Post by Jeff_Illingworth on 2008-12-08
aos101,

     Thank you very much. That fixed the problem.


Jeff.

---


---
title: "VMware Virtual Center and VMware Server 1.0.8"
date: 2009-02-23
forum: Virtualisation
---

### Post by maikens on 2009-02-23
I am running VirtualCenter 1.4.1 Build 36208 and have installed VMware Server 1.0.7 amd 1.0.8 on Ubuntu 8.10 Server and the VirtualCenter is reporting 0 MB Memory Available to new VMs on the Summary tab of each server. Both severs do have memory available (one is not even running any guests yet). Using the VMware Server Console, I have also Reserved Memeory for the virtual machines under the Memory tab in the Host settings.

Why is the memory not showing as available?

---

### Post by PilotJLR on 2009-02-23
Hi maikens,
You should really post this on VMTN... this doesn't seems to be an Ubuntu question (though Ubuntu is the host for Server).

I have not seen this version of VirtualCenter in quite a while! Are you sure VC 1.4 is intended to manage Server 1.0.7 resources?? Maybe a better question is... why do you want to use this old VC instead of a Server console? Granted, a separate console for each box, but this is only 2 hosts.

---


---
title: "Ubuntu and Hyper-V SCVMM Migration"
date: 2012-04-17
forum: Virtualisation
---

### Post by sixstringssteve on 2012-04-17
Got a wierd situation. I am running a Hyper-V environment and seem to run into glitches with my Ubuntu servers. They are all 10.04 LTS. When I migrate them with SCVMM some migrate fine and fire right up, others pay heck to get the network interfaces to work right. I modified the /etc/initramfs-tools/modules file (as they were running great on one Hyper-V host befire migration). 
 
The strange thing is some work great, others don't. There are a couple I jsut put legacy NIC's in because perfromance is not important, but I still feel like I took the easy way and let this thing beat me.
 
I know there may be subltle differences in hardware profiles between the hosts, but they are all Dell PowerEdges, so the differences should be minimal.
 
Any of you out there run into these issue with Hyper-V?

---

### Post by lukeiamyourfather on 2012-04-17
My brief experience with Hyper-V was terrible. Using Ubuntu Server 10.04 LTS made it even more frustrating because it was lacking some of the Hyper-V kernel modules. Newer version of Ubuntu Server have better integration with Hyper-V but I never got that far with it.

---

### Post by sixstringssteve on 2012-04-17
Because we are an enterprise environment, I only use LTS.  I am hoping in a few weeks to start upgrading to 12.04 for that very purpose.  10.04 can have the modules modified and it works great, right up to the point of a VM migration.

---


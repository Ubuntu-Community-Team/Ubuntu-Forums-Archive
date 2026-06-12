---
title: "karmic network problems when running as KVM?"
date: 2009-11-06
forum: Virtualisation
---

### Post by tomhorsley on 2009-11-06
I installed both 64 and 32 bit ubuntu 9.10 virtual machines running under KVM on a fedora 11 box. Both of these KVMs seem to have great difficulty maintaining a ssh connection. I'll ssh into the virtual machine to run some tests, and a little while later the ssh on the outside appears hung and the ssh on the inside of the virtual machines is simply gone. There is no longer any trace of the connection, but the network is still up, I can make new connections, and all is well (for a while). I have 8.10 and 9.04 KVMs running on the same host withg absolutely no problems like this. Anything about this strike a familiar note with anyone? (I've tried both virtio and an emulated hardware NIC and get the same behavior).

---


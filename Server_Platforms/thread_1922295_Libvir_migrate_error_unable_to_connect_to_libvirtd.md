---
title: "Libvir migrate error: unable to connect to libvirtd at 'host'"
date: 2012-02-08
forum: Server Platforms
---

### Post by SrSaitam on 2012-02-08
Hi everyone, I'm a newbie with Libvirt.

I'm trying to migrate a virtual machine from nodeA(192.168.1.70) to nodeB(192.168.1.100) using this command in nodeA:


virsh migrate VM1 qemu+tcp://192.168.1.100/system


And this is the error printed on screen:

 
**error: unable to connect to libvirtd at '192.168.1.100': Connection refused**


**Libvirtd **is running in the destination host, this appear to be simple but I can't figure out how to solve it.

Hope someone can help me!

Thanks :P

---


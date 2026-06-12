---
title: "Shared Folders in QEMU-KVM with Virtual Machine but without networking"
date: 2016-11-10
forum: Virtualisation
---

### Post by waterdevil on 2016-11-10
Hi,

I'm running Kubuntu 16.10 as host and windows 10 as guest.

  The guest system should be a sandbox without Internet so I removed the network card.


  There is an option in virtual-manager to add a file system (instead of a  storage device). I added a path, but how can i get access in the guest  system (Windows)?


  I can't find any documentation of access in the guest windows.


  I am looking for a definition which the path of the host assigns a letter or directory in the guest-windows.


  I don't want to use samba with virtual-nic this i tried and is working.


  The second option would be a set-up with NIC but disabled Internet.


  many thanks for your help
  Andy

---

### Post by waterdevil on 2016-12-15
I still could not solve this problem.

Please can anybody help?

Thank you

---

### Post by TheFu on 2016-12-15
I've never needed this, so don't know if it works or is even possible.

If there is a solution, it won't be using a GUI.  Learn about all the options of the VM XML definition files.  There are lots of different backend storage options, but most will assume a network stack since that is generally how Unix works.
[http://www.linux-kvm.org/page/9p_virtio](http://www.linux-kvm.org/page/9p_virtio) is the closest I could find. Looks like Windows would need the 9p file system support to make use of it. [http://9p.cat-v.org/implementations](http://9p.cat-v.org/implementations) ... nothing directly useful. Sorry.

I'd enable networking and firewall it.

---


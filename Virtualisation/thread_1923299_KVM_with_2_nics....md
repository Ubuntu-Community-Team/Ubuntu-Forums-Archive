---
title: "KVM with 2 nics..."
date: 2012-02-10
forum: Virtualisation
---

### Post by bercy on 2012-02-10
Hi,

Here are my requirements, I'd like to know how to setup networking :

I have two modems, and so two internet IPs.  Each modem currently has the same IP : 192.168.0.1.

In the PC, I have two nics (eth0, eth1).

I want the host PC and the VM to each have their own static local IP, for example 192.168.0.100 for the host, 192.168.0.200 for the VM.

I want the host PC to communicate on the internet through modem #1.

I want the VM to communicate on the internet through modem #2.

AND

I want the PC to be able to communicate with the VM, and vice-versa, on the "virtual" LAN...

What settings do I need to achieve this ?

Thanks.

---


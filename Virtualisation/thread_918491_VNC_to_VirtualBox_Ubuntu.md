---
title: "VNC to VirtualBox Ubuntu?"
date: 2008-09-13
forum: Virtualisation
---

### Post by magicmt on 2008-09-13
i have an XP computer with VirtualBox Ubuntu. is it possible to remote into this virtual machine? i set everything up but it won't connect. i have another computer running ubuntu, and i can vnc into that one with no problem. this makes me think that it might not be possible for VM.

---

### Post by maxrisc on 2010-04-27
I abhor open threads. Even old ones.

Yes you can but you interface must be set to host only because windows will not act like a router by default. This is the easiest way unless you configure the xp box for ics and punch holes in the network firewall with port forwarding.

---

### Post by amireldor on 2010-09-05
@maxrisc:
Can you elaborate more on how to do that, for the sake of n00bs?
Also, how can one do that when the OS inside the VirtualBox is an Ubuntu Server?

---

### Post by aSkqsTsn on 2011-01-02
any luck resolving this issue or info on configuring host OS to forward the connection to virtualbox?
 I have just encountered the same issue.

---

### Post by howefield on 2011-01-02
Try setting the VM network setting to use a bridged adapter.

And next time, open a new thread rather than append your post to an old one.

---

### Post by danny2010 on 2011-01-04
Just configure you card to bridged mode and put the guest and host machine in the same subnet for instance: 192.168.0.X

----------
[linux ubuntu](http://tips-linux.net)

---


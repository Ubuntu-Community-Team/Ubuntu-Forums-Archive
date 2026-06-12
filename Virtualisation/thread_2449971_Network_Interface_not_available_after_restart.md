---
title: "Network Interface not available after restart"
date: 2020-09-04
forum: Virtualisation
---

### Post by mflemmings760 on 2020-09-04
Hi,

I created a Ubuntu 20.04.1 LTS on VMware workstation platform. I cloned the Machine and created 2 cloned images. After cloning I deleted the Network interface of the cloned images and added a new one. Now my network interface doesn't come up. Infact, it is even not available. I ran the following command:

sudo dhclient -v

It created the interface and it is up. But when I restart the VM, network interface again vanished. Each time I restart the VM,  I have to run sudo dhclient -v command and my network interface is up and running.

Is there any permanent solution to this issue?


Thanks,

---

### Post by wildmanne39 on 2020-09-04
Moved to Virtualisation sub-forum.

---


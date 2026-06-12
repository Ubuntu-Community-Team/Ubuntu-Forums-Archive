---
title: "Giving separate, distinct IP addresses to the host and guest"
date: 2008-02-04
forum: Virtualisation
---

### Post by Starks on 2008-02-04
I have two Internet interfaces on my laptop, each has its own **distinct** IP address assigned to it.

How do I give my host OS exclusive access to one of those interfaces and the guest OS exclusive access to the other?

Is this even possible with VirtualBox or VMWare?

---

### Post by pdub on 2008-02-04
I use vmware workstation 6.02 and have this working fine. I just set the bridged adapter to my second card (eth1). This way I have the host connected to network A and the virtual machine connected to network B.

I am no familiar with VirtualBox or the free vmware server though.

---

### Post by Starks on 2008-02-05
How I do set this up in VMWare Workstation?

---

### Post by goginot on 2008-02-05
use this guide
[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

---


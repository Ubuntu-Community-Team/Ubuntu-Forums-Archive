---
title: "How to P2V (Physical-to-Virtual) a Ubuntu Host in a simple way ?"
date: 2014-07-02
forum: Virtualisation
---

### Post by ubuserone on 2014-07-02
Having an old ubuntu OS 9.10 , 10.10 running on other old computer.Both are just 40-60GB size
Planning to copy and convert into virtual guest.Using virtualbox.[http://en.wikipedia.org/wiki/Physical-to-Virtual](http://en.wikipedia.org/wiki/Physical-to-Virtual)

Any much easier way to P2V ? 
Which table on vbox manual guiding from Ubuntu OS to Virtual ?
;)

---

### Post by TheFu on 2014-07-02
[http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview](http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview) is how I've done it. Works regardless of VM hypervisor.  I've gone from Vbox, ESXi and Xen to KVM that way.  For non-desktops, KVM is great. For desktops ... er ... virtualization really isn't ideal for what most people expect - but virtualbox seems to be the best answer.

Of course, you know that both 9.10 and 10.10 are unsupported, so they shouldn't be allowed on ANY network.  14.04 is nice and you don't have to run Unity.

40G is HUGE!  Why so large?  Most of my VMs are 4-15G.  Data is stored outside the VM on the network.  Perhaps now is the time for you do consider this?

---


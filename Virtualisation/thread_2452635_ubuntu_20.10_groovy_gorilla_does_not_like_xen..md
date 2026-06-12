---
title: "ubuntu 20.10 groovy gorilla does not like xen."
date: 2020-10-26
forum: Virtualisation
---

### Post by marietto2008 on 2020-10-26
Hello to everyone.

it seems that ubuntu 20.10 does not like xen. During the the upgrade from focal fossa to groovy gorilla I have found this bug :

[https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/1901398](https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/1901398)

and after having installed a fresh copy of groovy gorilla,I found another bug,like this :

[https://ibb.co/vHxsffZ](https://ibb.co/vHxsffZ)

It's not freezing but holding, "Starting Hold until boot process finishes up ..." Because the dependencies are not started for the sssd.service, my computer is holding infinitely. System Security Services Daemon, I think this is apparmor,but I disabled and removed / purged it with all the dependencies,but the error persists. what can I do ?

---


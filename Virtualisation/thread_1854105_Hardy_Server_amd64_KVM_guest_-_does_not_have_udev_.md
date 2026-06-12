---
title: "Hardy Server amd64 KVM guest - does not have udev rules working"
date: 2011-10-03
forum: Virtualisation
---

### Post by nicolasdiogo on 2011-10-03
hello,

i have KVM hosts using debian 6 amd64 with ubuntu hardy guests.
and i find that udev is not working properly.

**/etc/udev/rules.d/70-persistent-net.rules**
is empty.

i have found it to be a regular problem.
[http://www.turnkeylinux.org/docs/virtualization/udev-persistent-net-generation](http://www.turnkeylinux.org/docs/virtualization/udev-persistent-net-generation)

i have removed *70-persistent-net.rules* rebooted the system:


and tried reinstalling udev but nothing semms to solve this problem.

any suggestions on how to get udev to create rules for the network card?

thanks,

---

### Post by nicolasdiogo on 2011-10-04
bumping ..

does anybody have any idea how to solve this?

---


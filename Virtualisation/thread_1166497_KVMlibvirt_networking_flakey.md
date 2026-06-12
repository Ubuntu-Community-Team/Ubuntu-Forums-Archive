---
title: "KVM/libvirt networking flakey"
date: 2009-05-21
forum: Virtualisation
---

### Post by freakalad on 2009-05-21
Don't quite know if this issue is limited to KVM, libvirt or brctl.

Installed KVM per instructions & been running it for some time, via bridging

Occasionally the networking would just go awry; either when adding or altering another client, or when applying changes on the host (which I need to do frequently). I make extensive use of virt-manager & virsh (I like GUI's, so please, no dodgy comments about using KVM from CLI; been there, done that)

Usually I'm able to see the host from the clients, but nothing beyond (network router/gateway, 'net)

A full system reboot usually solves the matter, but this is practical every time I create a non-standard client, or this issue crops up.

Is anyone able to give some insight into what might be causing this & how to address it? Or is this a bug & should I report it accordingly?

Thanks

- J

---

### Post by freakalad on 2009-05-21
Rebooted my server, but the problem is still present.

Clients are unable to get a DHCP lease, and even if I do specify a static IP, they are only able to see the host & nothing beyond. 

Seems to point to a routing or internal NAT issue on my host

---

### Post by freakalad on 2009-05-21
Possibly a libvirt or brctl problem, since I'm able to get a connection when running KVM directly (route IP resolves to host)

---


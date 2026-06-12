---
title: "Virtualization network problem"
date: 2012-01-26
forum: Virtualisation
---

### Post by hever0 on 2012-01-26
I have got two problems with networking. Use two operating systems - Ubuntu 10.04 (host and guest) and Windows 2008 server R2 (two guests). Using qemu-kvm, libvirt. Network is bridged, type virtio.

1) Time to time guest network stops working, no traffic.

It's done when network has high load, but no everytime. On Windows (through VNC) I see normal Network connection, no error anywhere. But there is no traffic. If I disable & enable connection, its will normal start working.

2) attach-interface or attach-device not work for 100%

When I try everything to solve my first problem, similar problem appeared. When I try attach network interface to guest, guest find it, but there is no traffic again.

Trying everything to get it works, but only what works is when I suspend & resume domain - voila, it works.

With attach-interface or attach-device I try everything, everytime the same problem - no traffic.

---
```

$  cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
        address 10.0.0.99
        network 10.0.0.0
        netmask 255.255.255.0
        broadcast 10.0.0.255
        gateway 10.0.0.138
        bridge_ports eth0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0
        dns-nameservers 10.0.0.138

$ sudo virsh attach-interface vmtest --type bridge --source br0 --mac 52:54:00:62:17:ab --model virtio
Interface attached successfully

$ sudo virsh suspend vmtest
Domain vmtest suspended
$ sudo virsh resume vmtest
Domain vmtest resumed

```

Linux version 2.6.32-36-server; x86_64; Guests are 64bit

---

### Post by hever0 on 2012-01-27
No one knows?

Is this bad place for this question? Is anywhere better place?

Thanks for any help...

---

### Post by japzone on 2012-01-27
You have to give people time to answer when using a Forum. Alot of people don't get a chance to login everyday so the person that knows the answer probably hasn't shown up yet. Just bump the Topic every couple of days to make sure it's visible.

I'd help you but I have no experience with KVM as I prefer VirtualBox. Hope you get help soon :)

---

### Post by TheR on 2012-02-08
Looks like I am one of those late to the party ;-)

I had the same problem and I switched from virtio to Intel adapter. So far (4 months) it works.

by
TheR

---

### Post by hever0 on 2012-02-13
Some better solution?

---


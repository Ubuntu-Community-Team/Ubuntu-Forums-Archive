---
title: "Wxp under kvm"
date: 2017-07-09
forum: Virtualisation
---

### Post by karel2 on 2017-07-09
Running Ubuntu 14.04 and kvm 2.0.0, I have a few virtual machines running nicely. I now want to add a Win XP virtual and I can install it but I cannot get it to have networking.
Some of my other virtuals need a fixed IP, accessible from outside, so I set up my host machine with a bridged interface. How should I set up the networking for the virtual WXP? Do I need to use the virtio drivers?

Definition of the bridge interface of the host machine:

auto br0
iface br0 inet static
        address 192.168.0.8
        network 192.168.0.0
        netmask 255.255.255.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        bridge_ports eth2
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0

Example of a working guest:

kvm -hda /vdi/bbx.raw -m 1024 \
  -device e1000,netdev=net0,mac=DE:AD:BE:EF:6F:87 \
  -netdev tap,id=net0


Any comments and pointers welcome.

---

### Post by KillerKelvUK on 2017-07-11
Network setup for XP should be similar/same to your other guests, only it maybe that you need to provide XP with a driver for the virtual NIC.

You could use virtio but I think there are also drivers for the e1000 model, me personally if virtio is available I use it.

Drivers from here [https://fedoraproject.org/wiki/Windows_Virtio_Drivers](https://fedoraproject.org/wiki/Windows_Virtio_Drivers) grab the latest iso, I had a quick look at XP drivers are included.

---

### Post by karel2 on 2017-07-11
Thanks Kelv, I will be looking into that but not right now, several more urgent things on hand. Will report back as soon as I have something to report!

---


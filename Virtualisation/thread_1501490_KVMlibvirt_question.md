---
title: "KVM/libvirt question"
date: 2010-06-04
forum: Virtualisation
---

### Post by srivo on 2010-06-04
I use KVM for my Virtual machine. I setup my bridge using the information at [http://wiki.libvirt.org/page/Networking](http://wiki.libvirt.org/page/Networking)

Did I need to issue the sudo sysctl -p /etc/sysctl.con each time I reboot the computer? Is there a way to load it automatically?

My VM doesn't get an address if I don't do it!

My network interfaces file is:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
    address 192.168.0.10
    network 192.168.0.0
    netmask 255.255.255.0
    broadcast 192.168.0.255
    gateway 192.168.0.1
        bridge_ports eth0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0

---

### Post by srivo on 2010-06-04
In fact I made some more test and no VM reach the network if I don't send  the sysctl command!

I don't understand, should sysctl.conf loaded at boot?

---


---
title: "Bridge networking problem"
date: 2016-02-23
forum: Virtualisation
---

### Post by satimis on 2016-02-23
Hi all,

VirtualBox 5.0.14
Host - Ubuntu 14.04 desktop 64bit
VM - Ubuntu 14.04. desktop 64 bit

Following entries works on all running VMs
```

&#10219; cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

# add bridge ports
auto br0
iface br0 inet static
        address         192.168.0.xxx
        dns-nameservers xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx
        network         192.168.0.0
        netmask         255.255.255.0
        broadcast       192.168.0.255
        gateway         192.168.0.1
        bridge_ports    eth0
        bridge_fd       9
        bridge_hello    2
        bridge_maxage   12
        bridge_stop     off

```

But it doesn't work on newly installed Ubuntu 14.04 VM.  I have been working couple hours and couldn't discover the cause.  NAT works without problem.

GuestAddtion already installed

Please help.  Thanks

Regards
satimis

---

### Post by MAFoElffen on 2016-02-24
Are you sure?

Although, I know this is an edited template file, where also I assume there are real values and not x'es... this is still not a valid VM interfaces configuration. That config sets an Ubuntu host's first physical network card up as a bridge, from a hypervisor's guest Vlan to the hosts local network. So if you try to use that on a VM guest, it would still be in an internal virtual vlan...

Your host NID is 192,168.0.0? Then you woulds set the VM NIC setting to bridge and set eth0 to static on that NID...

Unless-- This is a bridge from vlan 1 to vlan0, where to pass through another bridge to your to host network? Otherwise... Did you post the wrong interfaces file?

---

### Post by satimis on 2016-02-24
Hi MAFoElffen,

Sorry.  I forgot to install "bridge-utils".  After having it installed Internet can be connected.

Thanks

satimis

---


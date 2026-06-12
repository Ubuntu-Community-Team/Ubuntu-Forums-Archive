---
title: "How to set guest static IP"
date: 2008-08-02
forum: Virtualisation
---

### Post by satimis on 2008-08-02
Hi folks,


Ubuntu 8.04 server amd64 - host
Ubuntu 6.06 server amd64 - guest
KVM


I referred;
The Kernel Virtual Machine
[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

and couldn't figure out how to set guest static IP address


Host;

/etc/network/interfaces```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


auto eth0
iface eth0 inet manual


# The primary network interface
auto br0
iface br0 inet static
        address 192.168.0.110
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

```


Guest;
/etc/network/interfaces```

auto lo
iface lo inet loopbak

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

$ ifconfig```

...
inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
....

```


Host;

/etc/libvirt/qemn/networks/default.xml```

<network>
  <name>default</name>
  <uuid></uuid>
  <bridge name="virbr%d" />
  <forward/>
  <ip address="192.168.122.1" netmask="255.255.255.0">
    <dhcp>
      <range start="192.168.122.2" end="192.168.122.254" />
    </dhcp>
  </ip>
</network>

```


Please shed me some light.  TIA


B.R.
satimis

---

### Post by igwk on 2008-08-04
See my response in your other thread about pinging from a guest OS ([http://ubuntuforums.org/showthread.php?t=878883](http://ubuntuforums.org/showthread.php?t=878883)).  Both problems have the same solution.

---

### Post by eival on 2008-08-05
if you have a router you can set your DHCP to reserve your current IP and then your computer will save that IP for your computer forever, thus you have a "static ip" an wont need to do anything in Ubuntu

---

### Post by satimis on 2008-08-05
> **igwk said:**
> See my response in your other thread about pinging from a guest OS ([http://ubuntuforums.org/showthread.php?t=878883](http://ubuntuforums.org/showthread.php?t=878883)).  Both problems have the same solution.
Hi igwk,


Thanks for your URL.


The threads seemingly can't help me out.  I'm still struggling.  I'll come back to this thread if I can find a solution.


Thanks


satimis

---

### Post by satimis on 2008-08-05
> **eival said:**
> if you have a router you can set your DHCP to reserve your current IP and then your computer will save that IP for your computer forever, thus you have a "static ip" an wont need to do anything in Ubuntu
Hi eival,


Thanks for your advice.


I have not problem setting static IP on host.  I only encounter problem to set static IP on guest.


satimis

---


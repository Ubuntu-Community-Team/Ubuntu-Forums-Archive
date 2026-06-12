---
title: "Public IP on KVM client not working at all."
date: 2011-02-18
forum: Virtualisation
---

### Post by pnunn on 2011-02-18
Hi folks,

I've been battling this one for a while now and not getting anywhere.

I've set up a KVM host with a bridge interface as detailed in several places on here and it seems to be OK

```

brctl show
bridge name     bridge id               STP enabled     interfaces
br0             8000.e0cb4e8818a3       no              eth0
                                                        vnet0
virbr0          8000.000000000000       yes

# Bridge between eth0 and eth1
auto br0
iface br0 inet static
  address 192.168.123.82
  netmask 255.255.255.128
  gateway 192.168.123.1
  bridge_ports eth0
  bridge_stp off
  bridge_maiwait 0
  bridge_fd  0

```

This worked fine with the "normal" networking (with the nat) but now that I've converted it to using the bridge mode I can't get any networking happening.

The xml config file has
```
   <interface type='bridge'>
      <mac address='52:54:00:4e:d9:a3'/>
      <source bridge='br0'/>
    </interface>

```

The guest machine's network config is
```

auto eth0
iface eth0 inet static
  address 111.126.234.118 (made up address)
  netmask 255.255.255.240
  gateway 111.126.234.113
  broadcast 111.126.234.127

```

It starts up fine, I can log into the machine using virt-manager, but the client cannot see anything on the network (Destination Host Unreachable).  The routing table looks fine as does the ifconfig output.

I'm not sure if the issue is routing on the host... there is no sign of this ip subnet in the routing table of the host

```

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.123.0   0.0.0.0         255.255.255.128 U     0      0        0 br0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
0.0.0.0         192.168.123.1   0.0.0.0         UG    100    0        0 br0

```

Any ideas anyone?  What am I missing? I can't ping the host IP (which is on the 192.168.123.0 subnet from the client either.

Thanks

Peter.

---


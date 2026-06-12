---
title: "Problem on running static IP"
date: 2009-12-08
forum: Virtualisation
---

### Post by satimis on 2009-12-08
Hi folks,

KVM
host - Debian 5.0
VM (guest) - Ubuntu 9.10


Just created a new VM running Ubuntu 9.10 with following command;
```

$ sudo virt-install --connect qemu:///system -n vm30ubuntu910 -r 512 --vcpus=2 -f /home/satimis/VM/vm30ubuntu910.qcow2 -s 12 -c /home/satimis/Desktop/mini_ubuntu9.10.iso --vnc --noautoconsole --os-type linux --accelerate --network=bridge:br0 --hvm

```

Internet can be connected with following dynamic IP

$ cat /etc/network/interfaces```

auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```


If change it to static IP then it can't connect Internet

$ cat /etc/network/interfaces```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
        address         192.168.0.30
        netmask         255.255.255.0
        network         192.168.0.0
        broadcast       192.168.0.255
        gateway         192.168.0.1
        bridge_ports    eth0
        bridge_fd       9
        bridge_hello    2
        bridge_maxage   12
        bridge_stp      off

```


$ sudo ifconfig eth0```

eth0	Link encap: Ethernet  HWaddr 54:52:00:07:69:c8
	Broadcase multicast  MTU:1500  Metric:1
	RX packets:0 errors:0 dropped:0 ovrruns:0 frame:0
	TX packets:0 errors:0 dropped:0 ovrruns:0 carrier:0	
	collisions:0 txqueuelen:1000
	RX bytes:0 (0.0 B)  TX bytes:0 (0.0.B)
	Interrupt:10

```

$ netstat -rn```

Kernel IP routing table
Destination  Gateway  Genmask  Flags  MSS Window  irtt  Iface

```

Please advise how to fix the problem.  TIA


Remark:
Other VMs works seamlessly with above static IP settings


B.R.
satimis

---


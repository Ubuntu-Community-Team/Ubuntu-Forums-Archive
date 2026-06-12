---
title: "dedicated nic card to KVM vm"
date: 2019-11-03
forum: Server Platforms
---

### Post by Heeter on 2019-11-03
Hi all,

I have for network cards on my server. Planning on running 2 vm's using KVM.

```

root@server:/var/lib/libvirt/boot# ifconfig
eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.11  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::d6be:d9ff:feef:f05c  prefixlen 64  scopeid 0x20<link>
        ether d4:be:d9:ef:f0:5c  txqueuelen 1000  (Ethernet)
        RX packets 392  bytes 40823 (40.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 16  bytes 1280 (1.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

eno2: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.12  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::d6be:d9ff:feef:f05e  prefixlen 64  scopeid 0x20<link>
        ether d4:be:d9:ef:f0:5e  txqueuelen 1000  (Ethernet)
        RX packets 77658  bytes 113705050 (113.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 55011  bytes 4713253 (4.7 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

eno3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.13  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::d6be:d9ff:feef:f060  prefixlen 64  scopeid 0x20<link>
        ether d4:be:d9:ef:f0:60  txqueuelen 1000  (Ethernet)
        RX packets 392  bytes 40823 (40.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 16  bytes 1280 (1.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

eno4: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.14  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::d6be:d9ff:feef:f062  prefixlen 64  scopeid 0x20<link>
        ether d4:be:d9:ef:f0:62  txqueuelen 1000  (Ethernet)
        RX packets 704480  bytes 940864745 (940.8 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 629003  bytes 462200938 (462.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 30982  bytes 415985624 (415.9 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 30982  bytes 415985624 (415.9 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

virbr0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.122.1  netmask 255.255.255.0  broadcast 192.168.122.255
        ether 52:54:00:f8:9c:c8  txqueuelen 1000  (Ethernet)
        RX packets 902  bytes 145902 (145.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1227  bytes 1527966 (1.5 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

vnet0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::fc54:ff:fe21:3361  prefixlen 64  scopeid 0x20<link>
        ether fe:54:00:21:33:61  txqueuelen 1000  (Ethernet)
        RX packets 439  bytes 78613 (78.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 728  bytes 771740 (771.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

root@server:/var/lib/libvirt/boot# 

```

I currently use "eno1" as my ssh logon.

Would like to use 2 others, one for each vm that I plan on running.

How do I go about this? Or is it even worthwhile?

Regards

---

### Post by darkod on 2019-11-03
You can create two bridges. One bridge (for example named br2) will use only eno2. And br3 will use only eno3.

After that when creating the VMs you assign to use br2 or br3 as needed.

But in general seeing that all your cards are in the same network, I don't really see this as useful. It depends on the use but I don't think your VMs could saturate the ethernet NIC if they are on one card. That would be the only reason to separate them I guess.

---

### Post by Heeter on 2019-11-04
Great, Thank you for your opinion. Really appreciate it.

I will keep it at one NIC, your right, doesn't really matter since it all ends up going into the same router.

Regards

---

### Post by TheFu on 2019-11-04
You can use PCI passthru with KVM, if your hardware supports it. It makes the most sense only if the VM will be on a different network or is internet facing.  Having multiple NICs on the same subnet if there isn't switch diversity with failover isn't all that useful.

You can bond multiple interfaces into 1, then add a bridge to that if you need more throughput.  Or get some 10Gbps networking gear.

---

### Post by Heeter on 2019-11-04
Thank you for your response, really appreciate it. I am switching everything to a single NIC bridge

---


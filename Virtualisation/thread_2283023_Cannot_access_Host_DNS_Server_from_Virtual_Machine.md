---
title: "Cannot access Host DNS Server from Virtual Machine"
date: 2015-06-18
forum: Virtualisation
---

### Post by Martin_Gunther on 2015-06-18
Hi all. I have been running a number of virtual hosts on a KVM on Ubuntu 12.04 server, using bridged network (so they are network accessible). This has been working fine, until today, I decided to try out bind/named so that I could more easily reference the machines on the local network.

The host server is a Ubuntu 12.04 server version with all the latest patches, and my network configuration is as follows:

```
br0       Link encap:Ethernet  HWaddr 00:19:99:cb:56:54            inet addr:10.10.20.10  Bcast:10.10.255.255  Mask:255.255.0.0
          inet6 addr: fe80::219:99ff:fecb:5654/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7578 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7587 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:490666 (490.6 KB)  TX bytes:569629 (569.6 KB)


eth0      Link encap:Ethernet  HWaddr 00:19:99:cb:56:54  
          inet6 addr: fe80::219:99ff:fecb:5654/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7925 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7854 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:662305 (662.3 KB)  TX bytes:638285 (638.2 KB)
          Interrupt:20 Memory:f7f00000-f7f20000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2169 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:134846 (134.8 KB)  TX bytes:134846 (134.8 KB)


vnet0     Link encap:Ethernet  HWaddr fe:54:00:69:24:96  
          inet6 addr: fe80::fc54:ff:fe69:2496/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:371 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:30511 (30.5 KB)  TX bytes:37162 (37.1 KB)
```

All the virtual machines get their IP address from the main networks DHCP server. And I have no virtual networks defined. They access the internet fine.

So for example The host (hypervisor) IP address is 10.10.20.10 (as above), a network config for one of the virtual machines is as follows:

```
<interface type='bridge'>
      <mac address='52:54:00:69:24:96'/>
      <source bridge='br0'/>
      <target dev='vnet0'/>
      <model type='virtio'/>
      <alias name='net0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>

```

It works online, and has been assigned 10.10.200.100. The problem is I've set the DNS to 10.10.20.10, and it doesn't resolve, using dig @10.10.20.10 [www.google.co.uk](www.google.co.uk) doesn't work either. dnsmasq is NOT running on the host, and 10.10.20.10 DNS server works from other machines on the network. Also I can connect to port 80, and ssh port from the virtual machine to the hypervisor. Please help!

Regards,

Martin

---

### Post by Martin_Gunther on 2015-06-18
Sorry all. Was actually a firewall rule on the host machine in the end. What a pain! Love KVM :)

---


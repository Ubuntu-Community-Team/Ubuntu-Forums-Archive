---
title: "[virtualbox] Routing Between Two Ubuntu Guests"
date: 2013-06-26
forum: Virtualisation
---

### Post by benynug on 2013-06-26
Greetings,

I hope I put this question in correct forum since I am working with Ubuntu in my VirtualBox. I am new in configuring Virtual Machines (VMs), and I have a problem in routing between two guests with Ubuntu 12.04 run on both.

Here is my system :
My Host : Windows 7 64-bit
VirtualBox version : 4.2.12
All of my 3 guests : Ubuntu 12.04

My VM configuration is as the following :
_VM1 - As a Host 1_
Adapter 1 : NAT
Adapter 2 : Host-Only, the IP address is 192.168.56.101

_VM2 - As a Router_
Adapter 1 : NAT
Adapter 2 : Host-Only, the IP address is 192.168.56.102
Adapter 3 : Host-Only, the IP address is 192.168.194.101

_VM3 - As a Host 2_
Adapter 1 : NAT
Adapter 2 : Host-Only, the IP address is 192.168.194.102

I want it to make it like this : VM1 <---> VM2 <---> VM3.
But the ping result that I got :
from VM1 to VM2 : Success
from VM1 to VM3 : Failed!
from VM2 to VM1 : Success
from VM2 to VM3 : Success
from VM3 to VM1 : Failed!
from VM3 to VM2 : Success

It  seems like the VM2 does not work as a router, it can connect to each  host, but i can not make the hosts connected with each other. Can  someone please help me?
Thank you.

---

### Post by mlu17 on 2013-06-26
Hi,

if I'm not totally wrong to make this happen your VM2 would need to have two NICs. Otherwise it cannot communicate between the two networks.

Regards,
Michael

---

### Post by benynug on 2013-06-26
> **mlu17 said:**
> Hi,

if I'm not totally wrong to make this happen your VM2 would need to have two NICs. Otherwise it cannot communicate between the two networks.

Regards,
Michael

I did, I already added that two interfaces in the VM2, this is the ifconfig of VM2. But still it did not work. Any other suggestion? Thanks

```

eth0      Link encap:Ethernet  HWaddr 08:00:27:46:07:61  
          inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe46:761/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:189 errors:0 dropped:0 overruns:0 frame:0
          TX packets:231 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:136572 (136.5  KB)  TX bytes:24391 (24.3 KB)

eth1      Link encap:Ethernet  HWaddr 08:00:27:5c:e5:a2  
          inet addr:192.168.56.102  Bcast:192.168.56.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe5c:e5a2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15996 (15.9 KB)  TX bytes:11062 (11.0 KB)

eth2       Link encap:Ethernet  HWaddr 08:00:27:67:82:eb  
          inet addr:192.168.194.101  Bcast:192.168.194.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe67:82eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:81 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14697 (14.6 KB)  TX bytes:10527 (10.5 KB)

lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:86 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10202 (10.2 KB)  TX bytes:10202 (10.2 KB)

```

---

### Post by Kujua on 2013-06-26
benynug,

On VM2 did you enable forwarding and setup NAT rules? VM2 will not automatically start routing between VM1 and VM3.

Try this:
[http://how-to.wikia.com/wiki/How_to_set_up_a_NAT_router_on_a_Linux-based_computer](http://how-to.wikia.com/wiki/How_to_set_up_a_NAT_router_on_a_Linux-based_computer)

---

### Post by wildmanne39 on 2013-06-26
Moved to virtualization.

---

### Post by Rebelli0us on 2013-06-26
For VBox Guests to see each other (and your network) set Network to "Bridged Adapter".

---

### Post by markbl on 2013-06-26
This seems a routing question, not specifically anything to do with virtual machines. To ping/route from VM1 to VM3 you need to configure a route on VM1 to 192.168.194.* via adaptor 2, and vice versa for VM3. You also need to enable ip forwarding on VM2 - see Google for that.

---

### Post by benynug on 2013-06-27
> **markbl said:**
> This seems a routing question, not specifically anything to do with virtual machines. To ping/route from VM1 to VM3 you need to configure a route on VM1 to 192.168.194.* via adaptor 2, and vice versa for VM3. You also need to enable ip forwarding on VM2 - see Google for that.

Finally it's working

what I did :
1. enabling ip forwarding on VM2
2. adding default gateway on VM1 and VM3
3. adding route on VM1 to VM2 via adaptor 2, and on VM3 to VM1 via adaptor 2

Thank you all

---


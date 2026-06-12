---
title: "VMWare Server Problem"
date: 2009-12-29
forum: Virtualisation
---

### Post by dvdhaar on 2009-12-29
I've been messing around with VMWare Server just now. Spending quite some time trying to install it, I eventually installed it correctly and created a VM. Now what I want to do is let the VM use my secondary NIC to have it's own IP from my physical router. But I have no idea what I'm doing at the moment. 

I've got two NICs installed eth0 (static ip) and eth2 (dhcp).. So I renamed the eth2 to eth1 in the /etc/udev/rules.d/70-persistent-net.rules file. But this doesn't work, even after restarting the network daemon it stays 'eth2'. 

My VMWare Server configuration looks like this:

```

The following virtual networks have been defined:

. vmnet0 is bridged to eth2
. vmnet1 is a host-only network on private subnet 192.168.150.0.
. vmnet8 is a NAT network on private subnet 192.168.127.0.

```

But now if I 'ifup eth2' I can't access the internet anymore via eth0?!

---

### Post by Hopping_Ubu on 2009-12-29
Although new to Ubuntu, I have worked with VMware quite a bit. I need to ask a question for clarification, are you running VMware server on a Linux box or are you running a virtual instance of Ubuntu on the VMware server that is currently installed on another type of hardware/OS?

That will make it a little clearer.

Thanks,

---

### Post by dvdhaar on 2009-12-29
> **Hopping_Ubu said:**
> Although new to Ubuntu, I have worked with VMware quite a bit. I need to ask a question for clarification, are you running VMware server on a Linux box or are you running a virtual instance of Ubuntu on the VMware server that is currently installed on another type of hardware/OS?

That will make it a little clearer.

Thanks,

I'm running Ubuntu 9.04 (iirc) and on that machine I'm using VMWare Server v1

---

### Post by dvdhaar on 2009-12-29
Ok now I rebooted the machine and apparently the interfacename has been changed to eth1 but I can't seem to get it up and running?! And it seems like it somehow HASN'T changed because the auto complete tab thingy shows eth0 and eth2..

```

daniel@server:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fed4:9c4b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20342 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38222 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2036733 (2.0 MB)  TX bytes:25587941 (25.5 MB)
          Interrupt:252 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15110 (15.1 KB)  TX bytes:15110 (15.1 KB)

pan0      Link encap:Ethernet  HWaddr 
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

daniel@server:~$ sudo ifup eth1
Ignoring unknown interface eth1=eth1.
daniel@server:~$ sudo ifup 
eth0  eth2  lo    
daniel@server:~$ sudo ifup 

```

---

### Post by Hopping_Ubu on 2009-12-30
> **dvdhaar said:**
> Ok now I rebooted the machine and apparently the interfacename has been changed to eth1 but I can't seem to get it up and running?! And it seems like it somehow HASN'T changed because the auto complete tab thingy shows eth0 and eth2..

```

daniel@server:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fed4:9c4b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20342 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38222 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2036733 (2.0 MB)  TX bytes:25587941 (25.5 MB)
          Interrupt:252 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15110 (15.1 KB)  TX bytes:15110 (15.1 KB)

pan0      Link encap:Ethernet  HWaddr 
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

daniel@server:~$ sudo ifup eth1
Ignoring unknown interface eth1=eth1.
daniel@server:~$ sudo ifup 
eth0  eth2  lo    
daniel@server:~$ sudo ifup 

```

What about if you go in and check you network connections? What do you have listed? Do you have eth0 and eth1 or eth0 and eth2? You can always delete eth2 and then add a new network connection while in Ubuntu. Did you look at the VMware side? What network adapters does it have?    :confused:

---

### Post by dvdhaar on 2009-12-30
> **Hopping_Ubu said:**
> What about if you go in and check you network connections? What do you have listed? Do you have eth0 and eth1 or eth0 and eth2? You can always delete eth2 and then add a new network connection while in Ubuntu. Did you look at the VMware side? What network adapters does it have?    :confused:

Well VMWare currently has this configuration:

```

The following virtual networks have been defined:

. vmnet0 is bridged to eth2
. vmnet1 is a host-only network on private subnet 192.168.150.0.
. vmnet8 is a NAT network on private subnet 192.168.127.0.

```

Which I edited using the vmware-config.pl iirc.

```

daniel@server:~$ cat /etc/udev/rules.d/70-persistent-net.rules 
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

#The order it used to be:
#eth1
#eth0
#eth2

# PCI device 0x1106:0x3106 (via-rhine)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:02:44:91:49:5c", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1f:d0:d4:9c:4b", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8169 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:22:f7:11:75:4f", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


```

The via-rhine thing is a card I installed one time but I removed it long ago. One of the two is my on-board adapter and the other one is a PCI card. eth0 must be my on-board because I've set it to static 192.168.1.100..

---


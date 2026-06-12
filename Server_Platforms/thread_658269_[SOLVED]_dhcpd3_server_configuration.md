---
title: "[SOLVED] dhcpd3 server configuration"
date: 2008-01-04
forum: Server Platforms
---

### Post by bindatype on 2008-01-04
I need help setting up my dhcpd3 server. My dhcpd.conf looks like this 
```

subnet 192.168.1.0 netmask 255.255.255.0 {
        option routers                  192.168.1.254;
        option subnet-mask              255.255.255.0;

        option domain-name              "example.com";
        option domain-name-servers       192.168.1.1;

        option time-offset              -18000;     # Eastern Standard Time

        range 192.168.1.10 192.168.1.100;
}
default-lease-time 259200;
max-lease-time 604800;
 
} 


```

and I am trying to configure it to listen on eth1 so I set this flag in /etc/default/dhcp3-server 
```

INTERFACES="eth1"

```

My /etc/network/interfaces file looks like this

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp


```

The error message that I get is this 

```

Wrote 0 leases to leases file.

No subnet declaration for eth1 (169.254.1.175).
** Ignoring requests on eth1.  If this is not what
   you want, please write a subnet declaration
   in your dhcpd.conf file for the network segment
   to which interface eth1 is attached. **


Not configured to listen on any interfaces!


```

How do I get this sorted out?

---

### Post by reckless2k2 on 2008-01-04
you don't have an eth1

you only have an eth0

you understand? i think that is why you are getting an internal address on eth1 because it doesn't exist.

---

### Post by bindatype on 2008-01-04
I do have eth1, its just not in the interfaces file. An ifconfig gives this

```

eth1      Link encap:Ethernet  HWaddr 00:12:17:5C:0A:0A  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:57456 (56.1 KB)  TX bytes:14289 (13.9 KB)
          Interrupt:21 Base address:0x2400 

eth1:avah Link encap:Ethernet  HWaddr 00:12:17:5C:0A:0A  
          inet addr:169.254.1.175  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0x2400 


```

---

### Post by reckless2k2 on 2008-01-04
i could be wrong but how many NICs do you have plugged into your bus? Do you have 2 different ethernet cables going into your machine?

---

### Post by bindatype on 2008-01-04
Yes, I have two cables and two NICs

---

### Post by bindatype on 2008-01-04
THis is the full output from ifconfig -a

```

eth0      Link encap:Ethernet  HWaddr 00:40:2B:4D:55:04  
          inet addr:128.164.237.70  Bcast:128.164.239.255  Mask:255.255.252.0
          inet6 addr: fe80::240:2bff:fe4d:5504/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10509 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1702 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2099639 (2.0 MB)  TX bytes:296067 (289.1 KB)
          Interrupt:20 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:12:17:5C:0A:0A  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3420 (3.3 KB)  TX bytes:4079 (3.9 KB)
          Interrupt:21 Base address:0x2400 

eth1:avah Link encap:Ethernet  HWaddr 00:12:17:5C:0A:0A  
          inet addr:169.254.1.175  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0x2400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

---

### Post by reckless2k2 on 2008-01-04
well then there's a definite issue because it is not being recognized. try enabling it in the network manager so then you can get something going. it "needs" to show up in the interfaces file. you might want to try these 2 commands and check out the output:

```
lspci
```

```
dmesg
```

you'll be looking for references to the 2nd NIC that is not showing up and it might tell you why.

---

### Post by reckless2k2 on 2008-01-04
the NIC "serving" to your network will have to be static as well.

---

### Post by herbie_popnecker on 2008-01-05
Add
```

auto eth1
iface eth1 inet static
        address 192.168.1.254
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255

```
to your /etc/network/interfaces

to configure your eth1 to 192.168.1.254
then
sudo /etc/init.d/networking restart
sudo /etc/init.d/dchp3-server start

---

### Post by bindatype on 2008-01-06
Thanks, that was exactly what I needed.

---


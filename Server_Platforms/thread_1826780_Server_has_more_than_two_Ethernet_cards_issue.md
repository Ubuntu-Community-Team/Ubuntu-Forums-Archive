---
title: "Server has more than two Ethernet cards issue"
date: 2011-08-17
forum: Server Platforms
---

### Post by A9tm on 2011-08-17
Hi there,

I'm planning to setup a Ubuntu server to work as a transparent proxy (Squid). 
My diagram:

```

                       10.0.0.2
               +----+     +--------+     +-----+      |
INTERNET ------| GW |-----| Ubuntu |-----| SW  |------| LAN 10.0.0.0/8
               +----+     +--------+     +-----+      |
              10.0.0.1          10.0.0.3                 
Visions: 
- GW is also DHCP server, Ubuntu is DHCP relay agent
- Squid will forward every HTTP requests from LAN to GW
``` I've installed Ubuntu server 11.04 to HP xw4100 as well. HP server was installed two NICs: 

```
octopus@octopus:~$ sudo lspci | grep Ethernet
[sudo] password for octopus:
05:02.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5782 Gigabit Ethernet (rev 03)
05:09.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 64)

```I chosed 3Com NIC is primary to connect to Internet, and it's eth0 interface and put static IP addresses looks like above.

Problem is:
- From Out-side: I set up one PC that connected to GW then doing scan IPs, I found two IP address: 10.0.0.2 and 10.0.0.3 have the same MAC address: 
```
10.2.176.11        00-11-11-11-11-11    3COM CORPORATION    
10.2.176.12        00-11-11-11-11-11    3COM CORPORATION    
```But it's different on server:

```
octopus@octopus:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00-11-11-11-11-11
          inet addr:10.0.0.2  Bcast:10.255.255.255  Mask:255.0.0.0

eth1      Link encap:Ethernet  HWaddr 00-22-22-22-22-22
          inet addr:10.0.0.3  Bcast:10.255.255.255  Mask:255.0.0.0
```- I setup one more PC inside LAN which has IP 10.0.0.4/8, but it's can't see 10.0.0.3 with "Request timed out" responses.

Then now, I'm stucking at this point and need some solutions from you, I greatly appreciate.

Thanks,

---

### Post by hawk2010 on 2011-08-17
I have gone down this path which takes  along time. I finally found the best. which is Smoothwall . config is pretty straight forward and it does the job very well. Smoothwall3 is compatible with most of the ethernet cards.

> **A9tm said:**
> Hi there,

I'm planning to setup a Ubuntu server to work as a transparent proxy (Squid). 
My diagram:

```

                       10.0.0.2
               +----+     +--------+     +-----+      |
INTERNET ------| GW |-----| Ubuntu |-----| SW  |------| LAN 10.0.0.0/8
               +----+     +--------+     +-----+      |
              10.0.0.1          10.0.0.3                 
Visions: 
- GW is also DHCP server, Ubuntu is DHCP relay agent
- Squid will forward every HTTP requests from LAN to GW
``` I've installed Ubuntu server 11.04 to HP xw4100 as well. HP server was installed two NICs: 

```
octopus@octopus:~$ sudo lspci | grep Ethernet
[sudo] password for octopus:
05:02.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5782 Gigabit Ethernet (rev 03)
05:09.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 64)

```I chosed 3Com NIC is primary to connect to Internet, and it's eth0 interface and put static IP addresses looks like above.

Problem is:
- From Out-side: I set up one PC that connected to GW then doing scan IPs, I found two IP address: 10.0.0.2 and 10.0.0.3 have the same MAC address: 
```
10.2.176.11        00-11-11-11-11-11    3COM CORPORATION    
10.2.176.12        00-11-11-11-11-11    3COM CORPORATION    
```But it's different on server:

```
octopus@octopus:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00-11-11-11-11-11
          inet addr:10.0.0.2  Bcast:10.255.255.255  Mask:255.0.0.0

eth1      Link encap:Ethernet  HWaddr 00-22-22-22-22-22
          inet addr:10.0.0.3  Bcast:10.255.255.255  Mask:255.0.0.0
```- I setup one more PC inside LAN which has IP 10.0.0.4/8, but it's can't see 10.0.0.3 with "Request timed out" responses.

Then now, I'm stucking at this point and need some solutions from you, I greatly appreciate.

Thanks,

---

### Post by adoniasv on 2011-10-22
Try this

[http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/](http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/)

or

[http://www.linuxhorizon.ro/iproute2.html](http://www.linuxhorizon.ro/iproute2.html)

Wks 4 me!

@adoniasv

---


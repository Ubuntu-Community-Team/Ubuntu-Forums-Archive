---
title: "Internet issues after setting a static IP"
date: 2007-02-22
forum: Server Platforms
---

### Post by Macskeeball on 2007-02-22
I've got three computers on my home LAN, one of which is a headless PC running Ubuntu Server 6.10. The router is a Linksys WRT54G, and the PC has a wired connection to the router. I need to set a static IP on the server so that I can properly do port-forwarding, but when I reboot the server after doing that, the PC server is no longer able to access servers out on the Internet (that is, outside my LAN) by domain name. It is, however, able to access them via their IP addresses, and it has no issues with the computers inside my LAN.

The router's local IP address is 192.168.1.1, and the local IP I want to statically set for the PC is 192.168.1.2. Yes, that IP is available on my LAN.

Below is the change I made to /etc/network/interfaces, based on the [Ubuntu Server Guide](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/network-configuration.html) (Ethernet section)
```
# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1
```

I also made the following changes to /etc/resolv.conf, again based on the [Ubuntu Server Guide](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/network-configuration.html) (Ethernet section).
```

nameserver 192.168.1.1
nameserver 68.94.156.1
nameserver 68.94.157.1

```
The first name server is my router, and the next two are the nameserver IPs provided by my ISP. I'm not sure what domain to put for search; it's just a typical home LAN on a typical home ADSL line. Perhaps my leaving that out is the cause of the problem?

Upon rebooting, this is the output of "ifconfig eth0"
```
eth0      Link encap:Ethernet  HWaddr 00:12:17:5C:F5:21  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:17ff:fe5c:f521/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:385 errors:0 dropped:0 overruns:0 frame:0
          TX packets:344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:36579 (35.7 KiB)  TX bytes:50005 (48.8 KiB)
          Interrupt:10 Base address:0x6c00 
```

Any help with this would be greatly appreciated, because my server is of limited usefulness without both port forwarding AND the ability to connect to external servers via their domain names.

---

### Post by Macskeeball on 2007-02-22
Never mind. A couple of reboots later, it works. DynDNS also had an outdated record of my external IP address which i updated, but I don't see how that would have made a difference considering I had been testing the connection from the PC to the outside world (using w3m over ssh), and not from the outside worl to the PC. At least it all works now, at last.

---


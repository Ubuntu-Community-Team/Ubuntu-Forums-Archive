---
title: "Networking problem"
date: 2006-03-12
forum: Server Platforms
---

### Post by secici on 2006-03-12
Following lines are from my /etc/network/interfaces

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp


After startup my settings are normal. I can get IP from ADSL router via Ethernet 100BaseTX eth0.

But when I run dhclient eth1 (which is Intel Pro wireless) gets the IP 192.168.1.100 which is a configuration in my ADSL Router (static DHCP). After that I become unable to ping localhost/127.0.0.1 which makes myself impossible to test apache and web applications.

What may be the reason?

---

### Post by alamba on 2006-03-12
Post your /etc/hosts post running dhclient. That may be an issue though I've really never seen this error myself. Must be a rare case of localloop failing.

A

---

### Post by amohanty on 2006-03-12
I am assuming you have installed the wireless-tools package. Try adding the following to you interfaces:
>  
map eth1

iface eth1 inet dhcp
# wireless-* options are implemented by the wireless-tools package
wireless-mode managed
wireless-essid any

auto eth0
auto eth1

The do a :
> /etc/init.d/networkign restart

If you still cant ping your local loopback, please post the output of:
> host -a localhost and


AM

---

### Post by secici on 2006-03-13
Wireless-tools is installed. I modified my interfaces as they are on your directions. Here is the last state of the case:

> root@ubuntum5n:/home/secici# dhclient
There is already a pid file /var/run/dhclient.pid with pid 19090
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on   LPF/sit0/
Listening on LPF/eth0/00:0e:a6:bf:5e:8e
Sending on   LPF/eth0/00:0e:a6:bf:5e:8e
Listening on LPF/lo/
Sending on   LPF/lo/
Listening on LPF/eth1/00:0c:f1:30:76:26
Sending on   LPF/eth1/00:0c:f1:30:76:26
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 8
DHCPACK from 192.168.1.1
bound to 192.168.1.102 -- renewal in 36794 seconds.
root@ubuntum5n:/home/secici# ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.

--- 127.0.0.1 ping statistics ---
8 packets transmitted, 0 received, 100% packet loss, time 6998ms

root@ubuntum5n:/home/secici# host -a localhost
Trying "localhost"
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 18276
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 0, ADDITIONAL: 1

;; QUESTION SECTION:
;localhost.                     IN      ANY

;; ANSWER SECTION:
localhost.              604800  IN      SOA     localhost. root.localhost. 1 604 800 86400 2419200 604800
localhost.              604800  IN      NS      localhost.
localhost.              604800  IN      A       127.0.0.1

;; ADDITIONAL SECTION:
localhost.              604800  IN      A       127.0.0.1

Received 114 bytes from 195.175.37.14#53 in 64 ms


.......................

---

### Post by amohanty on 2006-03-14
Everything looks good. 
Do you still have problems then? 
Also can you post the output of ifconfig?

AM

---

### Post by secici on 2006-03-14
My problem points to a bug, here is the link:

[https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/13947](https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/13947)

I can deal with it by using ifdown lo ifup lo but system-tools-backends 1.4.0 is already installed on my system and my ubuntu system is up-to-date now.

Is there a bug fix actually?

---


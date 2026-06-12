---
title: "DHCP Server not starting on boot"
date: 2010-11-11
forum: Server Platforms
---

### Post by Z.K. on 2010-11-11
When my machine boots I get an error that says the dhcp server failed to start and it lists a subnet 0.0.0.0 even though I changed it in the dhcpd.conf file.  This used to work, but now suddenly I have to manually start it after booting.  I looked at the permissions of the dhcp3-server file and it looks like this.

-rwxr-xr-x 1 root root 2981 2010-04-01 10:46 dhcp3-server

I am wondering if I need to change the permissions in order for it to start up during boot since I have to start it with the sudo command.  

Once I started it manually, it works.

---

### Post by WinstonChurchill on 2010-11-11
> **Z.K. said:**
> When my machine boots I get an error that says the dhcp server failed to start and it lists a subnet 0.0.0.0 even though I changed it in the dhcpd.conf file.  This used to work, but now suddenly I have to manually start it after booting.  I looked at the permissions of the dhcp3-server file and it looks like this.

-rwxr-xr-x 1 root root 2981 2010-04-01 10:46 dhcp3-server

I am wondering if I need to change the permissions in order for it to start up during boot since I have to start it with the sudo command.  

Once I started it manually, it works.

I've had similar issues (although only with desktop installations), and I think this is due to the network device not being brought up by the time dhcp3-server is started, but I'm not entirely sure. It could also be udev not renaming interfaces fast enough - do you have multiple NIC's in your machine? Wireless cards, in my experience, seem to take longer to bring up - is this wifi?

---

### Post by Vegan on 2010-11-11
I use a Linksys box between my LAN and the internet. It provides DHCP services reliably.

It has served me well over the years since I bought it.

---

### Post by Z.K. on 2010-11-12
> **WinstonChurchill said:**
> I've had similar issues (although only with desktop installations), and I think this is due to the network device not being brought up by the time dhcp3-server is started, but I'm not entirely sure. It could also be udev not renaming interfaces fast enough - do you have multiple NIC's in your machine? Wireless cards, in my experience, seem to take longer to bring up - is this wifi?


No, I have only a single network card on my server and I am not using wireless.

---

### Post by Z.K. on 2010-11-12
> **Vegan said:**
> I use a Linksys box between my LAN and the internet. It provides DHCP services reliably.

It has served me well over the years since I bought it.

That is not the issue.  I have a router with a built in dhcp server that works just fine.  So, does my server if I start it manually.  As I said before I want the dhcp server to start when I boot the server.  

Granted I could use the router, but I don't want to.  This is mainly a knowledge gaining exercise and I want to setup a network boot system using dhcp and tftp servers on my server machine.

---

### Post by WinstonChurchill on 2010-11-12
Run this command:
```
cat /var/log/kern.log | grep eth0
```... and look for the last entry that looks like this:
```
Nov 12 11:28:16 DesktopBox kernel: [   12.892630] r8169 0000:03:00.0: eth0: link up

```Then compare that with the time you're seeing next to the error message for the DHCP server - is it earlier or later then when the kernel says the link is up? 

If not, than this isn't the problem...

---

### Post by Z.K. on 2010-11-13
> **WinstonChurchill said:**
> Run this command:
```
cat /var/log/kern.log | grep eth0
```... and look for the last entry that looks like this:
```
Nov 12 11:28:16 DesktopBox kernel: [   12.892630] r8169 0000:03:00.0: eth0: link up

```Then compare that with the time you're seeing next to the error message for the DHCP server - is it earlier or later then when the kernel says the link is up? 

If not, than this isn't the problem...

Well, this is what I get though I am not exactly sure what that is telling me other than the time the eth0 comes up.

Nov 13 16:52:26 server kernel: [   20.343828] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1


is it earlier or later then when the kernel says the link is up? 
-- I am not sure how to tell.

oh, this is what is in the syslog

```

Nov 13 16:52:24 server kernel: [   17.106184] type=1505 audit(1289695943.1            37:3):  operation="profile_load" pid=618 name="/usr/lib/NetworkManager/nm-dhcp-c            lient.action"
Nov 13 16:52:24 server kernel: [   18.370549] type=1505 audit(1289695944.4            01:6):  operation="profile_replace" pid=731 name="/usr/lib/NetworkManager/nm-dhc            p-client.action"
Nov 13 16:52:24 server kernel: [   18.454901] type=1505 audit(1289695944.4            85:10):  operation="profile_load" pid=736 name="/usr/sbin/dhcpd3"
Nov 13 16:52:26 server dhcpd: Wrote 8 leases to leases file.
Nov 13 16:52:26 server dhcpd:
Nov 13 16:52:26 server dhcpd: No subnet declaration for eth0 (0.0.0.0).
Nov 13 16:52:26 server dhcpd: ** Ignoring requests on eth0.  If this is no            t what
Nov 13 16:52:26 server dhcpd:    you want, please write a subnet declarati            on
Nov 13 16:52:26 server dhcpd:    in your dhcpd.conf file for the network s            egment
Nov 13 16:52:26 server dhcpd:    to which interface eth0 is attached. **
Nov 13 16:52:26 server dhcpd:
Nov 13 16:52:26 server dhcpd:
Nov 13 16:52:26 server dhcpd: Not configured to listen on any interfaces!


```


The thing is, it is incorrect.  I do have the Interfaces file set to eth0 and the the dhcpd.conf file is configured properly.

:confused:

Interfaces:
```


#GNU nano 2.2.2                  File: interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

#The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
        address 192.168.0.2
        netmask 255.255.255.0
        gateway 192.168.0.10
                    

```

dhcpd.conf:
```

#GNU nano 2.2.2                  File: dhcpd.conf

option domain-name-servers 68.238.64.14, 68.238.128.14, 192.168.1.1;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.

default-lease-time 86400;
max-lease-time 604800;
authoritative;

subnet 192.168.0.0 netmask 255.255.255.0 {
        range 192.168.0.100 192.168.0.200;
        filename "pxelinux.0";
        option subnet-mask 255.255.255.0;
        option broadcast-address 192.168.0.255;
        option routers 192.168.0.10;
}


```

---

### Post by WinstonChurchill on 2010-11-14
Ok, I think I've figured out your problem:

Look at the file /etc/default/dhcp3-server:
```

# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#    Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="**eth0**"

```Do you have 'eth0' listed there under interfaces?

---

### Post by Z.K. on 2010-11-14
> **WinstonChurchill said:**
> Ok, I think I've figured out your problem:

Look at the file /etc/default/dhcp3-server:
```

# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#    Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="**eth0**"

```Do you have 'eth0' listed there under interfaces?


Actually,I do.

/etc/default/dhcp3-server:
```

  GNU nano 2.2.2             File: dhcp3-server                       Modified

INTERFACES="eth0"

```

---

### Post by WinstonChurchill on 2010-11-14
> **Z.K. said:**
> Actually,I do.
Well, crap - nothing can be easy, eh?

What I was getting at earlier: Your logs show that the link was brought up and dhcpd started at 16:52:26 - unfortunately, we get the decimals for the kernel log entry, but not for the dhcp one... so my original idea might still the problem. Maybe give this a shot: add the following line at the beginning of /etc/init.d/dhcp3-server:
```

#!/bin/sh
**sleep 5**
```The init.d scripts are executed sequentially, and not forked, so your system will take 5 seconds longer to boot, but since it's a server it won't really matter. Maybe that will let the kernel bring up the interface before dhcpd tries to run on it. If not, just get rid of it.

---

### Post by Z.K. on 2010-11-14
> **WinstonChurchill said:**
> Well, crap - nothing can be easy, eh?

What I was getting at earlier: Your logs show that the link was brought up and dhcpd started at 16:52:26 - unfortunately, we get the decimals for the kernel log entry, but not for the dhcp one... so my original idea might still the problem. Maybe give this a shot: add the following line at the beginning of /etc/init.d/dhcp3-server:
```

#!/bin/sh
**sleep 5**
```The init.d scripts are executed sequentially, and not forked, so your system will take 5 seconds longer to boot, but since it's a server it won't really matter. Maybe that will let the kernel bring up the interface before dhcpd tries to run on it. If not, just get rid of it.

Thanks a lot, that worked.  Now if I could only get the tftp server to work.

:P

---


---
title: "Can't ping Ubuntu server from OS X"
date: 2007-07-10
forum: Server Platforms
---

### Post by kory on 2007-07-10
Howdy all.  I installed Ubuntu 6.07 on an old Dell box and added it to our DNS server (Win2003 on our domain controller) with its static IP, of course.  I'm working with OCS Inventory to track our PCs and Macs for licensing and asset management purposes.  

I can successfully ping other addresses from the server except for a Mac OS X client (running 10.3.9) nor can the Mac workstation ping the Ubuntu server.  The Mac client is on a slightly different subnet and obtains its IP address via DHCP from the XServe it connects to (using Netboot here).  

I'm going to take a shot in the dark but might anyone have any suggestions for me for getting our Mac clients to "see" the Ubuntu server?  All machines are on a 10.x.x.x. IP range with a netmask of 255.248.0.0.  I'm wondering if it's a firewall issue?

Thanks much, in advance!

Regards,
Kory

---

### Post by koenn on 2007-07-10
sounds like the Mac is blocking  ICMP echo-requests/echo-replies ("ping"). Could be a firewall on the Mac or on a router to the 'slightly different' subnet. I think there's also some kernel option to ignore ICMP. 

Don't know much about Mac, but try these linux commands ans see if it tells you anything :
```
iptables -L -v 
```
could reveil firewall rules on the machine itself. 

If ```

cat  /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts
cat  /proc/sys/net/ipv4/icmp_echo_ignore_all
``` return 1, the system is configured to ignore pings.

---

### Post by kory on 2007-07-11
Hi, koenn.  Thanks much for your reply.  I thought it might have been a ping issue too but I can ping other servers and workstations on that subnet from the Mac.  It doesn't like the "iptables" command.  

I can also ping the Ubuntu server from other workstations.  If I assign a static IP to the Mac, I can ping the server but that ultimately won't be ideal since the Macs are getting their IPs via DHCP from an XServe.

Regards,
Kory

---

### Post by koenn on 2007-07-11
Hi.
This doesn't make sense. Ping is not aware of whether an address was assigned by dhcp or manually. 
There's probably something yopu forgot to mention. are you pinging hostnames in stead of IP addresses ? Is there a chance you pinged an old address while the mac got a new one from dhcp ?

---

### Post by kory on 2007-07-12
:::shaking my head in shame::: :)

Apparently, when I assigned the gateway to the server's network interface, I gave it the wrong one.  Changed it to the correct one and can now ping from any workstation on the network.

So, I'm good to go.

Thx for your follow ups, koenn!

Regards,
Kory

---

### Post by koenn on 2007-07-12
:)

---


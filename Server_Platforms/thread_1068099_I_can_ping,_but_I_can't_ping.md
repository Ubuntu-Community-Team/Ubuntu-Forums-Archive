---
title: "I can ping, but I can't ping"
date: 2009-02-12
forum: Server Platforms
---

### Post by Go_Big_Blue on 2009-02-12
I have two machines setup for a LAN (or trying to be setup this way).  I have configured Server1 as the DHCP/DNS Server using Ubuntu 8.04 Server Edition.  It has two network cards, eth1 (connects to Linksys Router which is connected to my DSL modem) and eth0 (connected to a Linksys 8 port switch).  I have given both eth1 and eth0 static IP addresses in /etc/network/interfaces as follows:
```
auto lo
iface lo inet loopback
# The primary network interface
auto eth1
iface eth1 inet static
      address 192.168.1.42
      netmask 255.255.255.0
      network 192.168.1.0
      broadcast 255.255.255.0
      gateway 192.168.1.1
# The secondary network interface for the LAN
auto eth0
iface eth0 inet static
      address 10.4.16.42
      netmask 255.255.255.0
      network 10.4.16.0
      broadcast 10.4.16.255

```

The second machine is setup using Ubuntu 8.04 Server Ed. as well, but only as a file server.  eth1 is configured on the second machine as
```
auto eth1
iface eth1 inet static
      address 10.4.16.46
      netmask 255.255.255.0
      network 10.4.16.0
      broadcast 10.4.16.255

``` and it is connected to the Linksys switch (which is connected to Server1).

I have been following the tutorial on HowToForge.com on setting up NAT Gateway, Iptables, Port Forwarding (link is [http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server](http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server)), but now I am banging my head against a wall.

The 1st server can ping the internet with no problems.  The 1st server can ping the file server with no problems. The file server can ping the 1st server with no problems. BUT the file server cannot ping the internet.  This is what I get when I try to ping yahoo.com or ubuntu.com from the file server:
```
~#ping yahoo.com
ping: unknown host yahoo.com
~#ping ubuntu.com
ping:unknown host ubuntu.com

```
This is making me go crazy!! ](*,)

Any help would be greatly appreciated.

---

### Post by lykwydchykyn on 2009-02-12
DNS resolution is not working on your file server.  What is in /etc/resolv.conf on the file server?

---

### Post by Go_Big_Blue on 2009-02-12
```
~# cat /etc/resolv.conf
search AOP.lan
nameserver 10.4.16.42
nameserver 205.152.37.23
```

10.4.16.42 is the 1st server (AOP.lan)
205.152.37.23 is the 1st DNS of my ISP (Bellsouth.net)

---

### Post by lykwydchykyn on 2009-02-12
On the file server, what output do you get from this command:
```

host yahoo.com 10.4.16.42

```

Do you have other machines behind the gateway server?  How are they working?

Running a firewall on the gateway server (well, obviously you have some iptables rules, but are you blocking any ports?).

Run this on the gateway machine and post the output:
```

sudo iptables -L

```

---

### Post by windependence on 2009-02-12
Also, he may want to specify a default gateway for eth1. It cant get out if it doesn't know how.

You may want to add an external DNS server in your resolv.conf just in case there is a problem with your internal DNS. There is really no reason to run DNS on your LAN unless you have quite a few machines.

-Tim

---

### Post by Go_Big_Blue on 2009-02-12
> **lykwydchykyn said:**
> On the file server, what output do you get from this command:
```

host yahoo.com 10.4.16.42

```


This is what it returns:
```
~# host yahoo.com 10.4.16.42
;; connection timed out; no servers could be reached
```


> **lykwydchykyn said:**
> Do you have other machines behind the gateway server?  How are they working?

Not yet. I didn't want to put any other machines behind the gateway until I can at least get the file server to ping the internet.  Then any client computers I put behind the gateway server should be able to get to the internet fairly quickly and easily.

> **lykwydchykyn said:**
> Running a firewall on the gateway server (well, obviously you have some iptables rules, but are you blocking any ports?).

Run this on the gateway machine and post the output:
```

sudo iptables -L

```

From the gateway machine, I receive the following:
```
~# sudo iptables -L
Chain    INPUT (policy ACCEPT)
target   prot opt source      destination

Chain    FORWARD (policy ACCEPT)
target   prot opt source      destination

Chain    OUTPUT (policy ACCEPT)
target   prot opt source      destination
```

---

### Post by Go_Big_Blue on 2009-02-12
> **windependence said:**
> Also, he may want to specify a default gateway for eth1. It cant get out if it doesn't know how.

Do you mean to specify a default gateway for eth1 of the file server?

> **windependence said:**
> You may want to add an external DNS server in your resolv.conf just in case there is a problem with your internal DNS. There is really no reason to run DNS on your LAN unless you have quite a few machines.

-Tim

The contents of the /etc/resolv.conf file were listed above.  The 205.152.37.23 nameserver is the primary DNS of my isp. 

WRT to running a DNS - there will be approximately 8-10 machines on the server (depending on the # of laptops that get plugged in on a given day).

---

### Post by Go_Big_Blue on 2009-02-12
> **lykwydchykyn said:**
> On the file server, what output do you get from this command:
```

host yahoo.com 10.4.16.42

```

In between when I posted my last response to your statement, I realized, that I had plugged the ethernet cable to my Linksys router (not the switch) to do an apt-get update && apt-get upgrade to see if that helped the situation (which it had not).  At any rate, I plugged it back into the switch and ran the command you suggested, and it returned the following:
```

~# host yahoo.com 10.4.16.42
Using domain server: 
Name: 10.4.16.42
Address: 10.4.16.42#53
Aliases:

yahoo.com has address 68.180.206.184
yahoo.com has address 206.190.60.37
yahoo.com mail is handled by 1 c.mx.mail.yahoo.com
yahoo.com mail is handled by 1 d.mx.mail.yahoo.com
yahoo.com mail is handled by 1 e.mx.mail.yahoo.com
yahoo.com mail is handled by 1 e.mx.mail.yahoo.com
yahoo.com mail is handled by 1 f.mx.mail.yahoo.com
yahoo.com mail is handled by 1 g.mx.mail.yahoo.com
yahoo.com mail is handled by 1 a.mx.mail.yahoo.com
yahoo.com mail is handled by 1 b.mx.mail.yahoo.com

```

I hope this means that I am making progress, because I really am tired of banging my head against the wall trying to figure this out.
Thanks for the help.

---

### Post by Go_Big_Blue on 2009-02-12
Hello!?!? Anybody out there?  Really could use some help here.

---

### Post by lykwydchykyn on 2009-02-12
Ok, you have no firewall rules on your gateway machine.  So it is not doing any routing, and not being a gateway.  Basically, two NICs doesn't make it a gateway, you have to have some routing rules set up to pass packets from one to the other.  At least, that's my understanding.

I am *really* not very good at the whole gateway thing to be honest; I set it up once on a box at work by following a howto, and couldn't do it again without following one.

You may want to check out this thread: [http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)

---

### Post by Go_Big_Blue on 2009-02-13
Okay - followed the tutorial.  I would love to say that it works like a champ, but unfortunately it does not.  This is what I have so far:
- On the server/gateway
```
 iptables -L
Chain      Input    (policy ACCEPT)
target     prot opt source          destination

Chain      FORWARD  (policy DROP)
target     prot opt source          destination
ACCEPT     all -- anywhere          anywhere       state RELATED,ESTABLISHED
ACCEPT     all -- anywhere          anywhere
LOG        all -- anywhere          anywhere       LOG level warning

Chain      OUTPUT   (policy ACCEPT)
target     prot opt source          destination

~# ping 10.4.16.46
64 bytes from 10,4,16,46: icmp_seq=1 ttl=64 time=0.133ms
...
3 packets transmitted, 3 received, 0% packet loss, time 2000ms 
```

So the gateway computer can ping the file server computer through the switch.
The file server computer can ping the gateway computer with no problems. But when I go to ping yahoo.com from the file server computer, this is the response I receive:
```
~# ping yahoo.com
connect: Network is unreachable

~# host yahoo.com 10.4.16.42
Using domain server: 
Name: 10.4.16.42
Address: 10.4.16.42#53
Aliases:

yahoo.com has address 68.180.206.184
yahoo.com has address 206.190.60.37
yahoo.com mail is handled by 1 c.mx.mail.yahoo.com
yahoo.com mail is handled by 1 d.mx.mail.yahoo.com
yahoo.com mail is handled by 1 e.mx.mail.yahoo.com
yahoo.com mail is handled by 1 e.mx.mail.yahoo.com
yahoo.com mail is handled by 1 f.mx.mail.yahoo.com
yahoo.com mail is handled by 1 g.mx.mail.yahoo.com
yahoo.com mail is handled by 1 a.mx.mail.yahoo.com
yahoo.com mail is handled by 1 b.mx.mail.yahoo.com 
```

Any ideas?

---

### Post by lykwydchykyn on 2009-02-13
post the output of route?  You're at least getting DNS resolution at this point, that's an improvement.

---

### Post by Go_Big_Blue on 2009-02-13
> **lykwydchykyn said:**
> post the output of route?  You're at least getting DNS resolution at this point, that's an improvement.

since I'm a little bit of a noob, I presumed you meant that I just needed to type "route" at the command prompt on the file server.  This is what I received:
```
~# route
Kernel IP routing table
Destination    Gateway     Genmask         Flags Metric Ref     Use Iface
10.4.16.0      *           255.255.255.0   U     0      0         0 eth1

```

---

### Post by lykwydchykyn on 2009-02-13
Yeah, sorry; I'm getting a bit sloppy in my posts.

I think the problem is that you don't have the gateway set on the file server.  Edit the /etc/network/interfaces file on the file server and add this line to the eth1 config:
```

gateway 10.4.16.42

```

Then restart networking with this command:
```

/etc/init.d/networking restart

```
(on the file server, that is).

See if that gets you sorted out.

---

### Post by Go_Big_Blue on 2009-02-13
Thought it might, but when I did the /etc/init.d/networking restart, it returned the following:
```
~# /etc/init.d/networking restart
* Reconfiguring network interfaces...
SIOCDELRT: No such process
                                           [OK]

```

So I changed your suggestion from 10.4.16.42 to 10.4.16.1.  Then it restarted networking without any errors.  Now I can run the ping command, but the response that I get back is 
```
~# ping yahoo.com
PING yahoo.com (68.180.206.184) 56(84) bytes of data.
From 10.4.16.46 icmp_seq=1 Destination Host Unreachable
From 10.4.16.46 icmp_seq=2 Destination Host Unreachable
From 10.4.16.46 icmp_seq=1 Destination Host Unreachable

--- yahoo.com ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 51009ms, pipe 3
```

---

### Post by Go_Big_Blue on 2009-02-13
Since I feel I am making progress, I went and checked the /var/log/syslog on the gateway computer (I rebooted it after my last post).  I noticed the following line, but not sure if this might be my problem or not.
```

Feb 13 10:22:57 AOPserver1 dhcpd: Wrote 1 leases to leases file.
Feb 13 10:22:57 AOPserver1 dhcpd:
Feb 13 10:22:57 AOPserver1 dhcpd: No submet declaration for eth1 (192.168.1.4).
Feb 13 10:22:57 AOPserver1 dhcpd: ** Ignoring requests on eth1. If this is not what
Feb 13 10:22:57 AOPserver1 dhcpd: you want, please write a subnet declaration
Feb 13 10:22:57 AOPserver1 dhcpd: in your dhcpd.conf file for the network segment. Feb 13 10:22:57 AOPserver1 dhcpd: to which interface eth1 is attached. ** 
```

Any thoughts?

---

### Post by Go_Big_Blue on 2009-02-13
Problem solved.  I downloaded and installed pfSense and FreeBSD.  It walks you through setup with a quick webGUI and everything now works.  Unfortunately, I no longer have Ubuntu 8.04 Server on the gateway computer.  It is still on the file server computer with eBox.

---

### Post by lykwydchykyn on 2009-02-13
The shame of it is, we were about "this close" to fixing this. You should have left the gateway where it was, the "SIOCDELRT: No such process" is a meaningless error, AFAIK.

Oh well, glad you got something working anyway.

---


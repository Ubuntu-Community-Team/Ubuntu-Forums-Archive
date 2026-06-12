---
title: "Ubuntu Router/DHCP Setup"
date: 2006-08-10
forum: Server Platforms
---

### Post by TheGamingPit on 2006-08-10
Ok, I've been trying to get this set up for a week now. Here's what I've got.

Fiber Connection to the internet using PPPoE Connected to eth0
1GB Switch Connected to eth1
Several Win XP Pro boxes connected to the switch

I can connect to the PPPoE using pppoeconf without a problem
I can install firestarter, but get an "unknown error"
I've also tried webmin, and using dhcp3-server
I've reloaded from scratch thinking I had messed it up many times (15x or more)

The problem is that it is not handing out DHCP addys and even configuring the XP boxes with static IPs doesn't allow to ping to eth1 (192.168.1.1).

Please help, I will do almost anything...

```
eth0      Link encap:Ethernet  HWaddr 00:50:8D:85:EC:3E
          inet6 addr: fe80::250:8dff:fe85:ec3e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2265 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1891 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1561503 (1.4 MiB)  TX bytes:387956 (378.8 KiB)
          Interrupt:217 Base address:0x2000

eth1      Link encap:Ethernet  HWaddr 00:0E:0C:B8:55:B2
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0xac00 Memory:fcfe0000-fd000000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2708 (2.6 KiB)  TX bytes:2708 (2.6 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:66.172.97.43  P-t-P:66.172.97.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:2175 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1811 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:1508175 (1.4 MiB)  TX bytes:338480 (330.5 KiB)

```

```
#
# Sample configuration file for ISC dhcpd for Debian
#
# $Id: dhcpd.conf,v 1.4.2.2 2002/07/10 03:50:33 peloy Exp $
#

# option definitions common to all supported networks...
option domain-name "fugue.com";
option domain-name-servers 206.130.130.2, 206.130.133.2;

option subnet-mask 255.255.255.224;
default-lease-time 600;
max-lease-time 7200;

#subnet 204.254.239.0 netmask 255.255.255.224 {
#  range 204.254.239.10 204.254.239.20;
#  option broadcast-address 204.254.239.31;
#  option routers prelude.fugue.com;
#}
subnet 192.168.1.0 netmask 255.255.255.0 {
   range 192.168.1.125 192.168.1.225;
   option broadcast-address 192.168.1.255;
   option routers 192.168.1.1;
}

# The other subnet that shares this physical network
#subnet 204.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 204.254.239.10 204.254.239.20;
#  option broadcast-address 204.254.239.31;
#  option routers snarg.fugue.com;
#}

#subnet 192.5.5.0 netmask 255.255.255.224 {
#  range 192.5.5.26 192.5.5.30;
#  option name-servers bb.home.vix.com, gw.home.vix.com;
#  option domain-name "vix.com";
#  option routers 192.5.5.1;
#  option subnet-mask 255.255.255.224;
#  option broadcast-address 192.5.5.31;
#  default-lease-time 600;
#  max-lease-time 7200;
#}

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host passacaglia {
#  hardware ethernet 0:0:c0:5d:bd:95;
#  filename "vmunix.passacaglia";
#  server-name "toccata.fugue.com";
#}

# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.
#host fantasia {
#  hardware ethernet 08:00:07:26:c0:a5;
#  fixed-address fantasia.fugue.com;
#}

# If a DHCP or BOOTP client is mobile and might be connected to a variety
# of networks, more than one fixed address for that host can be specified.
# Hosts can have fixed addresses on some networks, but receive dynamically
# allocated address on other subnets; in order to support this, a host
# declaration for that client must be given which does not have a fixed
# address.   If a client should get different parameters depending on
# what subnet it boots on, host declarations for each such network should
# be given.   Finally, if a domain name is given for a host's fixed address
# and that domain name evaluates to more than one address, the address
# corresponding to the network to which the client is attached, if any,
# will be assigned.
#host confusia {
#  hardware ethernet 02:03:04:05:06:07;
#  fixed-address confusia-1.fugue.com, confusia-2.fugue.com;
#  filename "vmunix.confusia";
#  server-name "toccata.fugue.com";
#}

#host confusia {
#  hardware ethernet 02:03:04:05:06:07;
#  fixed-address confusia-3.fugue.com;
#  filename "vmunix.confusia";
#  server-name "snarg.fugue.com";
#}

#host confusia {
#  hardware ethernet 02:03:04:05:06:07;
#  filename "vmunix.confusia";
#  server-name "bb.home.vix.com";
#}
```


Please let me know if there is anything else you need to help me.

---

### Post by etechsupport.net on 2006-08-10
Try following routing rule :-

route add default gw 192.168.1.1 dev eth1

I have considered eth1 as your default gateway. If eth1 is not your default gateway then you will need to modify the above command.

---

### Post by Kurt` on 2006-08-10
I had problems getting my DHCP server going in [this thread](http://ubuntuforums.org/showthread.php?t=216412).

Turns out I needed to adjust a /etc/sysctl.conf setting. (ip_forward and i believe tcp_syncookies)

I never manually added routes, I just # sudo apt-get install ipmasq , and then everything worked automatically on all interfaces.

---

### Post by TheGamingPit on 2006-08-10
First, thank you both for your quick responses.

I've tried both fixes now.  When I manually added the route, I was no longer able to access the internet (reboot fixed it).  I installed dnsmasq and ipmasq, but still am not getting an ip on my xp boxes.  I modified my sysctl.conf, but still nothing.  

What next?  Do you need any other information from me?

---

### Post by TheGamingPit on 2006-08-10
and now i can only access ubuntuforums.org and google/gmail.  I am more than willing to reload this thing again if I need to.  Can anyone guide me from scratch??  If there's anything i can do to give you all the information you need, please let me know.

---

### Post by TheGamingPit on 2006-08-10
When I restart Firestarter, I get the following in syslog

```
Aug 10 14:42:44 localhost dhcpd: Listening on LPF/eth1/00:0e:0c:b8:55:b2/192.168.1.0
Aug 10 14:42:44 localhost dhcpd: Sending on   LPF/eth1/00:0e:0c:b8:55:b2/192.168.1.0
Aug 10 14:42:44 localhost dhcpd: Sending on   Socket/fallback/fallback-net
Aug 10 14:42:44 localhost dhcpd: There's already a DHCP server running. 
Aug 10 14:42:44 localhost dhcpd: exiting.
```

---

### Post by TheGamingPit on 2006-08-10
[This post]("http://http://ubuntuforums.org/showthread.php?t=91370") fixed it.  The difference seems to be using: 
```
net.ipv4.ip_forward = 1
```
instead of:
```
net/ipv4/ip_forward=1
```

---

### Post by Kurt` on 2006-08-11
> **TheGamingPit said:**
> [This post]("http://ubuntuforums.org/showthread.php?t=91370") fixed it.  The difference seems to be using: 
```
net.ipv4.ip_forward = 1
```
instead of:
```
net/ipv4/ip_forward=1
```
As far as I know, both of those work the same.

The default sysctl.conf uses / in the examples, but I've used . and / and they've both worked.

---

### Post by DeonaLyn on 2006-08-11
Re: Ubuntu Router/DHCP Setup

--------------------------------------------------------------------------------

Hi - this is the same set-up that we have here at the Gaming Pit(except that we have Ubuntu 6.06 loaded on)... we are able to get the internet working with the 'how-to listed'.. finally after struggling with trying to do it on our own for a week, see [post 1367460]("http://ubuntuforums.org/showthread.php?p=1367460");](*,)  but having to use the dynamic IP set on the windows XP boxes. The dynamic IPs is a better option because we have LAN parties where folks bring their PCs and hook up to our system and the Linux machine should be handing out IPs for them, rather than us having to manually configure all the machines every time. Has anyone got a fix for why the DHCP portion of this code isn't working? We are pppoe dependent and don't have a static IP from our ISP. I am a real newbie to Linux, but my techie employees convinced me that Linux & Ubuntu is the way to go!! Reading the forums, the help guides and the literature I agree - but there is quite a learning curve :)  

Also, each time we load firestarter to add in the firewall protection, the whole system crashes, so will be trying the direct format, rather than the gui - unless someone has a better suggestion based on our structure...

As a side note - I am really impressed by the support and community that the Ubuntu community shows. It beats the heck out of what I have seen in the 'other' community!  :-D 

Deanna


Quote:
Originally Posted by LordMerlin  
Hello everyone!

I got the iBurst up and running, with the pppoeconf command 

So, I setup Linux as a PDC, DHCP, caching DNS server, and want it to route internet traffic for the LAN

My setup is as follows:


iBurst Modem (pppoe connection - get's IP from ISP - 196.2.108.xxx)
|
|
|
eth0 (192.168.0.2)
||
Linux box
||
eth2 (192.168.10.1 - running DHCP)
|
|
|
24 port hub
| | | | |
XP PC 1 XP PC 2 XP PC 3 etc etc

The XP PC's can ping 192.168.10.1 & 192.168.0.1, but not 196.2.108.xxx, nor for example google.com. I tried running
"iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE", but that doesn't seem todo anyting. In fact, I followed the Howto Share internet connection

Can somone please assit me with this?

---

### Post by TheGamingPit on 2006-08-12
[CENTER]](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)[/CENTER] 
OK, so we tried to install firestarter for my less-than-expert knowledge of linux, and now it's not working again.  tried re-installing three times, and figured it's time to get back on here and see if anyone can help.  Thank you for your help so far, and I apologize for making this so difficult.

---

### Post by blkish on 2006-08-12
if you are simply using this machine as a router/dhcp server i would recommend looking into monowall and pfsense - 

[www.m0n0.ch](www.m0n0.ch)

and

[www.pfsense.com](www.pfsense.com)

respectively

blkish

---

### Post by TheGamingPit on 2006-08-14
Wow - that sure made it easy!  The pfsense was an easy install, easy interface - and hooked everything up quickly and easily!  Found the router, hands out dhcps - and we are 'alive'

Thank you!!!!
Deanna

---

### Post by dannyboy79 on 2006-11-01
> **TheGamingPit said:**
> Wow - that sure made it easy!  The pfsense was an easy install, easy interface - and hooked everything up quickly and easily!  Found the router, hands out dhcps - and we are 'alive'

Thank you!!!!
Deanna

i went and read about monowall as well as pfsense and I just want to verify something. Using what you did, you basically aren't using Ubuntu any longer correct? It appeared to me that pfsense as well as monowall are both based on bsd which another linux distro all together. if this is true, than this solution isn't really solved. I am looking to get rid of my old netgear router and to buy an additional gigabit ethernet card and turn my ubuntu desktop into a router/dhcp server. i want to stick with ubuntu is there a howto somewhere? or did I read the websites for pfsense and monowall incorrectly? thanks for any guidance.

---

### Post by TheGamingPit on 2006-11-11
[LEFT]The only advice we have is to not use Ubuntu for this.  Still too complicated.  pfsense has about a 5 minute setup, and works great.[/LEFT]

---

### Post by Nitrogen on 2007-02-21
Try Using SME server 7.1.

Easy to configure (about 10 min)
and the os has a web page to configure it, called server-manager

And the Samba shares work easly.
This server also has an E-mail server in it.

---


---
title: "Ubuntu Server Edition was unable to configure DHCP during install, now cannot connect"
date: 2010-04-12
forum: Server Platforms
---

### Post by Danbo19 on 2010-04-12
Hello,
I am trying to install Ubuntu server edition on an old HP XT963 that recently came into my possession. I mainly just wanted to use it as a home file server and print server. I have been running ubuntu desktop on my laptop for a little under a year, but this is my first go at the server edition.

While ubuntu was installing it said "network autoconfiguration failed," I  hit continue, thinking I could figure out how to configure it later. After lots of googling I still haven't figured out what exactly is wrong.

/etc/network/interfaces (just after installation):
```
auto lo
iface lo inet loopack
```

after googling around I made it look like:
```
# The primary network interface - use DHCP to find our address
auto eth0
iface eth0 inet dhcp]
```

pinging my laptop on the same network yields:

```
ping: 192.168.1.102
connect: Network is unreachable
```

and pinging google yields:

```
ping google.com
ping: unknown host google.com
```

I would like to provide more information such as ifconfig and any other commands but I'm not exactly sure how I would do that without being able to copy/paste. I guess I would have the command dump the output to a file, but I'm not familiar with the -options this being my first time CLI-only.

Any help would be greatly appreciated.

---

### Post by KB1JWQ on 2010-04-12
Do you have physical link between the new box and the network?

Is your network card being detected by the install?  dmesg may be of some help in this.

Does ifconfig show any interfaces besides lo?

---

### Post by Danbo19 on 2010-04-12
Hey, thanks for the quick reply.

Yes I do have the box connected via ethernet to the network.

dmesg prints a *long* output. What specifically am I looking for? Although, looking at it a second time just now, towards the end I see:

```
[ 14.945909] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[   22.624028] eth0: no I{v6 routers present
```
Does that help at all?

And yes, ifconfig does show eht0 and a list containing inet addr, Bcast, Mask, etc...

---

### Post by stilling on 2010-04-12
have you done the same with the second network card 

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

if you whant to give internet have you shared your internet connection
is dhcp server installed and configured

in desktop version you have network manager where you can edit eth1 and on ipv4 tab you can " select shared to others " and they will have automatic ip and internet

sorry for questions
hope this helps you and give you a fresh ideea

---

### Post by Danbo19 on 2010-04-12
Um, I guess I don't quite understand.

Should I have two network cards? Does that second eth1 go in /etc/network/interfaces ?

How can I tell if DHCP server is installed?

Sorry, again I'm new at using the command line only and at networking in general.

---

### Post by stilling on 2010-04-12
well you have a computer that you whant to connect with other computers and create a lan 
you whant to connect that computer via wireless or cable ?
if your internet connection is wireless and whant to create a lan via cable you don`t need second network card
or vice versa your internet coes on cable and create a wireless network
but other pc`s that you whant to connect must have wireless card also
if your internet comes with cable and you whant to make a lan cable you need 2 cards 1 for internet and 1 for lan connection 

if you don`t need internet just connect the lan cable in network card 

and see [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)
hope this helps

---

### Post by fang0654 on 2010-04-12
> **Danbo19 said:**
> 

```
# The primary network interface - use DHCP to find our address
auto eth0
iface eth0 inet dhcp]
```



Not sure if this is a typo, but a trailing ] will mess up the config.  It should just read:

```

auto eth0
iface eth0 inet dhcp

```

You can type in the following to test dhcp on your machine, regardless of config settings:

```

sudo dhclient eth0

```

This will show you what is happening when the machine is trying to get an address.

---

### Post by Danbo19 on 2010-04-12
Fang0654:

Yes you're right that was a typo, there is no trailing ]:

```
auto lo
iface lo inet loopack

# The primary network interface - use DHCP to find our address
auto eth0
iface eth0 inet dhcp
```

sudo dhclient eth0 results in a long list of DHCP offers, requests and discoveries. For example:

```
DHCPOFFER of 192.168.1.103 from 192.168.1.1
DHCPREQUEST of 192.168.1.103 on eth0 to 255.255.255.255
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
```
and on and on and on like that

Also if its of any relevance trying to connect via ssh from my laptop results in:

```
danny@danny-laptop:~$ ssh 192.168.1.102
ssh: connect to host 192.168.1.102 port 22: Connection refused
danny@danny-laptop:~$ 

```

---

### Post by Iowan on 2010-04-12
Use **ifconfig -a** to list your interfaces and their addresses. You suggest the server has the address 192.168.1.103, but try to ssh to 192.168.1.102?
You can use **ps -ef |grep dhcp** to see what if a DHCP process is running. My server uses DNSMasq - so the above command doesn't work. 
There is normally only one DHCP server on a (small) network (not including redundant, failover- type networks). Is this machine supposed to be a DHCP server - or did it just fail to get DHCP address?

---

### Post by Danbo19 on 2010-04-13
Iowan:
Thanks for the suggestions, is there a way to dump the output of those commands to a file so I can copy/paste theme here easier? It seems like there is too much margin for error if I try to retype their outputs.

I guess I should have explained what I was trying to do a little better in my OP. The machine isn't supposed to be a DHCP server, it just failed to get a DHCP address. Really all I wanted to do was set up a simple home file server for backups and to transfer files between laptops and to my desktop. Later I thought I might try some more advanced stuff too which is why I chose server edition, I thought it would be a good learning experience. I'm starting to feel like I jumped in over my head though, and maybe I should just install desktop Ubuntu, that way if I ran into the same problem I could fix it easier.

---

### Post by Iowan on 2010-04-13
I get lost in some details, but try this:
```
ifconfig -a >ifconfig.txt
```
```
ps -ef |grep dhcp > dhcp.txt
```
The latter one is probably unnecessary if you're not trying to run a DHCP server. After you get the file(s), you can copy them to a removable drive (floppy or USB stick) and transfer them to another machine to post.
Whether you choose server or desktop, you'll be able to learn a lot. I have a couple of machines set up as servers - one primarily as a web server "toy". It gets IP address via DHCP - but since the DHCP server (the "other" server) is configured to give static lease based on MAC address, the "toy" server always gets the same IP. 
The server edition takes Network Manager out of the equation, and lets you configure the server "the way things used to be configured..." Although it might not specifically answer current issues, the [Server Guide]("https://help.ubuntu.com/9.10/serverguide/C/index.html") is worth reading (bookmarking, even :) )
By the time you're done, you may *want* to install a DHCP server - I like DNSMasq...

---

### Post by Danbo19 on 2010-04-14
Okay, so here is the output of ifconfig -a:

```
eth0      Link encap:Ethernet  HWaddr 00:04:5a:67:38:03  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:5aff:fe67:3803/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6398 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5508 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1059420 (1.0 MB)  TX bytes:399488 (399.4 KB)
          Interrupt:17 Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1668 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1668 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:538580 (538.5 KB)  TX bytes:538580 (538.5 KB)

```
Thanks for the help, I have looked at the server guide, I came here when I still couldn't get and internet connection. Once its up and running I'll take another look at it and see what other cool stuff I can do.

---

### Post by Iowan on 2010-04-14
Thanks for being patient while the info soaks in. **ifconfig** suggests the machine has an IP address (the one you mentioned ;) ). **route -n** should show the routing table. Do the machines (server and laptop) connect to router or switch (they're not connected directly to each other)? We've decided the server has only one network card?

---

### Post by Danbo19 on 2010-04-15
Yes, the server has only one network card. It is connected to the router via ethernet cable and the laptop is connected to the router via wireless.

Here is the output for route -n:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0
```

---


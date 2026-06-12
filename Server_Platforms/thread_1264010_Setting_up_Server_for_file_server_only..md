---
title: "Setting up Server for file server only."
date: 2009-09-11
forum: Server Platforms
---

### Post by billkaroly on 2009-09-11
When it comes to Linux I am a major noob and could use any and all suggestions.

I am in the process of installing Ubuntu Server 9.04 x86 on a spare pc I have sitting around. It has a 40gig hardrive for the system and a 500gb drive for the files. I also want my Windows pc's to be able to see the server.

I have been trying to follow:
[http://www.howtoforge.com/ubuntu-home-fileserver-p3](http://www.howtoforge.com/ubuntu-home-fileserver-p3)

And this is where I am stumped.

My internet provider is AT&T Uverse. I have no need for setting up anything but a file server. It is not going to access the outside world except to get updates.

This is what I get from the 2wire box:

Internet Connection Details
Connection Type:                          Direct IP (DHCP or Static)
Internet Address:                          99.189.103.29
Subnet Mask:                                255.255.254.0
Default Gateway:                          99.189.102.1
Primary Domain Name Server:       68.94.156.1
Secondary Domain Name Server:   68.94.157.1

From another pc on the network:
Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . : gateway.2wire.net
   Link-local IPv6 Address . . . . . : fe80::f53a:7875:5203:c845%11
   IPv4 Address. . . . . . . . . . . : 192.168.1.101
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.1.254


The IP address of the box is 192.168.1.69 (DHCP)

Can I leave Server as-is using DHCP?

or make it static?

/etc/network/interfaces (after making changes:)
[FONT=monospace]
[/FONT]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
 address 192.168.1.110
 netmask 255.255.255.0
 network 192.168.1.0
 broadcast 192.168.1.255
 gateway 192.168.1.254

---

### Post by Udayakiran on 2009-09-12
> **billkaroly said:**
> When it comes to Linux I am a major noob and could use any and all suggestions.

I am in the process of installing Ubuntu Server 9.04 x86 on a spare pc I have sitting around. It has a 40gig hardrive for the system and a 500gb drive for the files. I also want my Windows pc's to be able to see the server.

...................................................

 broadcast 192.168.1.255
 gateway 192.168.1.254


If it is going to be a headless server and you are going to set up shares, it is recommended to make it static.

---

### Post by ugm6hr on 2009-09-12
I'd use static.

Why did you choose 192.168.1.110?

It is generally recommended to use an IP outside your DHCP range or at least near the end.  You other PC has 192.168.1.101 - is this DHCP?  If so, it is unusual that the server gets 192.168.1.69 on DHCP.

Anyway, if you are learning Linux specifically for this purpose, consider using a purpose-built OS instead: FreeNAS.

See the link below for details.

---

### Post by Udayakiran on 2009-09-14
What did you mean by "outside your DHCP range"? can you provide an example? i thought it was not possible...

---

### Post by TwiceOver on 2009-09-14
You should definitely make it static.

First thing you need to do is find out what your DHCP range is.  You should be able to find this in your 2wire box as a setting somewhere.  It should say something like "DHCP SERVER Range" 192.168.1.xxx to 192.168.1.xxx

Once you figure out what the range is, you want to assign an address to your server that is NOT in that range (outside the dhcp range).  

I like to use .10 for my primary server and .100 - .120 for my DHCP range...  It's really just personal preference.

---

### Post by ugm6hr on 2009-09-14
As TwiceOver said.

Many routers use a default DHCP of 192.168.x.1 to 192.168.x.254 or .100

Hence, I use 192.168.x.250 for my router, since there will never be 250 DHCP clients on my network.

But you should, in theory, use an IP outside the DHCP range.

---

### Post by Udayakiran on 2009-09-15
One more thing,
if i use 192.168.y.100 for the server, the devices in 192.168.x.* will not be able to access the server, right?

---

### Post by Iowan on 2009-09-15
> **Udayakiran said:**
> One more thing,
if i use 192.168.y.100 for the server, the devices in 192.168.x.* will not be able to access the server, right?Well, it depends...
The standard 255.255.255.0 (aka /24) would put them in different subnets, but a router could be configured to connect the two subnets... if you tried. On the other hand, a subnet 255.255.0.0 (/16) would have "x" and "y" in the same subnet - and all machines could play with each other.

---

### Post by Udayakiran on 2009-09-17
> **Iowan said:**
> Well, it depends...
The standard 255.255.255.0 (aka /24) would put them in different subnets, but a router could be configured to connect the two subnets... if you tried. On the other hand, a subnet 255.255.0.0 (/16) would have "x" and "y" in the same subnet - and all machines could play with each other.

Okay. Thank you.

---

### Post by billkaroly on 2009-09-18
After I set up this thread I had the darndest time finding it until now. Thanks for everyone who replied. My server is up and working amazingly. Different people seem to have different ideas. Anyway, I Googled the issue and found a solution that worked. I should have saved the link but it's gone and not sure I could find it again. 

I am sure there is some stuff in my smb.conf file that could be taken out but since this is for home use I will leave it like is. 

It was a share problem.

I also shortened to the following:

auto eth0
iface eth0 inet static
 address 192.168.1.110
 netmask 255.255.255.0
   gateway 192.168.1.254


Thanks,
Bill

---


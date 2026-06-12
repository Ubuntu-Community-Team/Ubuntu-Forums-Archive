---
title: "How to Configure Multiple NIC's for dedicated tasks"
date: 2012-10-18
forum: Server Platforms
---

### Post by mattlach on 2012-10-18
Hi,

I'm looking to set up my server (Ubuntu 12.04 LTS Server Edition) with three network cards as follows:

1.) NIC Dedicated to local network access. (SSH, CIFS, Ubiquiti Unifi Server and Web Configuration Interface, etc.)

2.) NIC Dedicated to the iSCSI Initiator (not connected to LAN or WAN)

3.) NIC Dedicated to everything that accesses the outside world.

Problem is, while I know that all this can be done, I don't have the foggiest idea where to start.

How do I set up each NIC to have their own IP address?  How do I tell various services which NIC to use?

The Ubuntu box will not be routing any traffic, it simply sees enough traffic that I feel a need to split it over multiple NIC's in order to avoid overloading the one.

Can someone point me in the right direction so I can figure out where to read up on all this?

Thank you very much,
Matt

---

### Post by LHammonds on 2012-10-19
How to configure multiple NICs with different static IPs?  Assuming they are in your machine and detected as well as being Ethernet cards:

Edit the interface file:
```
sudo vi /etc/network/interfaces
``````

# The loopback network interface
auto lo eth0 eth1 eth2
iface lol inet loopback

# The Secondary network interface
iface eth0 inet static
address 192.168.1.11
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.1
dns-nameservers 192.168.1.101 192.168.1.102

# The Secondary network interface
iface eth1 inet static
address 192.168.1.12
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.1
dns-nameservers 192.168.1.101 192.168.1.102

# The Tertiary network interface
iface eth2 inet static
address 192.168.1.13
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.1
dns-nameservers 192.168.1.101 192.168.1.102

```Restart the networking service:
```

sudo /etc/init.d/networking restart

```Review the config settings:
```
ifconfig
```See if you can ping Google a few times without any packet loss:
```
ping www.google.com
```LHammonds

---

### Post by mattlach on 2012-10-19
> **LHammonds said:**
> 
See if you can ping Google a few times without any packet loss:
```
ping www.google.com
```

LHammonds

Thank you for that, most of this I was familiar with, but I needed the refresher.

Regarding the last part, this is where my knowledge is completely lacking.

When I run that ping command, how do I know which interface the ping command is trying to use?   What if it tries to use the dedicated iSCSI interface?  That would obviously fail.

Is there a way to tell ubuntu which traffic to send to eth0, which traffic to send to eth1, and which traffic to send to eth2?

---

### Post by koenn on 2012-10-19
> **mattlach said:**
> T
When I run that ping command, how do I know which interface the ping command is trying to use?  

You don't; 
LHammond was just explaining to you how to set up multiple NICs


(ping has an option to let you select the sending interface, but that's not really your quastion, is it ?)

> Is there a way to tell ubuntu which traffic to send to eth0, which traffic to send to eth1, and which traffic to send to eth2?

Yes and no. 
Mostly it's a matter of network design, and services.

Most "server" software, i.e. programs that expect connections from clients, will have a configurable option regarding the address they "bind to". The will listen on that address/interface, and reply using the same intergaces.  That should cover most of your samba and ssh tupe stuff.

unless your clients will use bare ip^numbers, you're going to have to use DNS (or a similar solution) to diversify between the NICs, with specific hostnames for each NIC

An other approach is to use seperate networks on each NIC, eg for the iSCSIstorage part, use a 192.168.111.0 network in stead of 192.168.1.0, and give the NIC an address in that network.

"NIC Dedicated to everything that accesses the outside world" is something you can probably handle by way of setting your default gateway to the corresponding NIC, or to a router attached to that NIC.

For the stuff you can't manage with the above, you can probably use 
  - ip route for anything that can be identified by destination IP address or network
  - iptables DNAT, REDIRECT and the likes for traffic that can be identified by source and/or destination address/portnumber. Use only as a last resort, it gets ugly.

---

### Post by LHammonds on 2012-10-19
I could be wrong with what I posted above.  I have not tested it.  There might be a problem with all IP addresses being on the same subnet without additional filter modifications.

As for directing traffic, I believe you need to configure static routes.  I have not done that before so I'll let someone else chime in on that.

Reference Threads:
[Help setting up 2nd interface on Ubuntu 10.04]("http://www.gamerswithjobs.com/node/50990")
[Howto add permanent static routes in Ubuntu]("http://www.ubuntugeek.com/howto-add-permanent-static-routes-in-ubuntu.html")

**EDIT:** That's what I get for not hitting the reply button most of the day...got ninja'd by koenn.  hehehe.

LHammonds

---

### Post by mattlach on 2012-10-21
Thankn you for the help guys.

When I get started on setting this up (still waiting for hardware to arrive)  I'll probably be back with more questions :P

---


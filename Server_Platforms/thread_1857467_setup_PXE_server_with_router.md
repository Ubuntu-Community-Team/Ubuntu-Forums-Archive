---
title: "setup PXE server with router"
date: 2011-10-10
forum: Server Platforms
---

### Post by uPatrick on 2011-10-10
Hello,

I would like to setup pxe server with a router.

internet---(eth1)server(eth0)----router(wireless)---PXEclient

I follow this guidline, but it doesn't work for me
[http://ubuntuforums.org/showthread.phpt=1413126&highlight=dhcp3+fail](http://ubuntuforums.org/showthread.phpt=1413126&highlight=dhcp3+fail)

any help ?
Thank

---

### Post by matt_symes on 2011-10-10
Hi

> **uPatrick said:**
> Hello,

I would like to setup pxe server with a router.

internet---(eth1)server(eth0)----router(wireless)---PXEclient

I follow this guidline, but it doesn't work for me
[http://ubuntuforums.org/showthread.phpt=1413126&highlight=dhcp3+fail](http://ubuntuforums.org/showthread.phpt=1413126&highlight=dhcp3+fail)

any help ?
Thank

Your link above is not taking me to a tutorial. Can you test the link yourself ?

Kind regards

---

### Post by uPatrick on 2011-10-10
[http://ubuntuforums.org/showthread.php?t=1413126&highlight=dhcp3+fail](http://ubuntuforums.org/showthread.php?t=1413126&highlight=dhcp3+fail)

---

### Post by matt_symes on 2011-10-10
Hi

I have not got around to reading the tutorial yet but can you tell us where it is failing ?

Kind regards

---

### Post by uPatrick on 2011-10-10
Hello,

My configuration is:

internet------Switch-01
Switch-01----PC-01(client eth0-192.168.x.x)
Switch-01----PC-02(server eth1-192.168.x.x)  <= connect server to internet ok
PC-02(server eth0-10.2.x.x)------router-01(wireless router)
router-01(wireless router 172.168.x.x)------pc-03(laptop pxe-client) <= can not get ip form server DHCP

if I connect direct laptop(wire) to server, I get ip but tftp fail with ARP timeout

Can you help ?

---

### Post by matt_symes on 2011-10-10
Hi

> **uPatrick said:**
> Can you help ?

I'm not sure on this one but there are plenty of others here. I have  never set up a pxe boot before. I am interested though as it was  something i was thinking of playing with a while ago but never go around  to it.

> PC-02(server eth0-10.2.x.x)

This contains your DHCP server and your TFTP server ? Does it also contain all the boot files ?

> 
My configuration is:

internet------Switch-01
Switch-01----PC-01(client eth0-192.168.x.x)
Switch-01----PC-02(server eth1-192.168.x.x)  <= connect server to internet ok
PC-02(server eth0-10.2.x.x)------router-01(wireless router)
router-01(wireless router 172.168.x.x)------pc-03(laptop pxe-client) <= can not get ip form server DHCP


That is a complicated setup to try to work out what you have. You have three subnets kicking about there.

Ignore the router and get it working directly first.

What address range is your DHCP server supplying. Where is PC-01 getting its ip address from.

> 
if I connect direct laptop(wire) to server, I get ip but tftp fail with ARP timeout


What ip address is PC-03 getting when you connect it directly ?

What is the output of
[FONT=monospace]
[/FONT]```
cat /etc/dhcp3/dhcpd.conf

```
on the server

Kind regards

---

### Post by uPatrick on 2011-10-10
PC-02(server eth0-10.2.x.x) is my server

PC-03 getting client ip 10.5.0.20 mask 255.255.255.0 dhcp ip 10.5.0.1 gateway ip 10.5.0.1 pxe-e11: arp timeout

/etc/dhcp/dhcpd.conf

#option definitions
option domain-name "tufu";
option domain-name-servers 10.5.0.1;
option subnet-mask 255.255.255.0;
option broadcast-address 10.5.0.255;
option routers 10.5.0.1;

allow booting;
allow bootp;
#allow unknown-clients;
default-lease-time 86400;
max-lease-time 604800;
authoritative;

#subnet declaration
subnet 10.5.0.0 netmask 255.255.255.0 {
	range 10.5.0.20 10.5.0.40;
	filename "pxelinux.0";
	next-server 10.5.0.2;
}

interfaces


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

mapping hotplug
	script grep
	map eth1

auto eth1
iface eth1 inet dhcp

auto eth0
iface eth0 inet static
	address 10.5.0.1
	netmask 255.255.255.0

---

### Post by matt_symes on 2011-10-11
Hi

```
next-server 10.5.0.2;
```

Is your TFTP server on a box with IP address 10.5.0.2 ?

Kind regards

---

### Post by Jonathan L on 2011-10-11
Hi Patrick

I echo Matt's comments: you have a complex-sounding network, to me it sounds as though you have a networking issue rather than (as yet) a PXE issue.

You said ```
internet------Switch-01
Switch-01----PC-01(client eth0-192.168.x.x)
Switch-01----PC-02(server eth1-192.168.x.x)  <= connect server to internet ok
PC-02(server eth0-10.2.x.x)------router-01(wireless router)
router-01(wireless router 172.168.x.x)------pc-03(laptop pxe-client) <= can not get ip form server DHCP

if I connect direct laptop(wire) to server, I get ip but tftp fail with ARP timeout
```Is "172.168.x.x" a typo?  What connects the 10.2.x.x machines to the 10.5.x.x machines?  

Why not draw out a little diagram with the addresses on it and we'll see if we can help.

At base, you need to have

[LIST]
[*]a dhcp server on the same LAN as the client machines
[*]a tftp server, either on the same LAN as the clients, or with a working router in between
[*]an nfs server, either on the same LAN as the clients or with a working router in between
[/LIST]

I've used PXE with Ubuntu a lot: the only thing to watch out for is you must not use the package 'tftpd' as it is missing a few features required for PXE.  Use either tftp-hpa (no config required) or atftpd (minimal config required).  Plus correct files in /var/lib/tftpboot; that will get you PXE booting, then good files are required for NFS to bring the Ubuntu up.

If you're getting ARP timeouts it means you're almost certainly addressing a non-existant machine.

Happy to help if you put up the details.  

Kind regadrs
Jonathan.

---


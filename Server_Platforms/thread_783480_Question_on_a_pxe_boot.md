---
title: "Question on a pxe boot"
date: 2008-05-05
forum: Server Platforms
---

### Post by CoffeeBreath on 2008-05-05
Hi
I'm trying to configure a server for a pxe install

How can I figure out an appropriate address range, my servers address and my default gateway and the dns servers address?

as per theses instuctions:

[COLOR="Green"]
tell dnsmasq to assign addresses starting from <BEGIN_IP_RANGE> until <END_IP_RANGE>, put the server's ip address in <SERVER_IP>, the default gateway must be put in <DEFAULT_GW>, and the dns server in <DNS_SERVER>. Append this to /etc/dnsmasq.conf with your favorite editor[/COLOR]

or would this be suitable:

[COLOR="green"]dhcp-range=192.168.0.20,192.168.0.30,12h
dhcp-boot=pxelinux.0,192.168.0.10
dhcp-option=3,192.168.0.1
dhcp-option=6,192.168.0.1[/COLOR]

this will be a home job with a laptop running ubuntu server.

---

### Post by bluefrog on 2008-05-06
I am using dhcp3 server but it might help you.

/etc/dhcp3/dhcp.conf
subnet 192.168.1.0 netmask 255.255.255.0 {
  range dynamic-bootp 		192.168.1.150 192.168.1.200;
  option broadcast-address 	192.168.1.255;
  option routers 		192.168.1.60;
  allow 			unknown-clients;
  use-host-decl-names		on;
  filename "pxelinux.0";

Basically you choose the range you want.

James Dupin

---


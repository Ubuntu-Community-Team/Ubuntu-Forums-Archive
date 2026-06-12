---
title: "openthinclient and dhcp server"
date: 2010-08-09
forum: Server Platforms
---

### Post by noorez on 2010-08-09
Hi,

I am testing out the openthinclient in a virtual box machine. According to openthinclient, you need a separate dhcp server for clients as it does not provide one.

At first, I bridged both the openthinclient server and client to en0 which was connected to my router. This setup was successful. However, I wanted to try it without the router so I attempted to install an ubuntu server with an added dhcp server however this did not work. The thin client gives the error message that no boot file name was passed to it.

any ideas? whats the difference in having the dhcp server on a router vs on a server installation?

EDIT:

Here is the portion of the dhcp.conf file that I created. Could this be causing a problem?

subnet 192.168.0.0 netmask 255.255.255.0 {
	range 192.168.0.20 192.168.0.250;
	option domain-name "example.org"
	option domain-name-servers 192.168.0.1;
	option broadcast-address 192.168.0.255;
	option routers 192.168.0.1;
	option subnet-mask 255.255.255.0;
}

---


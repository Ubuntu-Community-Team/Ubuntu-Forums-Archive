---
title: "Ubuntu DHCP Server and OpenThinClient"
date: 2010-08-09
forum: Virtualisation
---

### Post by noorez on 2010-08-09
Hi,

I am testing out the openthinclient in a virtual box machine. 

At first, I bridged both the openthinclient server and client to en0 which was connected to my dlink router. This setup was successful as I was able to boot the client. 

However, I wanted to try it without the router so I attempted to install an ubuntu server with a dhcp server (on a separate virtual machine, bridged to en0) however this did not work. The thin client gives the error message that no boot file name was passed to it.

Whats the difference in having the dhcp server on a router vs ubuntu installation ?

Here is the dhcp.conf file that I am using. Could this be causing a problem?

```

subnet 192.168.0.0 netmask 255.255.255.0 {
range 192.168.0.20 192.168.0.250;
option domain-name "example.org"
option domain-name-servers 192.168.0.1;
option broadcast-address 192.168.0.255;
option routers 192.168.0.1;
option subnet-mask 255.255.255.0;
}

```

---


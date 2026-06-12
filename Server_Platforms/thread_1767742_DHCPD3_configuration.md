---
title: "DHCPD3 configuration"
date: 2011-05-26
forum: Server Platforms
---

### Post by charlesDS on 2011-05-26
Hi all,

I'm really new at this so I will try to explain my problem and I hope this will be clear enough.

I'm trying to configurate a small company network through my server that runs Ubuntu and DHCPD3 for network config.

Right now my DCHPD.conf file looks like this : 
[I]option domain-name "ergoland.org";
option domain-name-servers 8.8.8.8, 8.8.4.4;
default-lease-time 600;
max-lease-time 7200;
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.5 192.168.1.99;
  option routers 192.168.1.100;
  option subnet-mask 255.255.255.0;
}
[/I]
My server is on IP 192.168.1.100
Basically my internet connection goes straight to the server and then the server is connected to an ethernet switch (Netgear).
And I also run a Apple Time Capsule for my MacUsers that is connected to the switch.
And finally I have a WiFi access point connected to the switch (Netgear).

What I want to know is :
1) Is my DCHPD.conf file correct ?
2) I guess I need to configure my TimeCapsule on a fixed IP in order to work better ?
Basically any help to improve my network that sometimes has glitches would be great !

Thanks

---

### Post by headvampyre@hotmail.co.uk on 2011-05-26
Its unclear what devices are where.

Is the Ubuntu box configured as the router?

If not - the router needs to be set to the IP address of the device, usually something like 192.168.1.1

---


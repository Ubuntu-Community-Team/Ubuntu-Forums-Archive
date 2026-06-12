---
title: "DHCP3 server issue"
date: 2012-03-05
forum: Server Platforms
---

### Post by Justeri on 2012-03-05
Moved from general help to here (probably more correct thread).

************************
Hi,
 
I want to setup local dhcp3 server which returns for example ip address for my FTPS server ( option 66 ) . I don't want to get ip for my self ( at least not yet) :)
 
In addiotion if it is possible to configure dhcp3 server to serve just certain computers ( defined via mac addresses) on LAN i would like to see example about that.

I have two network card and DHCP3 server is set to correct interface
 
INTERFACES=”eth0&#8243;
 
and this interface is configured like below

[INDENT]auto eth0
iface eth0 inet static
address 192.168.1.0
netmask 255.255.255.0
[/INDENT]dhcpd.conf is the following

[INDENT]default-lease-time 600;
max-lease-time 7200;
 
option domain-name "xxxxxx.com";
 
subnet 192.168.1.0 netmask 255.255.255.0 {
option server-name "xxxxxxx";
}
 
[/INDENT]Is this looking like it should?? BTW: Do I need to set subnet at all in case of localhost, could i just list all needed options without subnet definition?
 
Could you please help me how I can test this somehow or what I have done incorrectly.
 
I have tried** pump -i eth0** and **dhcping -s xxx commands** but i do not receive answer from eth0 even dhcpd service is running.
 
Thanks in advance.
****************

---

### Post by Iowan on 2012-03-05
> **Justeri said:**
> 
and this interface is configured like below

auto eth0
iface eth0 inet static
address [COLOR="Red"]192.168.1.0[/COLOR]
netmask 255.255.255.0

That address references the network. 192.168.1.0 and 192.168.1.255 shouldn't be used as client address with 255.255.255.0 subnet.
A DHCP address range might also be valuable.

---


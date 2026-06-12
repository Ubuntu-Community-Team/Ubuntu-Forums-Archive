---
title: "Help needed -Very flaky internet gateway - server V9.04"
date: 2009-10-19
forum: Server Platforms
---

### Post by crazyasyou on 2009-10-19
Hi all,

looking for some help if possible with my Ubuntu Server 9.04 install acting as an internet gateway. I'm not really sure where to start when it comes to posting information, so I'll start with the problem and then post extra information as requested.

In short the internet connection drops out

When its working everything is fine so I'm sure my iptables rules are sound and most of the other config is too. The problem I have seems to hit randomly and without warning and from what I have investigated so far leaves nothing (I'm seeing) in the logs to show an issue.

config is very simple

eth0 - cable modem DHCP (Virgin BB 50mb)
eth1 - Static 192.168.1.1 - lan gigswitch with two or more PCs (192.168.1.2, or DHCP)
eth2 - Static 192.168.2.1 - link to wireless ap (linksys WRT54G DD-WRT)


When I have the problem none of my computers wired or wireless or the ubuntu gateway can contact the web in anyway, **/etc/init.d/networking restart** fixes the problem.

after weeks of searching around I thought this might be a WAN DHCP problem and found that **dhclient eth0** fixes the problem as well, I then started to investigate all my iptables rules for dhcp and found nothing a miss, whatever is happening that causes my internet connectivity to drop anything that brings down/up eth0 seems to fix it for a short time, but I need a better fix that dropping the interface every 12-24 hours.

the gateway is currently running

DHCP for the Lan
iptables
squid web proxy
cacti
LAMP
webmin
ddclient
samba

I'm very new to Linux and normally find most things I need with Google but this one has me stuck,l if i can't get it working soon might have t go back to my kiddie point n prey ISA server.

thanks in advance for any help offered

---

### Post by karlson on 2009-10-19
> **crazyasyou said:**
> Hi all,

looking for some help if possible with my Ubuntu Server 9.04 install acting as an internet gateway. I'm not really sure where to start when it comes to posting information, so I'll start with the problem and then post extra information as requested.

In short the internet connection drops out

When its working everything is fine so I'm sure my iptables rules are sound and most of the other config is too. The problem I have seems to hit randomly and without warning and from what I have investigated so far leaves nothing (I'm seeing) in the logs to show an issue.

config is very simple

eth0 - cable modem DHCP (Virgin BB 50mb)
eth1 - Static 192.168.1.1 - lan gigswitch with two or more PCs (192.168.1.2, or DHCP)
eth2 - Static 192.168.2.1 - link to wireless ap (linksys WRT54G DD-WRT)


When I have the problem none of my computers wired or wireless or the ubuntu gateway can contact the web in anyway, **/etc/init.d/networking restart** fixes the problem.

after weeks of searching around I thought this might be a WAN DHCP problem and found that **dhclient eth0** fixes the problem as well, I then started to investigate all my iptables rules for dhcp and found nothing a miss, whatever is happening that causes my internet connectivity to drop anything that brings down/up eth0 seems to fix it for a short time, but I need a better fix that dropping the interface every 12-24 hours.

the gateway is currently running

DHCP for the Lan
iptables
squid web proxy
cacti
LAMP
webmin
ddclient
samba

I'm very new to Linux and normally find most things I need with Google but this one has me stuck,l if i can't get it working soon might have t go back to my kiddie point n prey ISA server.

thanks in advance for any help offered

Let's start from the beginning?

1. What's the length of the lease on the DHCP?
2.  When the connection drop does your interface go down?  Does the interface have no IP?
3.  If both are still active in 2.  Can you ping default gateway?
4.  Have you spoken with your ISP to find out what they see when this happens?

---

### Post by crazyasyou on 2009-10-19
1. What's the length of the lease on the DHCP?

it a little different each time but seems to be 6.5-7 days (the IP never changes with Virgin unless your MAC changes)

lease {
  interface "eth0";
  fixed-address 77.100.144.1xx;
  filename "Lcd59a1e7b6cf4ef5.cm";
  option subnet-mask 255.255.254.0;
  option time-offset 0;
  option routers 77.100.144.1;
  option dhcp-lease-time 583587;
  option dhcp-message-type 5;
  option domain-name-servers 194.168.4.100,194.168.8.100;
  option dhcp-server-identifier 62.30.240.177;
  option interface-mtu 1500;
  option broadcast-address 255.255.255.255;
  option host-name "x1-6-00-e0-4c-79-34-3d";
  renew 4 2009/10/22 03:59:01;
  rebind 0 2009/10/25 05:15:18;
  expire 1 2009/10/26 01:31:07;
}

2.  When the connection drop does your interface go down?  Does the interface have no IP?
interface stays up and keeps its IP

3.  If both are still active in 2.  Can you ping default gateway?
eerr not sure, will test next time it happens.

4.  Have you spoken with your ISP to find out what they see when this happens?
For once it's not the ISP, if I use my old linksys router or use one of PCs or laptops direct the connection holds.

---


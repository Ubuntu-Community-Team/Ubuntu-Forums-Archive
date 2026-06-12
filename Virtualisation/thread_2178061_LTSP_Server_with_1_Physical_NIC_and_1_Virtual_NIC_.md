---
title: "LTSP Server with 1 Physical NIC and 1 Virtual NIC: Cannot boot Thin-Client"
date: 2013-10-01
forum: Virtualisation
---

### Post by hannah187 on 2013-10-01
Guys I am stuck. This is LTSP related. 

1. I have LTSP server isntalled in Xubuntu (Guest OS). 
2. I have got only 1 wifi nic which is wlan0 and connected to Internet.
3. Thin-Cleint is installed in VirtualBox.

Can I have this virtual thin-cleint booted up through LTSP server with only one physical NIC. I suppose there has to be a way to use a virtual network adapter and point ltsp dhcp server to that adapter and when a thin client booted up, this dhcp server should offer an IP but I have not been able to do this.


All what I am trying to do is to create a test case where we only have:

1 Physical NIC and 1 virtual NIC and have this whole set-up running in my Laptop. 

Please help..Here is a bit more details

Host OS Xubuntu 13.04 is the LTSP server. 1 wifi card connected to Internet. I have got wlan0 (addr:192.168.1.2) and virbr0 (addr:192.168.122.1). virbr0 is created by libvirt and not Virtual Box. 


Thin Client Guest OS installed in Virtual Box. /etc/ltsp/dhcpd.conf edited with these values:

authoritative;

subnet 192.168.122.0 netmask 255.255.255.0 {
    range 192.168.122.20 192.168.122.250;
    option domain-name "example.com";
    option domain-name-servers 192.168.122.1;
    option broadcast-address 192.168.122.255;
    option routers 192.168.122.1;

Thin client virtual network is this: Attached to: Bridged Adapter, Name: virbr0.
When booting up says searching for server ip (DHCP)....No IP.No IP.No IP.

I do not think that virtual box is able to use virbr0 which is created by libvirt.

I have other guest OS and point their network adapter to bridged virbr0 but could not obtain any IP.

Here are some pics to illustrate.

[http://imgur.com/GZvA6gN,A8hMQRT,Vh9esXn,xgt30eW,ErvCxJS](http://imgur.com/GZvA6gN,A8hMQRT,Vh9esXn,xgt30eW,ErvCxJS)

---

### Post by hannah187 on 2013-10-08
I am really hoping that some expert here will come and tell me that

1. This is how it is done, or
2. No this is an impossible situation

Someone please help

---


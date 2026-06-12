---
title: "Quick Routing Question"
date: 2017-09-26
forum: Server Platforms
---

### Post by DigiAngel on 2017-09-26
Quick question.  I have 2 nics.  Eth0 is dhcp and connected to a router which gives it all the info and in turn can get to the internet.  Eth1 has an internal static that I want to get to from my internal network, say 172.16.0.2.  I'm having trouble telling ubuntu to route all internet bound traffic to eth0.  How does one set something like that up?  Thank you.

---

### Post by darkod on 2017-09-26
Do you have a gateway specified for the eth1 config? If you do, delete it. If you want all traffic by default to go over eth0, just let it be default gateway from the dhcp (aasuming the dhcp issues default gateway info).

---

### Post by SeijiSensei on 2017-09-26
You can set up routing, but that would mean adding a static route on your router that sends packets for 172.16.0.0/24 back to your Linux box.  Without that the router will send packets to your upstream provider where they will vanish.

The other option is to configure the Linux box to use "masquerading."  Then all the traffic from the machines in 172.16.0.0/24 will appear to come from the Internet facing interface on the Linux box.  (This is the same method your router uses.)  This method requires using iptables and is described here:  [https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu_Internet_Gateway_Method_.28iptables.29](https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu_Internet_Gateway_Method_.28iptables.29)

In either case you will need to edit /etc/sysctl.conf and uncomment the line "net.ipv4.ip_forward=1".  By default Ubuntu will not forward packets across interfaces as a security precaution.

---

### Post by DigiAngel on 2017-09-30
Thanks for the responses all.

---


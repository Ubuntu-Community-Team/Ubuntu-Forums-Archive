---
title: "DDCLIENT With dyndns"
date: 2008-04-22
forum: Server Platforms
---

### Post by jayashleysmith on 2008-04-22
So I am Running ubuntu (without a GUI), I have a dyndns account with dynamic IP host. I need ddclient to run evry 2 hours and  update my dyndns account with my current web IP. Im on a dynamic Ip so it changes evry DHCP request or router restart.

Any Help would be appreciateed. 

JAS

---

### Post by bluefrog on 2008-04-23
If you cannot configure the router to talk to dyndns directly then you can configure ddclient to retrieve your router's public IP

For example on my router (which has local IP 192.168.0.1, ddclient can retrieve the public IP with the following conf.
adapt to your router access

/etc/ddclient.conf

pid=/var/run/ddclient.pid
protocol=dyndns2
fw-login=your-router-user, fw-password=your-router-user-password
use=fw, fw=192.168.0.1/info.html, fw-skip='ppp_8_35_1' ### the public IP is next to the ppp_8_35_1 field, adapt with where your public IP can be found and on what page###
server=members.dyndns.org
login=your-dyndns-login
password='your-dyndns-password'
jamesdupin.dyndns.org

James Dupin

---


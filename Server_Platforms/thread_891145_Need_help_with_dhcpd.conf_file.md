---
title: "Need help with dhcpd.conf file"
date: 2008-08-15
forum: Server Platforms
---

### Post by bboyambrose on 2008-08-15
I'm currently studying to get my linux+ cert, In the book we start talkin about servers and idk, i configured my server the way the book has it but somethings not right, trying to figure it out, if any 1 can help i would appreaciate it and also tell me whats wrong in detail, thx! :lolflag:






# A LINUX DHCP SERVER
# RESIDE IN /etc/dhcpd.conf

ddns-update-style ad-hoc;
option domain-name-servers 10.0.2.3;
option routers  10.0.2.2;
option broadcast-address 10.0.2.255;


 subnet 198.1.168.0 netmask 255.255.255.255 {
range 10.0.2.1 10.0.2.20;
default-lease-time 14400;
max-lease-time 172800;
}


the error im getting is- Address range 10.0.2.1 to 10.0.2.20, netmask 255.255.255.255 spans multiple subnets!

---

### Post by joebeasley on 2008-08-15
Your range (10.0.2.1 - 10.0.2.20) is not on the subnet you specified (192.1.168.0).  Change the subnet statement to 10.0.2.0 netmask 255.255.255.0.

---

### Post by promodus on 2008-08-15
subnet is abnormal.

---

### Post by Iowan on 2008-08-15
Just a(nother) heads-up... you won't want your static router/server addresses (10.0.2.2, 10.0.2.3) inside your DHCP range.

---

### Post by bboyambrose on 2008-08-16
This is why i love the ubuntu community u guys helped me and i cant appreciate u more, i will have more question on this topic, i really need to grasped this before i take my exam, but thank u all.

---


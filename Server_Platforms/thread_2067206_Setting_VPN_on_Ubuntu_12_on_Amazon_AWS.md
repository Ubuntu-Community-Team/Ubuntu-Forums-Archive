---
title: "Setting VPN on Ubuntu 12 on Amazon AWS"
date: 2012-10-06
forum: Server Platforms
---

### Post by Ronin1770 on 2012-10-06
Hi All

I have been trying hard to setup VPN Server on micro instances running on Amazon EC2  - however It was never successful. 

I have followed many guides and tutorials - however I couldn't make it through

I am getting following error when I am trying to connect from my Android phone:

I have assigned an Elastic IP to this AWS instance and that IP address is used as "SERVER.IP.ADDRESS" in /etc/ipsec.secrets


Any ideas what am I doing wrong?


```

Oct  6 11:30:02 pluto[6371]: packet from 110.38.x.x:500: received Vendor ID payload [RFC 3947] method set to=109
Oct  6 11:30:02 pluto[6371]: packet from 110.38.x.x:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02] meth=107, but already using method 109
Oct  6 11:30:02 pluto[6371]: packet from 110.38.x.x:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but already using method 109
Oct  6 11:30:02 pluto[6371]: packet from 110.38.x.x:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-00]
Oct  6 11:30:02 pluto[6371]: packet from 110.38.x.x:500: ignoring Vendor ID payload [FRAGMENTATION 80000000]
Oct  6 11:30:02 pluto[6371]: packet from 110.38.x.x:500: initial Main Mode message received on 10.209.105.134:500 but no connection has been authorized with policy=PSK


```

---


---
title: "ISP and DNS Servers"
date: 2009-08-01
forum: Server Platforms
---

### Post by oliv2915 on 2009-08-01
Is there a standard DNS server that can be used instead of your ISP's? If not, how can I setup bind9 with its own DNS IP's that point to my ISP on eth0 DHCP assigned DNS servers?

---

### Post by nix4me on 2009-08-01
You can use opendns instead of your isp.

[https://www.opendns.com/start/](https://www.opendns.com/start/)

Or you could setup your own dns servers via bind.  Bind works great however it is not what I would call easy.  Great care must be taken to understand and configure a proper dns server.  I run my own dns servers for my linux servers, but for home use, I use opendns.

---

### Post by oliv2915 on 2009-08-01
> **nix4me said:**
> You can use opendns instead of your isp.

[https://www.opendns.com/start/](https://www.opendns.com/start/)

Or you could setup your own dns servers via bind.  Bind works great however it is not what I would call easy.  Great care must be taken to understand and configure a proper dns server.  I run my own dns servers for my linux servers, but for home use, I use opendns.

I am more then willing to learn. I have reinstalled server and resetup DHCP and ufw masq over 30 times now and all of it was do to me learning what I can and can not do. As it stats I have to use my ISP DNS server in /etc/dhcp3/dhcpd.conf on the line for option domain-name-servers. If I leave that blank it won't let me connect to the internet. I like to have it setup so I can use a couple of IP's that I chose, ex: 10.10.0.2, 10.10.0.3.

---


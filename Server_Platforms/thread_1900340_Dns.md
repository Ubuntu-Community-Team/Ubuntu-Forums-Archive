---
title: "Dns"
date: 2011-12-26
forum: Server Platforms
---

### Post by biela on 2011-12-26
Im using Ubuntu Server 10.04.
I already setup the server and succeed in installing the EyeOS in Ubuntu Server.
I want to put the new domain that I bought for the EyeOS.
However, i met problems to up my server using the new domain name.
It seems like it involve the DHCP while configuring it.
The things is, we used our university network and the university used DHCP.
Is there other way to up my server and I no need to meet the technician to do it

Thank u.

---

### Post by oldos2er on 2011-12-26
Moved to Server Platforms.

---

### Post by rubylaser on 2011-12-26
I wish I understood what you are trying to accomplish so I could try to help. But, I'm not really sure what you're talking about or trying to accomplish.

---

### Post by Vegan on 2011-12-26
BIND is the open source DNS standard tool of choice.

[http://www.isc.org/software/bind]("http://www.isc.org/software/bind")

---

### Post by rubylaser on 2011-12-27
I don't think the OP is actually asking about DNS.  I sounds like he's trying to get his EyeOS box routable on the public internet, but he's connecting to his university's network.  As result, he's getting a private ip address for the school's network.

If this is the case, you'd need NAT setup to map a public ip address to your box (which would need a static ip address).  I don't know of any university that would do that for you.  Maybe I misunderstood, but that is my guess of what you're trying to accomplish based on the original post.

---


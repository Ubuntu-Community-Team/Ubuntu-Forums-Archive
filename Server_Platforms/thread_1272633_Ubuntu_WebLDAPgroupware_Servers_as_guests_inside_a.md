---
title: "Ubuntu Web/LDAP/groupware Servers as guests inside a Ubuntu Server machine"
date: 2009-09-22
forum: Server Platforms
---

### Post by 9047boy on 2009-09-22
Hi.

I am planning to build an Ubuntu server as a router/gateway/DNS/print/LDAP/groupware/SAMBA/web server. My idea was to build the machine as a router/gateway/DNS/print/SAMBA and install several virtual machines inside it to serve as:
1) a web,
2) LDAP and
3) groupware servers respectively.
The guests would also be Ubuntu Servers, JeOS maybe.
What I would like to know is if this would be a viable solution for a small business office (mainly security wise). 

Also, I know it is off topic, but it is part of the same problem, I will have to migrate a web server from a cPanel WHM to Webmin, so if you could give me any advice regarding this migration, that would be great.
The server configuration is as follows:
Intel Pentium Q9400
Intel BLKDQ45CB M/B
2 x 2GB DDR2
2 x 500GB SATA2 HDDs, with RAID1 (I only have 2 hard-drives at my disposal) software?(not sure how the mainboard RAID controller will interact with a software RAID)

Any solution as to how this could be done is appreciated (with or without virtualization).

Thanks in advance.

EDIT: the server will manage somewhere around 15 workstations, 10 on LAN an a few more by VPN. The web server hosts our company's website, so it will be public.

---


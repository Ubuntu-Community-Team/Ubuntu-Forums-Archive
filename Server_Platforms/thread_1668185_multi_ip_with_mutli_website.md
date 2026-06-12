---
title: "multi ip with mutli website"
date: 2011-01-16
forum: Server Platforms
---

### Post by alan889999 on 2011-01-16
Hi everyone 

Just need some help here

I rent a server with 7 ip given. And i also want to host 7 website with 7 domain name in it

I wish to assign each website with an ip address. is it possible to do that ?

When I do

<VirtualHost 192.1.1.123:80>

<VirtualHost 192.1.1.124:80>

<VirtualHost 192.1.1.125:80>

I type the domain can't go to the web site

something wrong

---

### Post by James78 on 2011-01-16
Try...
```
NameVirtualHost 192.1.1.123
NameVirtualHost 192.1.1.124
NameVirtualHost 192.1.1.125

<VirtualHost *:80>
```

---


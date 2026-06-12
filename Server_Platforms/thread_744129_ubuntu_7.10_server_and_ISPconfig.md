---
title: "ubuntu 7.10 server and ISPconfig"
date: 2008-04-03
forum: Server Platforms
---

### Post by AnthonyArde2 on 2008-04-03
Hi all, 
i have installed isp config on my computer but i`m a bit lost, i have put in a server address eg [www.mydomainname.co.za](www.mydomainname.co.za)

unfortunatley this domain is hosted with my ISP at the moment, so i wont be able to use it untill i get them to release the domain to me.

i require to do testing on this server so i need to change my server address to an address that i will be creating on DynDNS, how do i change my server name/address in ISPconfig?

Thanks

Anthony

---

### Post by hyper_ch on 2008-04-03
edit your /etc/hosts and add a new entry

IPADDRESS_OF_ISPCONFIG_SERVER [www.mydomainnem.co.za](www.mydomainnem.co.za)

---

### Post by AnthonyArde2 on 2008-04-03
ok, this would work but i have entered in a different name:

in the /etc/hosts i have my ip and my servers name but this is different to the server name i filled in during the isp config, at the end of the isp config installation it asks for a server name and i filled in a domain name that is being used at the moment, my server name under /etc/hosts is different to this name, it look like i am going to have to change both. 

where am i able to change the other. 

thanks for your assistance so far.

Anthony

---

### Post by cdenley on 2008-04-03
I'm not sure I understand your last post, but you can have multiple hostnames for your ip in /etc/hosts
```

127.0.0.1 localhost www.host1.com www.host2.com

```
/etc/hosts is just used to resolve names, like if you ping a name, or enter it in a web browser. It is read before a dns query is sent.

---

### Post by AnthonyArde2 on 2008-04-03
The problem is not in /etc/hosts.

the problem is in the configuration setup for ISPconfig, it said :

Please enter the host name (e.g www): www (i filled in www)
Please enter the domain name (e.g xyz.de) : dimensionpo.co.za (i filled in dimensionpo.co.za)

the domain dimensionpo.co.za is already in use at my isp so i have to change this entry to a new domain that i`m getting at DynDNS, where am i able to change this?

Thanks

Anthony

---


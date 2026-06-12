---
title: "Postfix Hostname and Domain name confusion"
date: 2010-02-17
forum: Server Platforms
---

### Post by youmustcomply on 2010-02-17
Hello,

I hope someone will be able to point me in the right direction. I have a server install of Ubuntu 8.10, which is currently running OpenLDAP, Samba, Bind, DHCP, NFS and Postfix with Davecot.

I believe i am very close to having postfix and Davecot working properly however I am having some confusion with the domain name.

my server is running a Samba domain
domain: company.local
name of server: Server
So the FQDN I believe to be Server.company.local

I have configured Postfix to run my actual internet domain
Domain: company.co.uk
MX records is pointing to mail.company.co.uk which points to my WAN IP which is then passed through a router/firewall.

My problem is in the main.cf file for postfix,


```

mydomain=company.local
myhostname = Server.company.local
myorigin = $mydomain

Some text omitted

```

Should this be the .local domain or the .co.uk domain?

Any help appreciated.

---

### Post by mbehamin on 2010-02-18
you should set it as your internet hostname of your mailserver. 
for example if your domain name is test.com you should set $servername.test.com

---

### Post by youmustcomply on 2010-02-19
Thanks, I will give this a try later.

---


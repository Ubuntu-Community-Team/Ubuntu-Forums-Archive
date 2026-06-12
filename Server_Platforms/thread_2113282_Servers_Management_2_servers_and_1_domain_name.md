---
title: "Servers Management: 2 servers and 1 domain name"
date: 2013-02-07
forum: Server Platforms
---

### Post by alfirdaous on 2013-02-07
Hello everybody,

I have 2 servers and 1 domain name:

+ Server1 with IP_SERVER1
+ Server2 with IP_SERVER2
+ domain.com

So domain.com is attached to Server1 (DNS and BIND)

I would like to create a subdomain for Server2, someting like: server2.domain.com

What are the steps that I should do to have access into my Server2, with url: server2.domain.com

PS: I am using command lines, no WHM.

Thanks for your replies

---

### Post by spynappels on 2013-02-07
I'm not sure if your DNS is internal only or external, but for the domain DNS entries accessible externally, you would creat a cname record and point it to the IP of the second server, assuming it has a public IP.

---

### Post by alfirdaous on 2013-02-07
I think the DNS is external, in this case how to use CNAME

---

### Post by spynappels on 2013-02-08
Ok, with your domain registrar, do you have the domain DNS set to the registrar's DNS servers, or to your own DNS server?

Do both servers have a unique public IP address, or are they NAT'd behind a single public IP address?

---

### Post by alfirdaous on 2013-02-09
> **spynappels said:**
> Ok, with your domain registrar, do you have the domain DNS set to the registrar's DNS servers, or to your own DNS server?

My DNS has been set to the registrar

> 
Do both servers have a unique public IP address, or are they NAT'd behind a single public IP address?They have different IP's

---


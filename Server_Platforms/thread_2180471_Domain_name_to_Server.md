---
title: "Domain name to Server"
date: 2013-10-13
forum: Server Platforms
---

### Post by salmendar on 2013-10-13
Hi,
     i have a static ip in my home and i have ubuntu server that is completely accessable. now the problem is that i can access it only using the ip and now i want to access it using a domain name. the problem is that i already know that i have to buy the domain from a domain name provider which i have already accomplished but i want to bind it to my ip to which i cnnot find the right steps to do .. please direct me towards the right ways by which i can bind the domain name to the ip.
thank you for the time

---

### Post by Lars Noodén on 2013-10-13
The steps vary from registrar to registrar because they have their own web interfaces for record management.  Which one is it?  Someone here might already be using it.

---

### Post by TheFu on 2013-10-13
[http://blog.jdpfu.com/2010/11/05/what-you-need-to-have-a-web-site](http://blog.jdpfu.com/2010/11/05/what-you-need-to-have-a-web-site) should explain what you need. It is impossible to explain the exact steps since every service provider will have a different interface.

I think you are missing the DNS service provider.

Make sense?

---

### Post by salmendar on 2013-10-13
quiet most of what i wanted but the thing is that i have a server running in the [static_ip]("http://182.180.82.4"). now my friends also need to get hold of it and use it for their development. so i want to give it a domain name since everyone cannot remember the ip and keep asking for it again and again.

---

### Post by salmendar on 2013-10-13
i have the public ip adress and the web server running . most of the reserach shows me that i don't need the DNS and i already have the domain name registered. now the only thing that i need is to bind the domain name to the ip....... that is what i need to know how to do .

once again i have the following

1)    static ip
2)    webserver running on my static ip
3)    a web domain

i need to bind them. tell me how to do that

---

### Post by Lars Noodén on 2013-10-13
The registrar should have a web interface that you log into to manage your domain name.  There it should allow you to set A or CNAME records for your IP address.  [bind](https://www.isc.org/downloads/bind/), at least for your part of the bargain, is not involved.  You only have to work through the interface they provide for you to manage your hostnames.

---

### Post by TheFu on 2013-10-13
Well, your research is incorrect. Sorry to say that.

A DNS is mandatory.  Did you read that link previously provided? Registrar, DNS, web server.  3 things are needed. If your IP address changes - i.e. is dynamic, then you'll want a dynamic DNS service - there used to be free ones - dyndns.org, no-ip.org ... probably a few others. I've been using Dyn for well since 1998. Some of these might be in your home router interface to make life easier.

Your registrar **may** provide DNS services, but 
a) using an all-in-one solution has drawbacks
b) registrars usually have you point to a DNS provider via IP for the domain DNS.  
c) You could run your own DNS, but generally that is a really, really bad idea for many reasons. Read that link.

DNS is the part you are missing.
The CNAME parts listed above by Lars are related to DNS records. You can't get around it.

---

### Post by jsavage1 on 2013-10-18
TheFu is right. DNS is the missing element. Dyn no longer offers free dynamic DNS service. I am currently using noip.com and it has been working great.

---

### Post by salmendar on 2013-10-19
the jobs done... asked my supervisor to do it for me... indeed i have a lot more to learn and i am just new to this......

thank you all very much . and yes DNS is important.

take care and keep helping guys like us..
someday we might be also of some help to others

---


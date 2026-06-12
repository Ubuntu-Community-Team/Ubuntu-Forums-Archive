---
title: "Setting up Virtual Hosts"
date: 2009-03-26
forum: Server Platforms
---

### Post by daboroe on 2009-03-26
I know this is a newb question and I should know it but I will ask none the less, so if another person is afraid to ask it they can not fear being made fun of. lol. I will take the heat for that.

When running Virtual Hosts in apache2 on ubuntu server, do you need to run a DNS server? 

I am planning on setting up a server at my house or apartment when I get out of school (May 2009) and want to make sure I understand everything okay.

---

### Post by volkswagner on 2009-03-26
You do not need a DNS server.  You can use the DNS provided at the registrar or with a service such as [Dyndns.com]("http://www.dyndns.com/")

If you have a static IP address provided by your ISP, you won't need a dynamic host provider service.  You can still use the free service if you don't want the $5-10/yr for a domain like mydomain.com

---

### Post by daboroe on 2009-03-26
so just purchase a domain name. and i need to buy a static ip or use dyndns.org or something like that correct?

---

### Post by volkswagner on 2009-03-26
That is correct.  

If it is not imperative to have your sites up 100% of the time, you can start without the dynamic service.  Many times under good conditions your ip address wont change for months.  You can manually update your ip address at the registrar to save the $27/yr on the dynamic services.

Just a though.

Enjoy

---


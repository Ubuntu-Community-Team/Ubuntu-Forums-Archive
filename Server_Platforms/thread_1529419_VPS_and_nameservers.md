---
title: "VPS and nameservers"
date: 2010-07-12
forum: Server Platforms
---

### Post by tbobker on 2010-07-12
I am getting a bit confused with this nameserver stuff and wanted some advice.

Basically, I just started renting a new VPS. This only came installed with Ubuntu 10 server. 
I installed Apache, MySQL and PHP I then wanted to setup a new domain name to point to my VPS.

I immediately thought I needed to install Bind9 for this, but noticed I can setup A records in my 123-reg account who is my domain registrar.

How can I configure my new server to deal with different domain names / multiple sites that are hosted on the VPS? Do I need to use Bind9?

---

### Post by terazen on 2010-07-12
Setup your dns with your domain registrar and use apache name-based virtual hosts on the VPS.  You don't need to setup bind unless the domain registrar website doesn't do what you need.

You'll create multiple apache sites in the /etc/apache2/sites-available/ directory with each site using a seperate name.  Look up NameVirtualHost howto's in a search engine and there should be a number of guides out there.

---

### Post by zereshk on 2010-07-12
It looks trivial, but I've also had HUGE headache to set up a Bind9 dns server on my vps. I could not find any decent tutorial to explain it in a detailed and noob-friendly way. They are either uncomplete or too elaborated for a humble dns server set up.

Here is the one I tried (and failed!)

[http://news.softpedia.com/news/How-to-Host-Your-Own-Domain-With-Bind9-on-Ubuntu-49585.shtml](http://news.softpedia.com/news/How-to-Host-Your-Own-Domain-With-Bind9-on-Ubuntu-49585.shtml)



So it would be a great help if anyone can point me to the right direction or write a complete dns tutorial for noob vps admins.

---

### Post by terazen on 2010-07-12
My personal opinion about setting up bind is that it's faster and easier to just read the first four or so chapters of the o'reilly book.  Going through a guide to setup bind is just asking to spend hours troubleshooting.

---

### Post by BobVila on 2010-07-12
Unless you're setting out specifically to learn bind, go with the first response. Have your VPS provider host the a records, configure the sites in sites-available, and leave the uptime and related DNS headaches to them.

---

### Post by zereshk on 2010-07-16
Well, at last I cope with the bind problem for my VPS, and documented the steps here:

[http://vpsdiary.blogspot.com/2010/07/setting-up-bind9-dns-sever-on-vps.html](http://vpsdiary.blogspot.com/2010/07/setting-up-bind9-dns-sever-on-vps.html)

---


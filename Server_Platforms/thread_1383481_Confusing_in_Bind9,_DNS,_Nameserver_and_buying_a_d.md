---
title: "Confusing in Bind9, DNS, Nameserver and buying a domain"
date: 2010-01-17
forum: Server Platforms
---

### Post by Grey08 on 2010-01-17
Hi

I have set up my own webserver, so thinking to get my own domain name. The thing is, when i tried to buy the domain i saw:

- Domain Name Servers
-------------------------------
1.Please Park my domain using abc's DNS servers (select this if you do not have DNS servers)

2.Use my own or my ISP's DNS Servers below (it must be registered DNS servers):
      NameServer #1 |_______________|(eg. ns1.myisp.net)
      NameServer #2 |_______________|(eg. ns2.myisp.net)


I get confused while i saw them, so i google "nameserver, DNS" and found that i should install BIND9, thus, i installed Bind9 and now i m still confusing about:

 "2.Use my own or my ISP's DNS Servers below (it must be registered DNS servers)"

--------------------
The problem now&#65306;
1. I think i already have "my own DNS server", so what should i put in the blank of:

NameServer #1 |_______________|(eg. ns1.myisp.net)
NameServer #2 |_______________|(eg. ns2.myisp.net)


2. Does that mean i can make my own domain with Bind9, for instance, "grey08.ubuntu", so everyone across the internet can reach my server through "grey08.ubuntu"??


I hope my English doesn't make everyone confusing. ;)


Best regards
Grey08

---

### Post by Grey08 on 2010-01-17
Anyone help me please??

---

### Post by gombadi on 2010-01-18
Most registrars that I have worked with also offer dns hosting - [http://www.dyndns.com/](http://www.dyndns.com/) and [http://www.godaddy.com](http://www.godaddy.com) for example.

When you buy a domain from them you can choose to host the dns on their machines then use the web interface to configure it so anybody looking up your site will be given the ip address of your server.

If the company does not provide dns hosting for domains they sell then you can still use a dompany like Dyndns to provide the dns hosting and just tell the registrar the ip addresses for the Dyndns servers (they will be providing the dns hosting)

If you want to host the dns servers yourself then you need to setup two servers and provide their ip addresses to the registrar. The ip addresses go in the Nameserver fields you posted above.

Bottom line is that you do not need to run/host your own nameservers/bind/dns just to provide a web site for your users. If running the web site is your main interest then put your time into that and leave the dns hosting to a company the works in that field.

---

### Post by tlsarles on 2010-01-18
True story, I wouldn't run your own nameservers unless you have to. I register my domains with godaddy.com simply because they have pretty simple dns management

---

### Post by Grey08 on 2010-01-19
> **gombadi said:**
> 

Bottom line is that you do not need to run/host your own nameservers/bind/dns just to provide a web site for your users. If running the web site is your main interest then put your time into that and leave the dns hosting to a company the works in that field.


Hi all

Yes, its my interest in web hosting, so i really willing to spend my time.

But when u say i dont need to run/host my own nameserver juto provide a web site for my user, i dont understand this, could you please say more about this? 

Thanks

Grey08

---

### Post by i.r.id10t on 2010-01-19
If you have 2 ip addresses you can host DNS for yourself and/or others.  Easiest to do is to use glue records to refer to yourself for your domain (or get a cheap $1 .us or .info, etc domain and use the registrar to point to that).  Then use some software to set up your DNS service.  I use ISPConfig for my hosting, works great

---


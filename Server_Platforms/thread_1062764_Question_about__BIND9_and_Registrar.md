---
title: "Question about  BIND9 and Registrar"
date: 2009-02-07
forum: Server Platforms
---

### Post by PGKMN on 2009-02-07
Hi all.

I've installed BIND9 and registered domain name(somename.net) at registrar. The registrar gave me account and password to login to a control panel at it's web site. From there I can choose from activation of DNS hosting or setting of DNS servers. If I choose to set the DNS servers and write ns1.somename.net and I try to save the changes it says that's invalid record. If I choose DNS hosting I have the following options:

hostname     address            Record type

*            xxx.xxx.xxx.xxx     A record
@            xxx.xxx.xxx.xxx     A record
www          xxx.xxx.xxx.xxx     A record

I can add A record, CNAME, URL forwarding, FRAME forwarding and TXT

When I set my IP address with an A record and ping somename.net it shows my IP address. But it works with or without BIND9 installed. When I type whois somename.net it says: 
ANSWER SECTION:
somename.net.  172800	IN  NS	dns1.name-services.com.
somename.net.  172800	IN  NS	dns2.name-services.com.
somename.net.  172800	IN  NS	dns3.name-services.com.
somename.net.  172800	IN  NS	dns4.name-services.com.
somename.net.  172800	IN  NS	dns5.name-services.com. 

What i need to do in order to make BIND to be name server of somename.net?

Please help:confused:
BTW  My IP address is static. 

Sorry for my English.

---

### Post by windependence on 2009-02-08
I've said it many times, and I wish they would make it clear in the tutorials. You DON'T need bind9 (a dns server) to run your own domain. Use your registrar's dns servers. You'll be much happier. Running your own DNS is a PITA, and you can actually make people very mad if you do it wrong.

Your English is great, BTW.

-Tim

---

### Post by PGKMN on 2009-02-20
In my case I really need to run my own DNS server. Should I talk with someone from the registrar?

BTW What PITA stands for?

---

### Post by cariboo on 2009-02-20
I'd like to know why you think you need to run your own DNS server too. Why run another service needlessly, when there are third party DNS servers all ready to go.

If you use a third party dns service it takes about 48 hours for the records to propagate through the other main dns servers, whereas there is no gaurantee on how long it takes if you do it yourself.

PITA = pain in the a**

Jim

---

### Post by PGKMN on 2009-02-23
> **cariboo907 said:**
> I'd like to know why you think you need to run your own DNS server too. Why run another service needlessly, when there are third party DNS servers all ready to go.

If you use a third party dns service it takes about 48 hours for the records to propagate through the other main dns servers, whereas there is no gaurantee on how long it takes if you do it yourself.

PITA = pain in the a**

Jim

Because with domain hosting come some restrictions that won't apply if I run it on my own.

And now you mentioned it PITA is probably PIN in the a** :)

---

### Post by windependence on 2009-02-23
Please explain this, I'm all ears. I run quite a few commercial boxes here and I use Godaddy's name servers for ALL of them. There are NO restrictions. I think you are confusing your ISP blocking ports with using your registrar's nameservers.

-Tim

---


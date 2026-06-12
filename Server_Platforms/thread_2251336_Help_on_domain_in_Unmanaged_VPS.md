---
title: "Help on domain in Unmanaged VPS"
date: 2014-11-03
forum: Server Platforms
---

### Post by Don_Jajo on 2014-11-03
Hi,
I bought this Unmanaged Ubuntu VPS from GoDaddy and have issues with domain name. My domain is registered externally, not by GoDaddy I mean, successfully my domain registrar configured my domain for me and its opening my IP. They said the added A Record that points to my IP and created nameservers for me ns1.site.com, ns2.site.com.

Now my problem is, they said if i add the ns1.site.com and ns2 as nameservers to any domain, I can add them to my server. Now how can I do that? :/ and am not having an MX Record for mails.

I just need how to configure  domain in an Unmanaged VPS when the domain is external.

Thanks :)

---

### Post by Habitual on 2014-11-05
Don:
You will need to  edit the nameservers for any other domain you control to use ns1.site.com and ns2.site.com
and it will get pointed to your VPS.

How it works in real life:
I fire up my browser and enter [www.mydomain.com](www.mydomain.com) and my host goes to the .com root server and asks "Does mydomain.com exist?" and if it does, "Where are your nameservers?"
The the query gets directed to ns1.site.com and asks "What's the 'A Record' for www.mydomain.com?" and off you go to the host with the A Record for mydomain.com and apache, nginx, or litespeed (any www-serving software) "serves" up the site for [www.mydomain.com](www.mydomain.com).

or Simply:
.com > domain > namservers > VPS

I really hope that helps.

---


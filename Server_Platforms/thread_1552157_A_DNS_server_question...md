---
title: "A DNS server question.."
date: 2010-08-13
forum: Server Platforms
---

### Post by Asoslim on 2010-08-13
Hello everyone,

i have set up a bind9 dns server and it works ok.
but i need to enter a blocked web site. 
i created a zone file for that website and now, i can enter the website. 
but the issue is, that web site has more than 100 subdomains and the IPs change often. i can not create/set zone file for each subdomains. and if i dont do that i cannot use that website.

the thing that i wanna do is, i want to solve the domain name with my domain name(i did it) and forward the rest domains to googles public name servers to solve.(when i use googles public NSs i cannot enter the web site, i have to solve that website first on my dns server than forward it) 

i used allow-update, allow-transfer etc  but the problem is still going on.

Thank you

---

### Post by scorp123 on 2010-08-13
> **Asoslim said:**
>  but i need to enter a blocked web site. 

Nasty web-site or not, but entering web sites that do not belong to you into your DNS is the wrong way to do it. And if your DNS is connected to the internet you are even forwarding those false entries which may cause others to see your site as malicious as well.

If you only want to block that web site for your own PC then it would be easier and far less work to enter their domain into /etc/hosts ... There are web sites that automatically produce ready-to-use /etc/hosts files filled with addresses of spam sites and malicious servers. Please read here:

[http://pgl.yoyo.org/adservers/](http://pgl.yoyo.org/adservers/)

It's fairly easy to extend such a list with your own entries.


If however you have a network with multiple users you could do the following things:

1. use a proxy server and block that unwanted web site this way

2. use a content-filter that will intercept any requests for that unwanted web site and re-route the connection to another page (e.g. a "Sorry" page that will say: "Sorry, that web site is not accessible!!")

3. use your firewall and once and for all block every traffic from that country where that web site is located. Game over.


Option #3 works pretty well. When a spammer from a certain Central Asian country kept attacking our servers we decided to once and for all block that guy's entire country and IP range. We're a small Swiss company, chances that we will ever do business with that country or ever travel there are totally zero. So when we got fed up we configured our firewall to completely block that country's one and only ISP by completely blocking their IP range, e.g. 123.*.*.*  <== Game over. No traffic from that country and ISP will ever reach us again ... and vice versa too, but then again we don't care.

The best of course would be to use a sensible combo between proxy + content-filter + firewall. This should help to eliminate any unwanted traffic to those addresses and their many sub-domains.


I hope this helped ... ?

---


---
title: "Apache2 with multiple webistes and forward 1 website to another lan apache"
date: 2009-07-23
forum: Server Platforms
---

### Post by pmla on 2009-07-23
I have been trying to get my apache2 to host multiple websites (sub-domains) of my main domains. Also 1 website (sub-domain) is hosted in another LAN computer.
Up to now it's mission impossible, so I will ask you guys if it's possible to do this. If so, the best easiest way of doing it.

A)
1 domain (example.com)
2 subdomains
 -sub1.example.com
 -sub2.example.com

B) everything being forward to my wan IP 

C) my router forwarding port 80 and 53 to may main apache2 webserver which is also dns server. 192.168.1.1

D) Main apache2 webserver 192.168.1.1 serves 2 websites
 - example.com website 
 - sub1.example.com
 - and should forward the 3 website sub2.example.com to another LAN computer with apache2 192.168.1.9



The dns is working ok inside the lan and I can ping the hosts ip's/domain names.

From the wan the domain and sub-domains always point to the sub1.example.com website????

I had my system running with different ports. The websites were 30000 the domain, 30001 sub1 and 30002 sub2. The router would point 30000 and 30001 to the main apache that I configure to respond to the selected ports. And would point 30002 to the other lan computer running apache sub2. It worked.


Is it possible to point domain and sub domains (port80) to the main apache server? Have it manage domain and sub1 and forward sub2 to another lan ip?

---

### Post by pmla on 2009-07-23
brrrr... getting desperate with this

the websites are working fine inside the lan

firefox browser inside LAN port 80
[http://example.com](http://example.com) points to main apache and shows the correct website

[http://sub1.example.com](http://sub1.example.com) points to main apache and shows the correct sub1.website

[http://sub2.example.com](http://sub2.example.com) points to second apache and shows the correct sub2.website ... but i'm guessing inside the lan the request goes directelly to the correct second apache server due to internal dns server


Firefox WAN port 80 (outside my lan)
domain and sub-domains all show the same website sub1.example.com


Almost looks like the DNS is correct inside lan but not the Public DNS 
about public dns, I have domain and subdomais pointing to my wan ip port 80, correct????

PLEASE help

---

### Post by Thirtysixway on 2009-07-23
For forwarding to another computer, please see my post in this thread:
[http://ubuntuforums.org/showpost.php?p=7661367&postcount=2](http://ubuntuforums.org/showpost.php?p=7661367&postcount=2)

---

### Post by pmla on 2009-07-24
tried that and it's still not working.

"DocumentRoot /var/www/subdomainfolder" do you mean the document folder in the apache where the webiste is at? or just the subdomain sub2.example.com?


Basically when I try firefox from WAN I always end up in the sub1.example.com website.

when I sudo /etc/init.d/apache2 force-reload
 * Reloading web server config apache2                                          [Fri Jul 24 16:40:54 2009] [warn] VirtualHost 192.168.1.1:80 overlaps with VirtualHost 192.168.1.1:80, the first has precedence, perhaps you need a NameVirtualHost directive


Any help here?

---

### Post by pmla on 2009-07-25
Bump 1

---

### Post by pmla on 2009-07-25
Finally working ufffff:

»Using firefox from WAN: [www.example.com](www.example.com) shows correct website in my main LAN apache2 server

»Using firefox from WAN: sub1.example.com shows correct website in my main LAN apache2 server

»Using firefox from WAN: sub2.example.com shows correct website in my secondary LAN apache2 server that was forward from main apache server

Later on today I will post a small how-to for all the ubuntu user's having an hard time with this. After 3 days and a lot of google, I found that the online documentation is scarce and fragmented, relating to several distros or releases.... complete confusing mess. And as you guys may see here only **Thirtysixway tried to help with the proxy part. Just sucks**

1) How-to have multiple virtualhosts (domain/sub) responding from WAN/LAN using port 80.
2) Having a main apache2 server for several virutalhosts and also how-to forward 1 or more domain/subdomain internally from a main apache2 server to a secondary apache2 server.
2) So that from WAN all sites (domains/subdomains) use the same static Ip and port 80

Ubuntu 9.04
Forward router ports
Bind9dns and Public DNS
Apache version 2.2.11

---

### Post by Thirtysixway on 2009-07-25
There is documentation on all of these things floating around online.  While it took me a while to figure out mod_proxy, I wouldn't completely hate on the help that the forums give.

But I'm glad it worked out for you, hopefully my post was somewhat helpful :)

---

### Post by pmla on 2009-07-29
Since I had vhosts running have been building my new websites.
So, the how-to is not forgoten, just delayed a couple of days.

In any case I started a page about this in my website. You can read it there.

[website]("http://www.pmabox.com/index.php?option=com_content&view=article&id=19:apache-multiple-virtual-hosts&catid=10:iceland-blog&Itemid=16")

---


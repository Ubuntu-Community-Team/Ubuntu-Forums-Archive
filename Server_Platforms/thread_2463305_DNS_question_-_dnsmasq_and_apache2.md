---
title: "DNS question - dnsmasq and apache2"
date: 2021-06-08
forum: Server Platforms
---

### Post by spyhabs on 2021-06-08
Hello,

I'm new here and I want some help to understand a DNS concept.  I hope somebody could give me an answer ;)
 
[COLOR=#3C3B37][FONT=&quot]I installed a DNS server (dnsmasq) on a ubuntu server located at 192.168.1.4 (primary), 8.8.8.8 (Secondary).  And I also installed Apache2 to run a  http server in the same host (192.168.1.4).  Apache2, there's a default web page appeared if I type 192.168.1.4 in a browser.  Also, I added another site [gci.example.com]("https://gci.example.com/") in apache2.

So,
  if I type 192.168.1.4 in a browser, it appears the Apache default web page.
  if I enter [http://gci.example.com](http://gci.example.com), it shows up my gci http page.[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=&quot]My question![/FONT][/COLOR]
[COLOR=#3C3B37][FONT=&quot]I really don't understand how the DNS knows that [gci.example.com]("https://gci.example.com/") is 192.168.1.4.   I never specified this information in dnsmasq.conf.  So, how does it work exactly?  I am little bit confused here...[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=&quot]
Have a nice day!

[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=&quot]Thanks[/FONT][/COLOR]

---

### Post by TheFu on 2021-06-08
DNS is like the old telephone books.

name ---->  phone number
But telephone books only worked 1 way from the name to the phone number.

DNS works 2 ways - from the IP to the name and from the name to the IP.
DNS-hostname <---->  IP address

In general, it is a bad idea to have DNS running on a server also doing dangerous things like serving webpages or email. Those 3 servers are the 3 more hacked types of systems.  I've not had a web server hacked, but I have had my DNS server hacked - back in 2002.

As to how dnsmasq works specifically, I don't know.  I use Bind and disable any local dns caching tools on my LAN.

We servers have and old idea of virtual hosts. This was how we could have 3000 websites on a singly web server for the last 25+ yrs.  The requested name is understood by apache, used to lookup in all the apache sites-enabled/ config files for which ServerName the HTTP request should be sent.
```
   <VirtualHost *:80>
     ServerName wb.example.com
     DocumentRoot /var/www/wallabag/web
        .....
  </VirtualHost>
```
ServerName the HTTP request should be sent.

```
   <VirtualHost *:80>
     ServerName nc.example.com
     DocumentRoot /var/www/nextcloud
        .....
  </VirtualHost>
```
So, with both of those stanzas in the apache..../sites-enabled/ directory, we have to ask for either wb.example.com or nc.example.com for Apache to know which we want.

There is probably a default.conf file there too, which doesn't specify any ServerName.  That's were any requests that get to the apache server go which aren't in the 2 configured servernames.

DNS is separate from the Apache stuff. If DNS or the client running the web browser /etc/hosts points to the wrong IP address, then no requests will get there with the expected ServerNames, so nothing will be served.  If you don't want to worry about DNS, you can just put the name/IP pairs you want used into the /etc/hosts on your client system.

Hope I said that in a clear way. Hope some other people will help by clarifying what isn't clear in a different way.

---

### Post by spyhabs on 2021-06-08
Hi TheFu,

Yes it's not clear:) Sorry!  When I use Wireshark to sniff the communication, I see the DNS request gci.example.com to my DNS server 192.168.1.4 on port 53.  And port 53 is managed by dnsmasq server.  The answer from this DNS request is 192.168.1.4 (the web site).  So, I wonder if dnsmasq interrogates the apache database to know if the site is available?

Best regards,

---

### Post by TheFu on 2021-06-08
DNS doesn't read apache config files - ever.
Apache doesn't read DNS config files either.

Apache logs may make DNS requests like any other client for log files data. That's usually disabled for performance reasons. It is just for logging, not for the server.

---

### Post by LHammonds on 2021-06-09
> **spyhabs said:**
> When I use Wireshark to sniff the communication, I see the DNS request gci.example.com to my DNS server 192.168.1.4 on port 53.  And port 53 is managed by dnsmasq server.  The answer from this DNS request is 192.168.1.4 (the web site).

What is the result of these two commands?

```
cat /etc/hosts
cat /etc/hostname
```
I suspect you named the host "gci.example.com" which is why the DNS server would resolve gci.example.com to the server's IP address when on another machine whose DNS points to that DNS server (192.168.1.4)

So, if you add another domain name to apache such as my.mydomain.local, I bet the DNS server will not know how to resolve it.  You would have to add an entry into your DNS server to let it know to resolve my.mydomain.local to 192.168.1.4 and then other machines could resolve it to the correct web server and THEN apache could point the HTTP request to the correct site/folder.

LHammonds

---


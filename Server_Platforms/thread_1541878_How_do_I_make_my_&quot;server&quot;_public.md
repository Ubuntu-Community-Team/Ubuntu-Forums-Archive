---
title: "How do I make my &quot;server&quot; public?"
date: 2010-07-29
forum: Server Platforms
---

### Post by Brando753 on 2010-07-29
Hello everyone,
I have followed the instructions here on how to make a server:
[http://how2forge.net/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-2](http://how2forge.net/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-2)
The server works locally on my 192.168.1.101 however how do I get my stugo.co.cc domain, my txug.co.cc domain, and my mundotg.co.cc domain to point to my ip address? 68.99.111.11 

I understand I have to use bind dns however im having the hardest time getting it to work ... Also it will be a lamp and mail server.

Can someone please give me a good guide. O and port 80 is blocked so I need to use port 8000. 

Thanks a bunch.

---

### Post by arrrghhh on 2010-07-29
First off, is that 192.168.1.101 statically configured?  You may want to do that so the IP can't change.

As for your domains, have you spoken to your hosting provider?  They should be able to help you migrate the records.  Where were these domains pointed to previously?

---

### Post by bovcan on 2010-07-29
At your DNS service (zoneedit, dyndns) you need to point A record to your IP, NOT 192.168.1.101, this is your internal/lan IP but the other one.
Than you need to enter DNS or named server into your domain configuration(godaddy or anyone else, ehere you bought the domain).
Than, normaly you need to wait up to 48 hour to DNS servers refresh.

If you are using apache, open port 80 in your router.

---

### Post by Brando753 on 2010-07-29
Thank you everyone for responding so quickly,
To answer your questions:
yes I have 192.168.1.101 set up statically 
They wernt pointed anywhere previously
bovcan I was setting up bind dns, so to whom to I give my external ip?

do I paste this <68.99.111.11> (not actual ip) as the name server to my domain registrar or where? 

Thanks for the help everyone.

---

### Post by bovcan on 2010-07-30
Hm, do not know. I was trying to setup Bind DNS, but than I went to zoneedit.com(free), much easier than setup your own dns.
I suggest you to get a free DNS service becouse Bind DNs is not so simple.


At domain registar you need to enter named servers, this are servers from DNS serverice, like example ns1.zoneedit.com or ns1.dyndns.com, than you point your ext. IP to domain name (A record - yourdomain.com - your ext IP)

---

### Post by arrrghhh on 2010-07-30
Yea, if you have a dynamic WAN IP (you usually have to pay more $$$ for a static IP from your provider) you'll need some way to update DNS records.  I use dyndns, but there are tons of other services.

BIND9 is a little tricky, but doable.

---

### Post by sampaioneto on 2010-07-30
I'm guessing you are trying to serve a webpage using apache as webserver, also your ISP gave you an static IP(you must confirm this address)

cc.co must be able to point your free domains to your machine, some kind of internal configuration/webpanel might be available.

Once you do that you can easily check this using:

```
$ ping your.domain.tld
```

it must return 

```
PING your.domain.tld (68.99.111.11) 56(84) bytes of data.
```

This means that your domains are pointing to your machine.

now it's time to configure apache's virtualhosts:

```
<VirtualHost domain.com:8000>
    ServerName www.domain.com
    ServerAlias  www.domain.com domain.com
    DocumentRoot /var/www/domain.com
</VirtualHost>



<VirtualHost otherdomain.com:8000>
    ServerName www.otherdomain.com
    ServerAlias  www.otherdomain.com otherdomain.com
    DocumentRoot /var/www/otherdomain.com
</VirtualHost>
```

This might work really well,

I couldn't look deeply howtoforge's article, but that might be ok

---

### Post by Raymond2201 on 2010-07-30
check out ddclient

if your using dyndns your in luck, it was originally created for their services although i do believe more dynamic DNS services are supported now.

```
sudo apt-get install ddclient
```It will also allow you to point multiple domains to your single IP address and will auto update your IP address on the dyndns servers in the event you puiblic IP changes for any reason (move to a new ISP etc...)
Just forward port 8080 to your server box and you should be good to go.

hope this helps...

---

### Post by bovcan on 2010-07-30
Some router have in setting this to update IP to DNS(if dynamic IP), else you can DL client.

---

### Post by gordintoronto on 2010-07-30
co.cc is not your domain, so it will never point to your computer.

---

### Post by bovcan on 2010-07-30
What?
I have one co.cc domain and I host this domain on my server at home.

---


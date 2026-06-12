---
title: "Using Ubuntu Desktop edition to host website"
date: 2010-01-08
forum: Server Platforms
---

### Post by ooloo on 2010-01-08
I'm trying to setup my Ubuntu 9.10 laptop to host a small website that I can practice and learn stuff with and I'm a little stuck at the minute.

I have got Apache2 and the LAMP stack installed okay, along with phpMyAdmin and can give my external IP to anyone with the http:// and anyone can view my website that way but what I want to do is have my IP resolve into a domain name like ooloo-website.net but I don't know how to do this.

Is there any way that I can do this like register my IP to a free DNS and domain website without buying a domain or using one of those free ones like ooloo.webhost.net or do I need to host everything myself like DNS and the domain? Can I even do all of this myself?

Any help I'd really appreciate. I guess I don't know that much about this type of thing but this is why I'm trying to learn more and do all of this. 

Thanks in advanced.

---

### Post by HighCommander540 on 2010-01-08
> **ooloo said:**
> I'm trying to setup my Ubuntu 9.10 laptop to host a small website that I can practice and learn stuff with and I'm a little stuck at the minute.

I have got Apache2 and the LAMP stack installed okay, along with phpMyAdmin and can give my external IP to anyone with the http:// and anyone can view my website that way but what I want to do is have my IP resolve into a domain name like ooloo-website.net but I don't know how to do this.

Is there any way that I can do this like register my IP to a free DNS and domain website without buying a domain or using one of those free ones like ooloo.webhost.net or do I need to host everything myself like DNS and the domain? Can I even do all of this myself?

Any help I'd really appreciate. I guess I don't know that much about this type of thing but this is why I'm trying to learn more and do all of this. 

Thanks in advanced.

First, off. You can't host your own domain names. And to do what you are talking about you would have to buy a domain name. Unless you are ok with having a domain like ***.no-ip.org. Then sure. To do this just find any site willing to do a IP redirect for you.

Here are a few examples:

[http://www.no-ip.org]("http://www.no-ip.org")
[http://www.dyndns.com]("http://www.dyndns.com")
[http://www.opendns.com]("http://www.opendns.com")

There are a bunch of others. Just search for dynamic DNS. You would need to download and install their IP address updater if you have a dynamic IP address from your ISP.

---

### Post by stlsaint on 2010-01-10
yes if you have access to server you can use free hosting via dyndns.com
now if you want fqdn as in: [www.whateveryouwant.com](www.whateveryouwant.com) than yes you will need say godaddy.com or fivebean.net

---

### Post by noway2 on 2010-01-10
The service, dyndns can aslo register whatever-you-want.xzy domain name for you and will couple it with their DNS forwarding so that it will resolve to your server.  In this case, I can personally vouch for it as I use it for one of my domains.

---

### Post by guessswh0 on 2010-01-11
It's really only like 6-12 bucks a year to get a domain.  A dollar a month.  If you are wanting something good, then buy a domain.

---


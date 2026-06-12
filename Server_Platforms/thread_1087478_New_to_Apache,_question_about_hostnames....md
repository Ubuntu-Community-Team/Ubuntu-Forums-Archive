---
title: "New to Apache, question about hostnames..."
date: 2009-03-05
forum: Server Platforms
---

### Post by Sneaky07 on 2009-03-05
Hi I am new to Apache and was following this guide and just have a probably easy/noob question here.  I was following the guide:  [HOWTO Set up an Apache Web server for free]("http://ubuntuforums.org/showthread.php?t=632841&highlight=HOWTO+Apache")

Now I have an old Xbox with Xdsl on it and was told that I could run a Web server on it  EDIT: (Either that or an old PC).  I was planning on using Apache but I was just wondering how it would be possible to set up a hostname such as "www.hostname.com" like those for commercial sites.  
I was also reading [Identifying Your Site]("http://www.skandex.com/documentation/manual/manual.1d.html") and the other says, > Registering a Domain Name

If you are independent, then you can register your own domain, and use it for your WebSTAR server. Your ISP should be able to help you register it. As of the time of this writing, the Domain Name Registry in the United States is run by the InterNIC at:

    [http://rs.internic.net/rs-internic.html](http://rs.internic.net/rs-internic.html)

I'm not sure if I understand this correctly so I was just wondering if anyone had experience with, or went through the process of creating/registering hostnames like those of professional websites and could shed some light on it?  Any help would be appreciated.  Thanks!!

---

### Post by matey3 on 2009-03-05
I am not an expert but for what I have seen, you have to have a registered domain (name) so you can be part of the internet.
Otherwise you have to stay with your localhost (LAN).
May be some one else can shed more light on this subject?
good luck!

---

### Post by tornadof3 on 2009-03-05
[www.no-ip.com](www.no-ip.com) may provide the service you require, and DynDNS also do similar. You need to purchase a domain name (eg yourdomain.com) and then have a DNS record set up to make that domain name point to the IP address of this server you wish to set up.

Since there are lots of potential pitfalls along the way associated with whether your ISP will allow you to do this, you may wish to try one of No-IP's "free" packages, which I use extensively. They allow you to register a user account and then use one of their pre-existing domain names, eg username.oneoftheirdomains.com would point to your server. Also, your IP address may periodically change if you have a normal 'home' broadband internet connection. NoIP and dynDNS provide tools to update their records automatically.

---

### Post by Sneaky07 on 2009-03-05
So basically the only way you could have a hostname such as "www.hostname.com" would be to buy one or register it with your ISP?  I don't think I want to use those sites though because my main reason for putting up a site was to see if I could make a small business site.  I was just seeing how I could set it up the cheapest.

EDIT:  I think I did not understand hostnames before though.  I guess I will just have to buy one.

---


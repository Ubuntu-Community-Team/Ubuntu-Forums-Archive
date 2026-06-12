---
title: "Confused about Bind and configuration"
date: 2010-10-16
forum: Server Platforms
---

### Post by SirMeaky on 2010-10-16
Hey,
I've got my server up and running now and I can access my website using the IP address of the machine.  Now all that is left to do is to setup bind and get my domains all linked.

Now, I had this done on Windows Server and it worked fine (well  I could see my website using the URLs at least).  However with Bind I am lost.

**Bind**
I can install bind and that's as far as I can get without losing it.  I have tried to follow some tutorials but they didn't really explain in any detail.

I have 2 domains that I want to work with my server, we shall call them [www.site1.com]("http://www.site1.com") and [www.site2.com]("http://www.site2.com").  I have also purchased an additional domain to serve as a name server we shall call this [www.ns1.com]("http://www.ns1.com").

Now I am hoping someone will be able to shed some light on exactly how to configure all of this.  

I am running Ubuntu Server 9.04.

Thanks guys

---

### Post by James78 on 2010-10-16
Here's my quick crash course. We'll assume my domain name is domain.com, and domain.com's IP is 127.0.0.1, where ns1.domain.com and ns2.domain.com are also located at 127.0.0.1 (but can BOTH be pointing to completely different DNS server IP's).

1. My nameservers are ns1.domain.com and ns2.domain.com.
2. Now, with my domain host (in this case GoDaddy), I told them that ns1.domain.com and ns2.domain.com is located at 127.0.0.1.
3. Now that their servers know where my nameservers actually are, I tell them that for domain.com, my nameservers are ns1.domain.com and ns2.domain.com
4. Now that they're pointing to me, I create 2 NS records. My first NS record's name is domain.com. (notice trailing period) and has a value of ns1.domain.com. (<-- That's just the end of the sentence) My second NS record's name is domain.com. and has a value of ns2.domain.com.
5. Now I need to tell the DNS where my NS records actually point to. So I create an A record with a name of ns1.domain.com. (trailing period!) and a value of 127.0.0.1. (<-- end of sentence) Now I create a second A record with a name of ns2.domain.com. with a value of 127.0.0.1.
6. Now my NS configuration is done. Now I create an A record with a name of domain.com. which points to 127.0.0.1. I create a second record with a name of [www.domain.com](www.domain.com). which points to 127.0.0.1. In #8 we make a subdomain, so in addition to the main site DNS records, create an A record for sub.domain.com. pointing to 127.0.0.1 and an A record for [www.sub.domain.com](www.sub.domain.com). pointing to 127.0.0.1.
7. I made sure my VHost (127.0.0.1:80) has a document root and a ServerName (domain.com) and a ServerAlias ([www.domain.com](www.domain.com)). I restart BIND and Apache, and wait about 30 minutes for the cache to catch up. Now I can access my site (GoDaddy's cache also needs to catch up, this can take a few days in some cases).
8. I create a second VHost (127.0.0.1:80) with a ServerName of sub.domain.com and a ServerAlias of [www.sub.domain.com](www.sub.domain.com), with a document root at /home/mysiteuser/domains/sub.domain.com/public_html, or /var/www/sub.domain.com, or anywhere really
9. I now have a main domain, and a subdomain. Have fun! :)

---

### Post by SirMeaky on 2010-10-16
Awesome, that helped a lot thanks :D

Why can't everyone do that instead of including all of the unneeded parts!

Thanks again ^_^

---

### Post by James78 on 2010-10-16
It would seem I forgot 1 step for ya. For the subdomain, you need to have an A record for sub.domain.com. pointing to 127.0.0.1, and an A record for [www.sub.domain.com](www.sub.domain.com). pointing at 127.0.0.1, just like in step #6 (an A record pointing to the IP of every single domain, and subdomain basically. Each site has it's own zone of course. I assumed you already have your in-addr.arpa stuff setup.) :)

---


---
title: "DYNDNS and bind"
date: 2008-06-07
forum: Server Platforms
---

### Post by ianb72 on 2008-06-07
I have set up a LAMP server and installed webmin and everything needed for people to access my website via my IP address and ftp it too.

My question is now I think I am ready to purchase a domain name, lets say [www.mydomain.co.uk](www.mydomain.co.uk), how do I go about setting it up in webmin and can I set up a DNS on my server even though I don't have a static IP from my ISP, or will I have to register with someone like DYNDNS.ORG??

I've heard that not everyone will be able to access the site if its redirected and as its for my local rugby club I want everyone to be able to get access, as some will access the site from their place of work!

I also then want to add extra domain names at a later date, I have also contacted my ISP and their so called technical services about getting a static IP Address but I was told they don't offer these.

Thanks in Advance
Ian

---

### Post by azadpanchi on 2008-07-25
I would not recommed hosting your own name servers if you do not have a static ip address.  You can use dyndns.org and other similar options and where ever you maybe hosting your name servers you can create CNAME records for any hosts and point it to your dyndns.org address.  Most registrars offer complementary use of their name servers.

If instructions seem vague please feel free to update this post.

---


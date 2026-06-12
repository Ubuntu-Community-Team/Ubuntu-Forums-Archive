---
title: "Intranet Site and DNS"
date: 2012-08-30
forum: Server Platforms
---

### Post by Delarth on 2012-08-30
I've tried searching all over the web for some sort of solution to the problem I am currently having. I am using the latest version of Ubuntu Server 64-bit, I think its 12.04.

What I want to do is have an intranet site hosted on this server that people on my network can access by typing in something like (site).internal I have the site setup on Apache, I created an A record in Bind along with setting it up following the steps i[n this guide]("https://help.ubuntu.com/10.04/serverguide/dns-configuration.html"). When I type in the local IP address it works just fine but not when I try to use (site).internal In the Apache files the server name and server alias both reflect what I want the site name to be.

Is there something I still have to change server side or might I have to change something within my router instead so it knows that the Ubuntu server is a DNS as well?

---

### Post by kennethconn on 2012-08-30
Do your clients know to use that server for DNS?

---

### Post by darkod on 2012-08-30
> **Delarth said:**
> 

  or might I have to change something within my router instead so it knows that the Ubuntu server is a DNS as well?

As the previous posted mentioned, your guess is right. If your server is not set up as primary DNS for the computers on your network, there is no DNS server that can resolve site.internal for them.

Enter the router or dhcp server options, and in the DNS set the apache server private IP to be primary option. For secondary option you can set any public DNS or the router IP.

Some of the clients might need to release and renew the lease to get these new settings. Once they do, it should work provided your bind is set up correctly.

---

### Post by Delarth on 2012-08-30
Your solutions worked well. I altered the router DNS settings and now I can access the site but I have one small lingering problem. If I put in the www then it fails to find the website. Under the /etc/apache2/sites-available/(site) file I have the ServerAlias set as *.site.internal and I assume this should work. Is there another place I need to put the ServerAlias directive?


Edit:
I had to update the DNS records and add in a CNAME for the site and things are working.

---

### Post by darkod on 2012-08-30
You need something like:
www CNAME site.internal

in bind. It doesn't matter what apache has, it's the DNS service (bind) that needs to know what www is. I don't have experience with bind so the above might not be the exact syntax, just a guide. Check the exact syntax you need to use.

---

### Post by Doug S on 2012-08-31
Actually, it is preferred practise to use "A" records instead of CNAME records, when you can. Yes, the majority of the references you will find suggest to use CNAME for www.

---


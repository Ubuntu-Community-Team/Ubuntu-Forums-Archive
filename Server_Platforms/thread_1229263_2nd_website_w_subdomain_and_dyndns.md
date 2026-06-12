---
title: "2nd website w/ subdomain and dyndns"
date: 2009-08-01
forum: Server Platforms
---

### Post by Mykle87 on 2009-08-01
I want to host a website for a friend on my machine as a subdomain of my dyndns (friend.mydyndns.com). I have LAMP and dyndns installed. When I test apache on my lan, I see "it works!" I created a site in sites-available and linked it. Here is what the file looks like:
```

<VirtualHost *:80>
  ServerName friend
  ServerAlias friend.localhost
  DocumentRoot /home/friend/www

```

When I go to friend.local IP address, nothing happens. What am I missing? Also, will this work with my dyndns? Thanks.

---

### Post by jamesrfla on 2009-08-01
It should work with DynDNS. I never had to play around with Virtual Hosts when I setup my server and used DynDNS. Did you try port forwarding port 80 in your router? Some ISP's don't even allow you to host web servers.

---

### Post by Thirtysixway on 2009-08-02
..can you have subdomains on IP addresses?

---

### Post by jamesrfla on 2009-08-02
> **Thirtysixway said:**
> ..can you have subdomains on IP addresses?

Yeah I believe so. I have a sub domain routed to a IP address.

---

### Post by Mykle87 on 2009-08-02
I have the first website working which is the default apache2 page. All I want is for  the 2nd site to have the address friend.mydyndns.com. Is this possible?

---

### Post by cmwslw on 2009-08-02
I had trouble with this when I was beginning with a server. Once I figured it out I wrote up a guide: [URL="http://me.clustur.com/node/24"]
Apache subdomains with DynDNS or No-IP[/URL]. I really hope this helps you :)

-Cory

---

### Post by Mykle87 on 2009-08-02
It looks like wildcards is a pay-for option with DynDNS. Looks like I'll have to go back to the drawing board. 

How about this situation:
I use my dyndns to access my server functions (sftp, transmission, subversion) from the internet. What if I buy a domain name from GoDaddy and use that for just a website on the same server? Is that possible?

---

### Post by Mykle87 on 2009-08-02
When I type my server's hostname (which is "server" on my lan) in firefox, I see the default webpage. I cannot figure out how to even host another separate website. Any help is greatly appreciated.

---

### Post by jamesrfla on 2009-08-02
The guide that cmwslw provided looks like it will help. Having one of your web sites on a DynDNS and the other site on a real domain might work.

---

### Post by Mykle87 on 2009-08-02
That doesn't seem to work. If anyone has the patience to walk me through this step by step, I would greatly appreciate it.

---

### Post by confusedstingray on 2009-08-02
for you want you should not need another domain just reconfigure apache to do virtualnamedhosting here is a link from apaches to explain and how to 

what you do have your internet ip (via router) point to an internal ip (which is your apache machine) and setup apache from below below 


[http://httpd.apache.org/docs/2.0/vhosts/name-based.html](http://httpd.apache.org/docs/2.0/vhosts/name-based.html)

---


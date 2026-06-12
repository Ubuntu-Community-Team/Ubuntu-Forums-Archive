---
title: "how to config apache to run ssl for specified folder"
date: 2008-08-02
forum: Server Platforms
---

### Post by taicyber on 2008-08-02
I have modified ssl.conf to run ssl cert.
But I want to run it for specified folder 
not whole website in order to save my cpu's work.

How to do this? I have talked with server admin,
he said this is a programmer's work not server admin's work.


thanks in advance for answer.

---

### Post by Dedoimedo on 2008-08-02
Hi,

You can use VirtualHost for that. This will allow you to separate content. I think the best idea would be to create a virtual network adapter, something like eth0:1, give it a separate IP and host the secure server on it, thus separating the non-secure and secure content.

Please remember you must use an IP-based virtual host for the secure server.

Coincidentally, I've written a huge guide on Apache - link in my sig, you'll find your answer there.

Cheers,
Dedoimedo

---

### Post by taicyber on 2008-08-02
thank you for very much for fast reply.
I just read you book.Apahce server complete guide.
You wrote that <Location> is for Urls.
Can I use something like this?

<Location "/var/www/html/secure area">
SSLVerifyclient require
SSLVerifyDepth 1
</Location>

At this time, I do not want to change anything like eth0 or any.
I just want to try to modify ssl.conf if it does not work I will think about your idea.

---

### Post by Dedoimedo on 2008-08-02
Hi,

First, I don't think "secure area" with the space in it is a good idea. Never use spaces in URL names.

Second, Location is for non-filesystem content, in other words, stuff (files and directories) that does not physically reside on the server. Yet, you pointed to /var/www ... which is usually the DocumentRoot, i.e. it does reside on the filesystem.

From the Apache website:

"...It is important to never use <Location> when trying to restrict access to objects in the filesystem. This is because many different webspace locations (URLs) could map to the same filesystem location, allowing your restrictions to be circumvented..."

[http://httpd.apache.org/docs/2.0/sections.html](http://httpd.apache.org/docs/2.0/sections.html)

Under, what to use when ...

Third, I don't think it will work - and it's definitely not the optimal way of doing things. Use the virtual hosts, they are specifically made to separate content and allow modularity.

If you really want security + fully working setup, there are no shortcuts.

Cheers,
Dedoimedo

---

### Post by taicyber on 2008-08-02
thanks again for fast reply.

In virtual host, I have to define DocumentRoot again?
Or have to do something more than default setting?

I wonder how the shopping website do this, when I went to 
their website I used http:// but when I had to pay I forced
to use https://

---

### Post by windependence on 2008-08-02
> **Dedoimedo said:**
> 

Please remember you must use an IP-based virtual host for the secure server.


Actually he can run just one named based virtual host as the secure server. With IP based he could run several.

> You can, of course, use Name-Based Virtual Hosting to identify many non-SSL virtual hosts (all on port 80, for example) and then have a single SSL virtual host (on port 443). But if you do this, you must make sure to put the non-SSL port number on the NameVirtualHost directive, e.g.

```
NameVirtualHost 192.168.1.1:80
```

Other workaround solutions include:

Using separate IP addresses for different SSL hosts. Using different port numbers for different SSL hosts.

[http://httpd.apache.org/docs/2.0/ssl/ssl_faq.html#vhosts](http://httpd.apache.org/docs/2.0/ssl/ssl_faq.html#vhosts)

-Tim

---

### Post by Dedoimedo on 2008-08-02
Hello,

It's a possibility, albeit a more complicated one, imho ...

Considering that servers could quite often change IP, plus the fact he might want to use a single port for secure connections, using several IPs seems like the best solution.

That's what I'd do at least ...

Dedoimedo

---

### Post by windependence on 2008-08-02
A server on the LAN shoul NEVER change IP. They should be set up static unless there is a good reason for it.

And yes, of course he would probably want to use port 443. What is your point here? If he just needs one host this is a no brainer.


-Tim

---

### Post by Dedoimedo on 2008-08-02
Hello,

I don't wish to fight - it's not the Ubuntu way.

Reading back, I don't see the OP mentioning a LAN environment. Besides, you confirmed what I wanted to say in the first place - use IPs for servers...

Let's focus on helping the chap here and not bicker. I premeditatedly intend to lose any e-battle ...

Have a good day,
Dedoimedo

---

### Post by windependence on 2008-08-02
I'm not fighting at all, just giving him all his options. You are not understanding when I say static IP, I am talking on his LAN, his server needs a static IP. The whole idea behind named based hosts is that you can use just one external IP (because they are expensive) and serve 100s of sites from it.

In this case if he assigns his server a static *internal* IP, he can do at least one SSL host on 443 or whatever port he wants. In fact, according to the Apache docs, he should be able to do more than one IF he uses different ports, that's all I was saying. :)

-Tim

---

### Post by Dedoimedo on 2008-08-02
Hello,
And you are correct! But this may not be the simplest solution for him, or the most flexible one... but it is definitely an option.
Dedoimedo

---

### Post by taicyber on 2008-08-03
Thank you very much Dedoimedo and windependence for your idea and solution.

I am a newbie of server administrator. 
Let me explain my server environment.

2 servers with DRBD + Hearbeat (2 NICs one for external another for internal especially for drbd)
Apache 2.2.4
PHP5
Mysql5

After I read your dicussion about my problem, it seems that
I have to use ip address for ssl virtual host. That means I have 
to buy two more ip address for these servers?

Thanks again.

---

### Post by Dedoimedo on 2008-08-03
Hi,

Two options that I can think of:

1. Buy more IPs.

2. You can create a virtual network address and give it a local IP, then forward requests to and fro between the external and internal network, possibly including firewall rules as well.

Option 2 is more complicated, and you'll have to make sure the DNS resolution works properly for all addresses and domains ... but it is cheaper.

Option 1 is more expensive, but is simpler to configure ...

Your choice.

Cheers,
Dedoimedo

---

### Post by windependence on 2008-08-03
Aye Caramba, you don't quit do you? 

All he needs to do is set up a LAN, like everyone else on the planet does and NAT his network so that he has private addresses for his servers. Viola! Problem solved. he does not need to buy any external IPs at all.

All he needs to do this is in post #6.

-Tim

---


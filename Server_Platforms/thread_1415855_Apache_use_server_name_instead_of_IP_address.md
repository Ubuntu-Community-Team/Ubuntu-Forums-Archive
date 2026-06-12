---
title: "Apache use server name instead of IP address"
date: 2010-02-25
forum: Server Platforms
---

### Post by dsmith1337 on 2010-02-25
Ok i'm a bit of a noob with Linux server and I'm gonna try and explain this as simply as I can. I've setup a Ubuntu 9.10 LAMP server to host a word press blog on an intranet. I've got everything working except the url for the site.

The IP address of the server will take me to the site **[http://192.168.1.100/](http://192.168.1.100/)**

But I'd rather use the server's name instead of the IP address [B][http://west-tech-srv/](http://west-tech-srv/)

[/B]When i try to go to **[http://west-tech-srv/](http://west-tech-srv/)** in Firefox or IE it give me a server not found page and changes the URL to** [http://www.west-tech-srv.com/](http://www.west-tech-srv.com/). **I also have Webmin installed on the server and I've been playing around with the Apache module and can't figure out how to set it so i can use the server name instead of the IP address to get to the site. Any help is appreciated.

---

### Post by noway2 on 2010-02-25
You need to have your server registered with a dns.  You should be able to do this with the company that registered your domain.  You need to have you public ip addr identifiable.  Plenty of threads in this forum to get you started.  Look for dns and check out dyndns.  You can do this for free, by the way.

---

### Post by Vishal Agarwal on 2010-02-25
Basically your client computer is searching for the DNS name for your server **[http://west-tech-srv/](http://west-tech-srv/)**. And it is not getting that name resolved. that's why simply your internet explorer is unable to reach to your server. And when you are providing the IP address, there is no need to reverse or resolve the ip address. And your client compuyer cn reach to your server.

---

### Post by cdenley on 2010-02-25
On the system you are trying to browse your site on, add a line to /etc/hosts which looks like:
```

192.168.1.100 west-tech-srv

```

This will force that computer to resolve that hostname to the server's LAN IP.

---

### Post by dsmith1337 on 2010-02-25
Thank you all. I got it working now.

---

### Post by noway2 on 2010-02-25
Just to be sure you understood.  If you take the approach of adding the entry to your hosts table, only that one PC will be able to access the site by name.  The public will not be able to access it, nor will you be able to access it remotely.  This does not solve the problem of making it discoverable.  For that you DO need a DNS solution.

---

### Post by Vegan on 2010-02-25
I installed BIND9 to take care of my DNS needs, works fine once you learn how to use it properly.

I use it as a secondary DNS and when I make changes to my LAN topology I have my servers all working immediately.

---


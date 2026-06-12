---
title: "web server &amp; domain setup in ubuntu8.10"
date: 2008-11-05
forum: Server Platforms
---

### Post by thekid on 2008-11-05
Hi,

I have ubuntu server 8.10 installed and I have a dedicated internet connection and a domain name. I want to hosting some websites with that server. I know how to get set up LAMP. But I am not too sure how to set up the ubuntu so that it can host my domain names. 

Would setting up a DNS be the only thing I need to have my domain [http://www.something.com](http://www.something.com) pointed to my server? (I know how to change the nameserver etc from godaddy, where my domain name is registered). 

Basically I want to tie my domain name to a server running ubuntu8.10 with a static IP. 

Thanks in advance.

---

### Post by williehowe on 2008-11-05
You could use the default website, if that is the only domain you want to host.  You'll need to setup DNS to point to your IP, and if you're behind a router, you'll have to forward the appropriate ports.  If you have a static IP, you could host your own dns.  If you did that, you would just have to open port 53 and 80 on your firewall and forward them to your Ubuntu server.

---


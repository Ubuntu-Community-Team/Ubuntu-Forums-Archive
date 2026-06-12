---
title: "Two web servers"
date: 2006-04-27
forum: Server Platforms
---

### Post by xinman on 2006-04-27
Ok, I have two boxes one that sits on the outside IP and one that is visible only on the local network, both running Ubuntu.
The one on the outside IP has a web server and dns server setup.  The one on the inside has a web server setup.  What I would like to do is make a subdomain that will redirect it to the other web server.  Is this possible without making it run on a diffrent port and using NAT rules to make it work?

---

### Post by montecore on 2006-04-28
I'm not exactly sure what your asking but I have a feeling that setting up some redirects on the internal web server will do what you want.

[http://httpd.apache.org/docs/2.2/mod/mod_alias.html#redirect](http://httpd.apache.org/docs/2.2/mod/mod_alias.html#redirect)

---

### Post by xinman on 2006-04-30
It's similar to what I want, what I'm looking for is to make something like this:

sub.domain.com -> point to an internal address using a gateway (outside IP)

Both of these are running ubuntu 5.10

Any thoughts on how to do this, if it's possible with one outside IP?

Thanks

---

### Post by Koybe on 2006-05-01
I think you should go for a Name-based Virtual Host. Everything should work properly. 
Here's the documentation : [http://httpd.apache.org/docs/2.0/en/vhosts/name-based.html](http://httpd.apache.org/docs/2.0/en/vhosts/name-based.html)
And a good howto from gentoo distribution : [http://gentoo-wiki.com/HOWTO_Apache_VirtualHost_by_IP_Address](http://gentoo-wiki.com/HOWTO_Apache_VirtualHost_by_IP_Address)

---

### Post by xinman on 2006-05-03
Thanks Koybe, I'm not sure that will actually do want I want.  I've decided it's not a huge deal, if I can get it I get it, but if not I'm not going to lose sleep over it.  I'll sketch out a diagram of what I'm trying for, but like I said it's not a huge deal.  It would be very nice though.

sub.domain.com  ->  10.1.2.3 webserver

sub2.domain.com -> 10.1.2.3 (Gateway) -> 192.168.2.3 webserver

I still think I have to do it with some sort of proxy server or iptables.

Any other thoughts would be nice.

---

### Post by Koybe on 2006-05-08
Yes you'll probably have NAT. So make your second web server listening another port then the port 80. And forward it from your gateway.
If you're already nating, something like that should work :
```
iptables -t nat -A PREROUTING -i $IP_INTERNET -p tcp --dport 81 --to-dest 192.168.2.3 -j REDIRECT --to-port 81
```

---


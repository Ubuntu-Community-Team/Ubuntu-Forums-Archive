---
title: "Having Apache listen only local network machines"
date: 2009-06-02
forum: Server Platforms
---

### Post by OMA2k on 2009-06-02
Hello all. I'm searching for a way to make Apache reject connections from the Internet but accept local network connections (not only from localhost, but also other machines in the network) for an Intranet type application. 

The server will be running in a tablet with Netbook Remix, so it's a small server for only a few users (less than 5, probably). Any other security recommendation for this environment apart from blocking external traffic?

Thank you!

---

### Post by Alekz_ on 2009-06-02
Assuming that you have two network interfaces (one for LAN and another for WAN), you just need to edit your httpd.conf and let your LAN address listening.

i.e.
```
Listen 192.168.0.10:80
```

It is ONE way.. :)

---

### Post by cdenley on 2009-06-02
> **Alekz_ said:**
> Assuming that you have two network interfaces (one for LAN and another for WAN), you just need to edit your httpd.conf and let your LAN address listening.

i.e.
```
Listen 192.168.0.10:80
```

It is ONE way.. :)

Actually, in ubuntu, that would belong in /etc/apache2/ports.conf.

---

### Post by Alekz_ on 2009-06-02
Really? I'm still using httpd.conf...

Maybe a different release..

But thanks anyway! :D

---

### Post by Iowan on 2009-06-02
It's not OFFICIAL unless it includes a [link]("https://help.ubuntu.com/community/ApacheMySQLPHP#Securing%20Apache") ;)

---

### Post by Alekz_ on 2009-06-03
Nice Iowan! Tnks! :)

---

### Post by v3xtra on 2009-06-03
Could you do 192.168.0.*:80 for any machine on your local intranet?  Or would that not work?

---

### Post by cdenley on 2009-06-03
> **v3xtra said:**
> Could you do 192.168.0.*:80 for any machine on your local intranet?  Or would that not work?

That would not work with a "Listen" statement. You are telling apache which interface to listen for connections on, not which addresses to accept connections from. You can use access controls with Order, Allow, and Deny.
[http://httpd.apache.org/docs/2.2/howto/access.html](http://httpd.apache.org/docs/2.2/howto/access.html)
That would probably belong in your site configuration. (/etc/apache2/sites-available/default)

---


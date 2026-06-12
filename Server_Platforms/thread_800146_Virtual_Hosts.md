---
title: "Virtual Hosts"
date: 2008-05-19
forum: Server Platforms
---

### Post by diasje on 2008-05-19
I am running a ubuntu webserver apache2 on my company.

And i wold like o user several virtual hosts.

My server extruture:

/var/www/forum1
/var/www/forum2
/var/www/fileman
/var/www/website

My computer (server) name is jednet.

I wold like to use virtual hosts like:

/var/www/forum1 = _[http://forum1](http://forum1)_ or _[http://forum1.jednet](http://forum1.jednet)_
/var/www/forum2 = _[http://forum2](http://forum2)_ or _[http://forum2.jednet](http://forum2.jednet)_
/var/www/fileman = _[http://fileman](http://fileman)_ or _[http://fileman.jednet](http://fileman.jednet)_
/var/www/website = _[http://jednet](http://jednet)_


Is it possible?

I found a lot of tutorials about virtual hosts, but all of them are about registered domains.

---

### Post by jpeddicord on 2008-05-19
You can set them up the same way as a VirtualHost with a TLD, but keep in mind they won't be visible at all to the rest of the world, just the server LAN. Which probably isn't much. If that's all right with you, here's a sample vhost config with a non-TLD domain:

```
<VirtualHost *>
        ServerName forum1
        ServerAlias forum1.jednet
        DocumentRoot /var/www/forum1
        
        [...]
</VirtualHost>

```

---

### Post by diasje on 2008-05-19
Thats exactly what i whant, its just for my company, not for the www.

So as you say, its possible to use:

<VirtualHost *>
        ServerName forum1
        ServerAlias forum1.jednet
        DocumentRoot /var/www/forum1
        
        [...]
</VirtualHost>

or

<VirtualHost *>
        ServerName forum1
        ServerAlias forum1
        DocumentRoot /var/www/forum1
        
        [...]
</VirtualHost>

Keep in mind that my server or host name is jednet.

---

### Post by jpeddicord on 2008-05-19
> **diasje said:**
> Thats exactly what i whant, its just for my company, not for the www.

So as you say, its possible to use:

<VirtualHost *>
        ServerName forum1
        ServerAlias forum1.jednet
        DocumentRoot /var/www/forum1
        
        [...]
</VirtualHost>

or

<VirtualHost *>
        ServerName forum1
        ServerAlias forum1
        DocumentRoot /var/www/forum1
        
        [...]
</VirtualHost>

Keep in mind that my server or host name is jednet.

The first will suffice. ServerAlias lets you define alternative names to access the site by, so you can even remove that line entirely if needed.

---

### Post by diasje on 2008-05-20
Thanks man, i will try this today ;)

---


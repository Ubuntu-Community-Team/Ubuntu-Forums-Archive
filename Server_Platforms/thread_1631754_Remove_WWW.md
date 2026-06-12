---
title: "Remove WWW"
date: 2010-11-27
forum: Server Platforms
---

### Post by Smart_Viral on 2010-11-27
i have added a domain to my new vps account
but i notice that the website doesn't work with www
so how can i redirect [www.example.com](www.example.com) to example.com

(bind9, apache2, webmin, ubuntu server 10.04 lts)

---

### Post by James78 on 2010-11-27
See if this does the trick for you. (Add it either to the .htaccess in your public_html root, or add it to your sites apache config)
```
RewriteEngine On
RewriteCond %{HTTP_HOST} ^www\.example\.com$
RewriteRule ^/?(.*) http://example.com/$1 [R=301,L]
```

---

### Post by SeijiSensei on 2010-11-27
Before you add rewrite rules, you first need to determine whether [www.example.com](www.example.com) actually points to your server.  In your DNS zone, is there a record for [www.example.com](www.example.com) that points to the same IP address as example.com?

In Apache, the simplest method to support multiple names for the same server is to use the "ServerAlias" directive in your <VirtualHost> containter like this:

```

ServerName     example.com
ServerAlias    www.example.com

```

If you use ServerAlias you shouldn't need to use the rewriting rules James78 suggests.

---

### Post by James78 on 2010-11-27
> **SeijiSensei said:**
> Before you add rewrite rules, you first need to determine whether [www.example.com](www.example.com) actually points to your server.  In your DNS zone, is there a record for [www.example.com](www.example.com) that points to the same IP address as example.com?

In Apache, the simplest method to support multiple names for the same server is to use the "ServerAlias" directive in your <VirtualHost> containter like this:

```

ServerName     example.com
ServerAlias    www.example.com

```

**If you use ServerAlias you shouldn't need to use the rewriting rules James78 suggests.**
That's correct. Although in many cases, from an SEO standpoint, it's still a good idea to redirect to either example.com or [www.example.com](www.example.com), but not have them both accessible.

---

### Post by SeijiSensei on 2010-11-27
I guess.  Most people running servers here are still a long way from worrying about search engine optimization.  Usually I just advertise the [www.example.com](www.example.com) address and support example.com as an alias for people who forget and leave off the www part.

---

### Post by windependence on 2010-11-27
The correct way to do this is to set up a CNAME in DNS for the www address.
 
-Tim

---

### Post by czr114 on 2010-11-27
This:

> **windependence said:**
> The correct way to do this is to set up a CNAME in DNS for the www address.
 
-Tim

---

### Post by Vegan on 2010-11-27
The way I have my domains setup I use an A record with my DNS and a CNAME for the www subdomain.

In Apache, I use the non-www as the site domain and the www version is the alias

---

### Post by SeijiSensei on 2010-11-27
> **windependence said:**
> The correct way to do this is to set up a CNAME in DNS for the www address.
 
-Tim

True, but you still need to set up virtual hosting in Apache to support both versions.  

There are also times when you can't use a CNAME.  For instance, if you send mail for the www.example.com host to a different MX server than the default for example.com, BIND will complain about and not load a zone file like this:

**This example is wrong for illustration purposes!**
```

www      IN   CNAME   example.com.
         IN   MX      0 some.mail.host.
         IN   MX      5 another.mail.host.

```

You must give www an A record to specify MX hosts for the name.

---

### Post by iNsOmNiOuS on 2010-11-27
I also had this problem, I pointed mysite.com and [www.mysite.com](www.mysite.com) to my servers IP, then in /etc/hosts I added a line for both, and all worked fine !

---

### Post by Smart_Viral on 2010-11-29
i figured out that i must use an external proxy to test,
the [www.example.com](www.example.com) dns update needed 11 hours while example.com took 1 hour

thanks a lot

---


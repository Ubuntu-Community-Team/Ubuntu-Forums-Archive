---
title: "can i host several domains virtualhosts on one ip with apache"
date: 2011-12-06
forum: Server Platforms
---

### Post by rubo77 on 2011-12-06
i want to host several domains on a private root server, on the same IP. is this possible? 
(i know its not 100% secure, but i dont care about the warning, that it has no valid certificate, i just want to have the data transferred encrypted)


i get the warning


```
[warn] VirtualHost X.X.X.X overlaps with VirtualHost X.X.X.X, the first has precedence, perhaps you need a NameVirtualHost directive

```

how must i setup the config file for the virtualhoss?

---

### Post by prodigy_ on 2011-12-06
Yes, you can:
[http://httpd.apache.org/docs/2.2/vhosts/name-based.html](http://httpd.apache.org/docs/2.2/vhosts/name-based.html)

---

### Post by rubo77 on 2011-12-06
cool thank you,

i just added 
```
NameVirtualHost *:443
```

to the top of my last conf file in 
```
/etc/apache2/sites-enabled
```

---

### Post by SeijiSensei on 2011-12-06
> **rubo77 said:**
> i just added 
```
NameVirtualHost *:443
```


Just a warning that name-based virtual hosts don't get along well with HTTPS, even using a wildcard certificate.  In the past the rule has been one secure server per IP address.  Name-based virtual hosting works fine on HTTP sites with "*:80" instead of "*:443".

---


---
title: "URL redirect in apache2"
date: 2008-02-20
forum: Server Platforms
---

### Post by palcica on 2008-02-20
Ok, my problem is that ia have 2 servers. One is a webserver with apache2 and the other one is a exchange mail server with OWA only ssl suport.
Now I have a problem in apache2 redirection... how to redirect [http://mail.domain.com](http://mail.domain.com) on apache to [https://domain.com/exchange](https://domain.com/exchange) on exchange. The solution on iis webserver is very simple but on apache.... :confused:

---

### Post by cdenley on 2008-02-20
First, run this command to enable the required module.
```

sudo a2enmod rewrite

```

Then add this to your vhost config, within the VirtualHost tag.
```

RewriteEngine On
RewriteRule (.*) https://domain.com/exchange

```

If you don't already have a vhost configuration for mail.domain.com, then create this file:
/etc/apache2/sites-available/mail
```
<VirtualHost *>
        ServerName mail.domain.com
        RewriteEngine On
        RewriteRule (.*) https://domain.com/exchange
</VirtualHost>
```
...then enable it
```

sudo a2ensite mail

```

Restart apache, and it should work.
```

sudo /etc/init.d/apache2 restart

```

> The solution on iis webserver is very simple but on apache....
If you want simple, use IIS. If you want secure and efficient, use apache.

---

### Post by OffAxis on 2008-02-20
instead of 
> sudo ln -s /etc/apache2/mods-available/rewrite.load /etc/apache2/mods-enabled/rewrite.load

you could also use
```

sudo a2enmod
-->rewrite

```

which provides a slightly easier mechanism for mod linking.

---


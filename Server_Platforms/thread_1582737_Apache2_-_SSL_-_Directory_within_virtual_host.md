---
title: "Apache2 - SSL - Directory within virtual host"
date: 2010-09-26
forum: Server Platforms
---

### Post by riverty on 2010-09-26
Hello, thanks for reading!

I'm trying to figure out how (or if it's even possible) to declare a particular directory within a virtual host for SSL encryption. If so, how?

My setup: Ubuntu 10.04 Server / ISPConfig / Apache2 / PHP5

ISPConfig has setup Apache for virtual hosts and seems to be working fine however, it seems one can only turn on SSL for the whole virtual host. With or without ISPConfig, I would like to know if I can turn on a specific directory within the virtual host for SSL only rather than the whole site. So far, I have been trying to accomplish this by declaring a directory within the sample.net.vhost file without much success. Seems to me we should be able to do this but maybe not. My searching has turned up plenty on how to turn on SSL for a whole host but I have found nothing about turning on SSL for a directory within a host

If you are an admin, and you have a website for a host where 40% does not need SSL, and 60% needs SSL, but it's for the same host, how does one go about getting that accomplished? Maybe I'm thinking the wrong way about this?

Thanks for your time!

---

### Post by SeijiSensei on 2010-09-26
Because of the way SSL works, [each secure virtual host must have a separate IP address]("http://httpd.apache.org/docs/2.0/vhosts/name-based.html").  You can't create secure hosts with just the NameVirtualHost method where all the virtuals share a single IP.

So you can create a secure virtualhost using a stanza that starts with "<VirtualHost 192.168.1.1:443>", but any additional secure VHs would need a unique address before the colon.

That's easy enough to accomplish in Linux where you can create multiple virtual interfaces eth0:0, eth0:1, eth0:2, etc., and assign them each a unique address, but your ISP has to route all those addresses to you.  If you want to support multiple secure hosts, you'll need to get a range of IP addresses, typically called a "subnet," from your ISP.  They usually come in quantities of 6, 14, or 30 addresses because of the way subnetting works.

---

### Post by riverty on 2010-09-27
I understand and that's fine. But I only have 1 host that I want SSL so no problem there. What I want to do is something like this:

/etc/apache2/sites-available/example.com.vhost

```

<VirtualHost *:80>

        ServerAdmin admin@example.com
        ServerName example.com
        ServerAlias www.example.com

        DocumentRoot /var/www/example.com/web/

        <Directory /var/www/example.com/web/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

</VirtualHost>

<VirtualHost *:443>

        ServerAdmin admin@example.com
        ServerName example.com
        ServerAlias www.example.com

        DocumentRoot /var/www/example.com/web/ssl/

        <Directory /var/www/example.com/web/ssl/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

</VirtualHost>

```

- or - perhaps something like this:

/etc/apache2/sites-available/example.com.vhost

```

<VirtualHost *:80>

        ServerAdmin admin@example.com
        ServerName example.com
        ServerAlias www.example.com

        DocumentRoot /var/www/example.com/web/

        <Directory /var/www/example.com/web/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

         <VirtualHost *:443>

             ServerAdmin admin@example.com
             ServerName example.com
             ServerAlias www.example.com

            DocumentRoot /var/www/example.com/web/ssl/

        <Directory /var/www/example.com/web/ssl/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        </VirtualHost>

</VirtualHost>

```

The end result would be that documents out of /web would be http, yet documents out of /web/ssl would be forced to https. All for the same host (IP address). Even though I have other vhosts on the machine, I have only 1 vhost that requires SSL.

- or -

Another way to think about it. Define /var/www/example.com/web as doc root for http and somehow define /var/www/example.com/web/ssl as the ONLY SSL directory for the host. I can't seem to get this done.

While I can get https for the whole directory (/var/www/example.com/web) or not, I can't seem to get both on the same vhost. Either the intended directory is SSL but cannot get anything else from the site, or the whole thing is SSL.

I hope that helps make sense of what I'm trying to do. Can this be done?

---

### Post by terazen on 2010-09-27
It may be cleaner if you didn't put the ssl directory inside the non-ssl directory.  Anyhow, something like this may work with SSLRequireSSL:
```
<VirtualHost *:80>
...

        <Directory /var/www/example.com/web/ssl/>
                Options Indexes FollowSymLinks MultiViews
# Force SSL
                SSLRequireSSL
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
...
</VirtualHost>
```

Edit:
This might require changing the documentroot to "/var/www/example.com/web/" for the ssl virtualhost.

---


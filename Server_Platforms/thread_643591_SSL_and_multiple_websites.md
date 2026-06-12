---
title: "SSL and multiple websites"
date: 2007-12-17
forum: Server Platforms
---

### Post by jphillip on 2007-12-17
Hello,

I have apache2 running 4 websites and all have been running perfectly with virtual host setting. 

I needed website1.net to have a ssl site set up so I built me a openssl cert and created another virtual host entry and it worked basically perfectly except that if I type [https://website2.net](https://website2.net), [https://website3.net](https://website3.net), [https://website4.net](https://website4.net) it will redirect me back to [https://website1.net](https://website1.net) webpages.They all still work fine with just the http:// ... 
Any ideas on how to fix this or what I missed. 

Below is the code I used to create the virtual host ssl stuff
```

NameVirtualHost *:80
NameVirtualHost website1.net:443

<VirtualHost *:443>
   ServerName www.website1.net
    ErrorLog /var/www/website1.net/logs/error.log
     SSLEngine On
    SSLCertificateFile    /etc/apache2/apache.pem
    SetEnvIf User-Agent ".*MSIE.*" nokeepalive ssl-unclean-shutdown
    DocumentRoot /var/www/website1.net/htdocs
    rewriteEngine on
    rewriteCond %{REQUEST_METHOD} ^(TRACE|TRACK)
    rewriteRule .* - [F]
</VirtualHost>


<VirtualHost *:80>
    ServerAlias *.website1.net
    DocumentRoot /var/www/website1.net/htdocs
    ServerName website1.net
....
...
...
</VirtualHost>

```

---

### Post by rsw686 on 2007-12-18
I'm fairly sure this

NameVirtualHost website1.net:443

should be 

NameVirtualHost *:443

so that requests are allowed to any hostname at port 443

---

### Post by HermanAB on 2007-12-18
The problem is that you need a separate IP address for each separate SSL virtual server.

---

### Post by rsw686 on 2007-12-18
> **HermanAB said:**
> The problem is that you need a separate IP address for each separate SSL virtual server.

Here's a Debian how-to on how to workaround that problem. Since Ubuntu is based off Debian it shouldn't require much modification.

[http://www.howtoforge.com/enable-multiple-https-sites-on-one-ip-using-tls-extensions-on-debian-etch](http://www.howtoforge.com/enable-multiple-https-sites-on-one-ip-using-tls-extensions-on-debian-etch)

---

### Post by MJN on 2007-12-18
Note that many browsers don't support TLS extensions (it's a relatively new protocol enhancement) and hence you will likely find the majority of connecting clients will not function as desired.
 
Notable exceptions include IE7 under Vista, Firefox 2 and above and some later versions of Opera. Other browsers (and versions), of which there are an unbelievably large amount of, will not function as desired.
 
Mathew

---

### Post by HermanAB on 2007-12-18
Exactly, and since Vista is proving to be not particularly popular, bazillions of people will still run IE5 or 6 on WinXP for decades to come.  So till the 22nd century or so, you would still need to tie up one IP address per HTTPS connection.  

A web site is not much good if it only works for you.  It needs to work for everyone else.

Cheers,

Herman

---

### Post by jphillip on 2007-12-18
Could anyone possibly point me in the direction of multiple ips for one box. I assume maybe adding something to the /etc/hosts file????

Thanks for any assistance...

---

### Post by rsw686 on 2007-12-18
> **jphillip said:**
> Could anyone possibly point me in the direction of multiple ips for one box. I assume maybe adding something to the /etc/hosts file????

Thanks for any assistance...

You need multiple public IPs. It all depends on how your setup is configured. Does the box have a public IP now? Does your router use 1:1 NAT?

---

### Post by HermanAB on 2007-12-18
You can assign multiple IP addresses to one adaptor using ifconfig.  For a public web server, you get the addresses from your ISP.  Then you have to configure your DNS so that each domain name that requires HTTPS resolves to a different IP address.  Domains that do not require HTTPS, can share a single IP address.

---


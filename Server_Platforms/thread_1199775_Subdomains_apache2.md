---
title: "Subdomains apache2"
date: 2009-06-29
forum: Server Platforms
---

### Post by edwlarkey on 2009-06-29
I am trying to figure out if this is possible. I want to set up a couple of subdomains on apache2. But  one has to use ssl.  Can apache2 do this?

---

### Post by jhannah on 2009-06-30
As with any web server, if you need to setup SSL, you cannot use name based hosting. Apache can indeed do name based hosing for HTTP sites making use of the NameVirtualHost directive. Something like the below configuration should give you an idea of how to break up your VirtualHost containers:

```

NameVirtualHost *:80

<VirtualHost *:80>
  ServerName subdom1.domain.com
  # Directory / DocumentRoot / Other directives you need
</VirtualHost>

<VirtualHost *:80>
  ServerName subdom2.domain.com
  # Directory / DocumentRoot / Other directives you need
</VirtualHost>

```

You can of course setup another VirtualHost to listen on port 443 and do HTTPS but because you cannot match ServerName in an HTTPS session and thus will have to serve content from a single directory with a single SSL certificate, you can really only have a single SSL site per IP.

---

### Post by edwlarkey on 2009-07-02
> **jhannah said:**
> As with any web server, if you need to setup SSL, you cannot use name based hosting. Apache can indeed do name based hosing for HTTP sites making use of the NameVirtualHost directive. Something like the below configuration should give you an idea of how to break up your VirtualHost containers:

```

NameVirtualHost *:80

<VirtualHost *:80>
  ServerName subdom1.domain.com
  # Directory / DocumentRoot / Other directives you need
</VirtualHost>

<VirtualHost *:80>
  ServerName subdom2.domain.com
  # Directory / DocumentRoot / Other directives you need
</VirtualHost>

```

You can of course setup another VirtualHost to listen on port 443 and do HTTPS but because you cannot match ServerName in an HTTPS session and thus will have to serve content from a single directory with a single SSL certificate, you can really only have a single SSL site per IP.


Just clarifying. So you are saying that this is not possible? I can't have subdom1.domain.com http and have subdom2.domain.com be http and https or even just htps?

---

### Post by kustomjs on 2009-07-02
yes you can have https on subdomains because I got 2 different sites on my server on that. but just a heads up there can be only one 443 and if you want 2 sites running SSL you need to have site 1 on 443 and site 2 on port 444 or something.

and only thing you want to look at is mod_rewrite.

here is a setup you need to use:

put this under /etc/apache2/sites-available
with this file yoursite1.com.conf and yoursite2.com.conf

Site 1:
```
<VirtualHost *:80>
ServerName yoursite1.com
DocumentRoot /var/www/yoursite1/
</VirtualHost> 


<VirtualHost *:444>
ServerName secure.yoursite1.com
DocumentRoot /var/www/yoursite1/
SSLEngine on
SSLCertificateFile /etc/ssl/apache/yoursite1/conf/yoursite1/ssl.crt
SSLCertificateKeyFile /etc/ssl/apache/site/conf/yoursite1/ssl.key
   SSLCertificateChainFile /etc/ssl/apache/site1/conf/site1/sub.class1.server.ca.crt
   SSLCACertificateFile /etc/ssl/apache/site1/conf/yoursite1/ca.crt
</VirtualHost>
```



Site 2:
```
<VirtualHost *:80>
ServerName yoursite2.com
DocumentRoot /var/www/yoursite2/
</VirtualHost> 



<VirtualHost *:443>
ServerName secure.yoursite2.com
DocumentRoot /var/www/yoursite2/
 SSLEngine on
   SSLCertificateFile /etc/ssl/apache/conf/ssl.crt
   SSLCertificateKeyFile /etc/ssl/apache/conf/ssl.key
   SSLCertificateChainFile /etc/ssl/apache/conf/sub.class1.server.ca.crt
   SSLCACertificateFile /etc/ssl/apache/conf/ca.crt
   </VirtualHost>
```

then you want to restart apache with sudo /etc/init.d/apache2 restart.

also you would need a SSL cert per site I would go with: startcom site: [http://www.startssl.com/]("http://www.startssl.com/")

---


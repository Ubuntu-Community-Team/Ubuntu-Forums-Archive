---
title: "SSL certificate blues"
date: 2012-04-18
forum: Server Platforms
---

### Post by oboyledk on 2012-04-18
I'm having considerable difficulty configuring my HTTPS connection.  I've already generated a key and sent it to my CA, but after configuring my sever I constantly get:
 Error 102 (net::ERR_CONNECTION_REFUSED): The server refused the connection.

Here's my config:
```

Namevirtualhost 37.??.??.???:80
Namevirtualhost 37.??.??.???:443
<VirtualHost 37.??.??.???:80 >
        ServerAdmin webmaster@localhost
        Servername My FQN is here. (without the www)
        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>

        # Disable direct access to the folder
<Directory /var/www/videos>
        AllowOverride None
        allow from all
</Directory>

and my SSL,
 <IfModule mod_ssl.c>
<VirtualHost 37.??.??.???:443>
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/direct
        Servername my FQN (with www omitted)

        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>
 SSLCertificateFile /etc/ssl/certs/my_site.crt
SSLCertificateKeyFile /etc/ssl/private/my.key
 SSLCertificateChainFile /etc/ssl/certs/my.ca-bundle
```

---

### Post by webservervideos on 2012-04-18
which program is giving the error "Error 102 (net::ERR_CONNECTION_REFUSED): The server refused the connection.", is that a browser?

---

### Post by oboyledk on 2012-04-18
> **webservervideos said:**
> which program is giving the error "Error 102 (net::ERR_CONNECTION_REFUSED): The server refused the connection.", is that a browser?

Yes that's in Chrome Browser, sorry I was unclear. 

In IE I just get a general failed to connect.

---

### Post by rubylaser on 2012-04-18
Sounds like your SSLEngine is not enabled. Your vhost file needs an entry like this.
```
SSLEngine On
```

Typically placed right before your SSLCertificate section at the bottom.

---

### Post by oboyledk on 2012-04-18
> **rubylaser said:**
> Sounds like your SSLEngine is not enabled. Your vhost file needs an entry like this.
```
SSLEngine On
```

Typically placed right before your SSLCertificate section at the bottom.

I have SSLENgine on.  

I also enabled the mod in apache
a2enmod sll

Still no joy. 

Thanks for the ideas so far everyone.

---

### Post by rubylaser on 2012-04-18
Have you set Apache up to Listen on port 443?

---

### Post by oboyledk on 2012-04-18
> **rubylaser said:**
> Have you set Apache up to Listen on port 443?

Here's my Ports file: (I've also tried forcing the Listen443 line without the ifmodule)

```
#NameVirtualHost *:80
Listen 80
#NameVirtualHost *:443
#Listen 443
<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
   Listen 443
</IfModule>


```

---

### Post by jason0 on 2012-04-18
Hello,

First, determine if anything is binding to port 443:

sudo netstat -anp |grep :443| grep LISTEN 

you should see a line similar to:

> tcp          0        0   0.0.0.0:443               0.0.0.0:*                 LISTEN        10894/apache2   
Whereas on my system, the number 10894 is the process id of the master apache process (prefork).  you may see several lines, but that one is the critical one.  If there is no line, then apache is not binding to port 443 at all (listen directive).  If there IS, then perhaps there is a firewall running blocking access to that port.

--jason

---

### Post by oboyledk on 2012-04-18
Step one looks good.  I issued netstat as suggested by Jason and recieved this:
```

tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      7101/apache2
```

So apache is listening on 443.

---

### Post by webservervideos on 2012-04-18
is port open on your firewall? Tried a different browser? Are you doing something with proxy using/going through one?

---

### Post by oboyledk on 2012-04-18
> **webservervideos said:**
> is port open on your firewall? Tried a different browser? Are you doing something with proxy using/going through one?

It fails in IE and chrome.  No Proxy that i'm aware of. 
This is a dedicated box that I'm renting.  

Is there an easy way to test for a firewall?

---

### Post by oboyledk on 2012-04-18
After thinking about it, I don't think there's a firewall.  

If I disable my default site and leave only the default-ssl up, when I navigate to the site I get a response that says I'm trying to communicate with plain text to a sever that's using encryption.  

It would seem as though something is getting through?

---

### Post by oboyledk on 2012-04-18
Solved.

I just realized all my testing has been with a CA that did not include www. 

I was able to troubleshoot using these tools: (Life saver!)
[http://www.sslshopper.com/ssl-certificate-tools.html](http://www.sslshopper.com/ssl-certificate-tools.html)

Can I generate a ca of *.domain.com to cover all sub domains of my site?

---

### Post by darkod on 2012-04-18
> **oboyledk said:**
> Solved.

I just realized all my testing has been with a CA that did not include www. 

I was able to troubleshoot using these tools: (Life saver!)
[http://www.sslshopper.com/ssl-certificate-tools.html](http://www.sslshopper.com/ssl-certificate-tools.html)

Can I generate a ca of *.domain.com to cover all sub domains of my site?

You can. I think they call them mutil-domain or something. Or UCC certificates.

Of course the price is higher than for a single domain. Depends on the provider how much higher.

GoDaddy for example seems to have one with unlimited sub-domains for 145€ annual (where I am the pricing is shown in € by default.
[http://www.godaddy.com/ssl/ssl-certificates.aspx?ci=8979](http://www.godaddy.com/ssl/ssl-certificates.aspx?ci=8979)

---

### Post by SeijiSensei on 2012-04-18
> **darkod said:**
> You can. I think they call them mutil-domain or something. Or UCC certificates.

They are usually called "wild-card certificates."

---

### Post by darkod on 2012-04-18
> **SeijiSensei said:**
> They are usually called "wild-card certificates."

Correct. I was too lazy to google it first. :)

The multi-domain or UCC is literary for multiple different domains.

For only subdomains, wild card certs.

---

### Post by Stereotypical Rage on 2012-04-18
> **oboyledk said:**
> Solved.

I just realized all my testing has been with a CA that did not include www. 

I was able to troubleshoot using these tools: (Life saver!)
[http://www.sslshopper.com/ssl-certificate-tools.html](http://www.sslshopper.com/ssl-certificate-tools.html)


You can also use ```
openssl s_client -connect HOST:PORT </dev/null
```

It's a godsend in troubleshooting ssl related issues.


> Can I generate a ca of *.domain.com to cover all sub domains of my site?

Some CAs, such as [**Comodo**]("http://www.instantssl.com/ssl-certificate-products/addsupport/wildcard-ssl-premiumssl_wildcard.html") will generate a wildcard certificate for you and include a Subject Alternate Name (on same certificate) of 'domain.com' if you purchase a wildcard for '*.domain.com'

---


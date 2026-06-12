---
title: "Reverse Proxy using SSL Certificate"
date: 2008-07-02
forum: Server Platforms
---

### Post by amenszer on 2008-07-02
Hey fellas,

I currently have an Ubuntu Server running Apache/2.2.8 set up as a reverse proxy.

I have multiple web servers sitting behind the proxy...all accessible by somename.companyname.com.

I am trying to implement a verisign SSL certificate we recently acquired into this environment. 
I mirrored the proxy server onto another machine in order to test this...and have the following vhost files for one of the webservers.

The normal port 80 traffic hits this vhost:
```

<VirtualHost *>
        UseCanonicalName On
        ServerName companyname.com
        ServerAlias www.companyname.com

        ErrorLog /var/log/apache2/companyname.com.error.log
        CustomLog /var/log/apache2/companyname.access.log combined
        RewriteEngine on

        RewriteCond %{SERVER_PORT} !^443$
        RewriteRule ^.*$ https://%{SERVER_NAME}%{REQUEST_URI} [L,R]

        RewriteLog /var/log/apache2/companyname.com.rewrite.log

</VirtualHost>

```

Then the 443 traffic hits this one:

```

NameVirtualHost *:443
<VirtualHost *:443>
        ServerName companyname.com
        UseCanonicalName On

        SSLEngine On
        SSLProxyEngine On
        SSLCertificateFile /etc/apache2/cert/companyname.com.crt
        SSLCertificateKeyFile /etc/apache2/cert/companyname.com.key


        ErrorLog /var/log/apache2/companyname.com.error.ssl.log
        CustomLog /var/log/apache2/companyname.access.ssl.log combined
        
        ProxyRequests Off
        ProxyVia Off
        ProxyPreserveHost On
        <proxy *>
                Order deny,allow
                Deny from all
                Allow from all
        </proxy>

        ProxyPass / http://companyname.com/
        ProxyPassReverse / https://companyname.com/

</VirtualHost>

```


The URL is correctly written to [https://companyname.com](https://companyname.com) when hitting companyname.com....but it is not using the certificate...or doesn't seem to be. 
I am wondering if someone out there has tried this and has an alternate setup or sees a problem with my particular setup. 

Thanks.

---

### Post by amenszer on 2008-07-02
Actually...the site does appear to be using the certificate...but only for urls that are 2 or 3 directories deep in the website....i.e. [https://companyname.com](https://companyname.com) does not show that it is using the certificate....but [https://companyname.com/folder1/file.php](https://companyname.com/folder1/file.php) does show that it is.

---

### Post by amenszer on 2008-07-03
Apparently, there was some content loaded on my homepage from another site that was not secure, which was causing the conflict for the home page. Once the unsecure linking was removed, the certificate loaded correctly.

Just fyi as well,
I was receiving unknown certificate errors in Firefox (all versions), but not in IE. I did not include the Verisign intermediate certificate file in my config...once added, everything worked properly in Firefox. The parameter I'm referring to is SSLCACertificateFile.
Here are the links that helped me with this problem:
[http://groups.google.com/group/mozilla.support.firefox/browse_thread/thread/48541520b5772216/45acd6a5b98aba77]("http://groups.google.com/group/mozilla.support.firefox/browse_thread/thread/48541520b5772216/45acd6a5b98aba77")
[https://knowledge.verisign.com/support/ssl-certificates-support/index?page=content&id=AR657]("https://knowledge.verisign.com/support/ssl-certificates-support/index?page=content&id=AR657")

Here is my SSL vhost config:
```

NameVirtualHost *:443
<VirtualHost *:443>
        ServerName companyname.com
        ServerAlias www.companyname.com
#        UseCanonicalName On
        ServerAdmin webmaster@localhost

        RewriteEngine on

        RewriteCond %{SERVER_NAME} ^www.companyname.com* [NC]
        RewriteRule ^.*$ https://companyname.com%{REQUEST_URI} [L,R]


        SSLEngine On
        SSLCertificateFile /etc/ssl/certs/companyname.com.crt
        SSLCertificateKeyFile /etc/ssl/certs/companyname.com.key
        SSLCACertificateFile /etc/ssl/certs/intermediate.crt

        ErrorLog /var/log/apache2/zeus-www.companyname.com.error.ssl.log
        CustomLog /var/log/apache2/zeus-www.companyname.com.access.ssl.log combined
        ProxyRequests Off
        ProxyVia Off

        <proxy *>
                Order deny,allow
                Deny from all
                Allow from all
        </proxy>

                ProxyPass / http://companyname.com/
                ProxyPassReverse / http://companyname.com/

</VirtualHost>

```

---


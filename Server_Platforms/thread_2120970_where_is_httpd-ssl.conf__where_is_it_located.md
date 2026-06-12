---
title: "where is httpd-ssl.conf?  where is it located?"
date: 2013-02-28
forum: Server Platforms
---

### Post by 007casper on 2013-02-28
where is httpd-ssl.conf?  where is it located?

I dont have this file.

Thank you.

---

### Post by sandyd on 2013-02-28
moved to server platforms

---

### Post by sanderj on 2013-02-28
> **007casper said:**
> where is httpd-ssl.conf?  where is it located?

I dont have this file.

Thank you.

Check with:

```
locate httpd-ssl.conf
```

---

### Post by CharlesA on 2013-02-28
What are you trying to do?

If you enable ssl, you can change the settings in /etc/apache2/sites-available/default-ssl.

---

### Post by 007casper on 2013-03-01
cp default-ssl store.site.com-ssl

I have enabled store.site.com-ssl

/etc/init.d/apache2 reload
/etc/init.d/apache2 restart

apache2ctl configtest

apache2ctl restart

I have tried many other things and I constantly get the same error.  And the app is not loading on the browser.

[Fri Mar 01 03:55:30 2013] [error] ap_proxy_connect_backend disabling worker for (localhost)
[Fri Mar 01 03:55:30 2013] [error] proxy: AJP: failed to make connection to backend: localhost
[Fri Mar 01 14:32:06 2013] [error] (111)Connection refused: proxy: AJP: attempt to connect to 127.0.0.1:8009 (localhost) failed

I am not really sure why it is not loading.

---

### Post by CharlesA on 2013-03-01
Looks like you are using Tomcat (?)

[https://wiki.archlinux.org/index.php/Tomcat_and_Apache](https://wiki.archlinux.org/index.php/Tomcat_and_Apache)

---

### Post by 007casper on 2013-03-03
thanks for the link.  I dont know why I am getting this error.  I still get the same error.

here is my vhost file

> # domain: store.example.com
# public: /var/www/

#Listen 80
NameVirtualHost *:80

<VirtualHost *:80>
     # Admin email, Server Name (domain name), and any aliases
     ServerName  store.example.com:443
     ServerAdmin webmaster@localhost
     
     # Index file and Document Root (where the public files are located)
     # DirectoryIndex index.html index.php
     # DocumentRoot /home/user/public/store.example.com/public
     DocumentRoot /var/www 

     SSLEngine Off

     # Log file locations
     LogLevel warn
     ErrorLog /var/log/apache2/error.log
     CustomLog /var/log/apache2/access.log combined
  
     ProxyRequests Off
     ProxyPreserveHost On
     ProxyPass / ajp://localhost:8009/

     RewriteEngine On
     RewriteRule ^/(images/.+);jsessionid=\w+$ /$1

</VirtualHost>


<VirtualHost *:443>
     ServerName  store.example.com:443
     ServerAdmin webmaster@localhost
     
     ProxyRequests Off
     ProxyPreserveHost On    
     proxyPass / ajp://localhost:8009/ retry=0

     RewriteEngine On
     RewriteRule ^/(images/.+);jsessionid=\w+$ /$1 

     SSLEngine On
     SSLProtocol all -SSLv2
     SSLCipherSuite ALL:!ADH:!EXPORT:!SSLv2:RC4+RSA:+HIGH:+MEDIUM:+LOW
     SSLCertificateFile /etc/apache2/ssl/st_example.crt
     SSLCertificateKeyFile /etc/apache2/ssl/st.example.key
     SSLCACertificateFile /etc/apache2/ssl/st_example.ca-bundle
</VirtualHost>

---

### Post by 007casper on 2013-03-03
I wonder if it is better to define with IP then localhost

ProxyPass / ajp:// your ip:8009/ instead of proxyPass / ajp://localhost:8009/ retry=0

any ideas

---

### Post by 007casper on 2013-03-03
I tried many ways as localhost, with IP, with 127.0.0.1...  I even put the "proxyPass / ajp://localhost:8009/" ajp in apache2.conf.  

The app doesnt load.  I just seem to have the same problems.  

[Fri Mar 01 03:55:30 2013] [error] ap_proxy_connect_backend disabling worker for (localhost)
[Fri Mar 01 03:55:30 2013] [error] proxy: AJP: failed to make connection to backend: localhost
[Fri Mar 01 14:32:06 2013] [error] (111)Connection refused: proxy: AJP: attempt to connect to 127.0.0.1:8009 (localhost) failed

Is there any way to solve this problem?

---


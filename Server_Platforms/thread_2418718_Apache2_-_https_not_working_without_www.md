---
title: "Apache2 - https not working without www"
date: 2019-05-10
forum: Server Platforms
---

### Post by KuJiM on 2019-05-10
Hi all, 

if we access this site ofornecedor.com.br/#/dashboard without www then the certificate is not added to the browser, however, if we access the site [www.ofornecedor.com.br/#/dashboard](www.ofornecedor.com.br/#/dashboard) with www then we can see that the connection is secure.
What is wrong with this config? My server is on Amazon.
```
LoadModule proxy_module /usr/lib/apache2/modules/mod_proxy.so
LoadModule proxy_http_module /usr/lib/apache2/modules/mod_proxy_http.so
LoadModule proxy_wstunnel_module /usr/lib/apache2/modules/mod_proxy_wstunnel.so
LoadModule rewrite_module /usr/lib/apache2/modules/mod_rewrite.so
<VirtualHost *:80>
   ServerName ofornecedor.com.br
   ServerAlias [www.ofornecedor.com.br](www.ofornecedor.com.br)

   ProxyPreserveHost On
   ProxyRequests Off
   ProxyPass / [http://localhost:8080/](http://localhost:8080/)
   ProxyPassReverse / [http://localhost:8080/](http://localhost:8080/)

RewriteEngine on

   RewriteCond %{HTTP:Upgrade} =websocket [NC]
   RewriteCond %{REQUEST_URI} /admin [NC]
   RewriteRule /admin/(.*) ws://exp:8080/admin/$1 [P,L]

   RewriteCond %{HTTP_HOST} !^ofornecedor\.com\.br$
   RewriteCond %{HTTP_HOST} !^$
   RewriteRule ^/(.*) https://ofornecedor.com.br/$1 [L,R]

</VirtualHost>
```
[ATTACH=CONFIG]283239[/ATTACH]
THanks

---

### Post by SeijiSensei on 2019-05-10
Where's the declaration for port 443?   In the file/section that begins with "<VirtualHost: 443>" what do you have as the ServerName and ServerAlias there?

---

### Post by KuJiM on 2019-05-10
I do not have a declaration for port 443. Should I include that in the same file?

---

### Post by KuJiM on 2019-05-11
I came up with this config after a bit of research. 


But it still doesn't work for some reason. 


What Am I doing wrong here? 

```

    LoadModule headers_module /usr/lib/apache2/modules/mod_headers.so
    LoadModule proxy_module /usr/lib/apache2/modules/mod_proxy.so
    LoadModule proxy_http_module /usr/lib/apache2/modules/mod_proxy_http.so
    LoadModule rewrite_module /usr/lib/apache2/modules/mod_rewrite.so
    
    <VirtualHost *:80>
      ServerName ofornecedor.com.br
    
      RewriteEngine on
      RewriteRule ^/(.*) https://ofornecedor.com.br/$1 [L,R=301,NE]
    </VirtualHost>
    
    <VirtualHost *:443>
      ServerName ofornecedor.com.br
    
      RequestHeader set X-Forwarded-Proto "https"
    
      SSLEngine on
      SSLCertificateFile /etc/letsencrypt/live/ofornecedor.com.br/cert.pem
      SSLCertificateKeyFile /etc/letsencrypt/live/ofornecedor.com.br/privkey.pem
      SSLCertificateChainFile /etc/letsencrypt/live/ofornecedor.com.br/chain.pem
    
      Header always set Strict-Transport-Security "max-age=15768000"
    
      ProxyRequests Off
      ProxyPreserveHost On
    
      ProxyPass / [myPulicIP:8080/]("http://54.233.239.122:8080/") timeout=5
      ProxyPassReverse / [myPulicIP]("http://54.233.239.122:8080/")[:8080/]("http://54.233.239.122:8080/") timeout=5
    
      RewriteEngine on
    
      RewriteCond %{HTTP:Upgrade} =websocket [NC]
      RewriteCond %{REQUEST_URI} /admin [NC]
      RewriteRule /admin/(.*) ws://[myPulicIP]("http://54.233.239.122:8080/"):8080/admin/$1 [P,L]
    
      RewriteCond %{HTTP_HOST} !^ofornecedor\.com\.br$
      RewriteCond %{HTTP_HOST} !^$
      RewriteRule ^/(.*) https://ofornecedor.com.br/$1 [L,R]
    </VirtualHost>
    
    SSLProtocol all -SSLv3
    SSLCipherSuite ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES128-SHA256:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA:ECDHE-ECDSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA:ECDHE-RSA-AES256-SHA:DHE-RSA-AES128-SHA256:DHE-RSA-AES128-SHA:DHE-RSA-AES256-SHA256:DHE-RSA-AES256-SHA:ECDHE-ECDSA-DES-CBC3-SHA:ECDHE-RSA-DES-CBC3-SHA:EDH-RSA-DES-CBC3-SHA:AES128-GCM-SHA256:AES256-GCM-SHA384:AES128-SHA256:AES256-SHA256:AES128-SHA:AES256-SHA:DES-CBC3-SHA:!DSS
    SSLHonorCipherOrder on
    
    SSLUseStapling on
    SSLStaplingResponderTimeout 5
    SSLStaplingReturnResponderErrors off
    SSLStaplingCache shmcb:/var/run/ocsp(128000)
```

---

### Post by SeijiSensei on 2019-05-11
Well, the first place to look are the logs. What do you see in /var/log/apache2?  

Is the purpose of this server to relay all requests to myPulicIP:8080? What is myPulicIP? Is it on this server or somewhere else? If it's a different server, you need to check its logs as well. 

Why don't you tell us what you're trying to do in general terms. Are you trying to set up an encrypted portal that relays requests to another server?  Why not just encrypt that server?

---

### Post by dmnur on 2019-05-11
I guess this is what you need:
```

# Required Apache modules:
# alias
# ssl
# proxy
# proxy_http

# All HTTP requests to ofornecedor.com.br or www.ofornecedor.com.br
# will be redirected permanently to HTTPS ofornecedor.com.br
<VirtualHost *:80>
    ServerName ofornecedor.com.br
    ServerAlias www.ofornecedor.com.br
    Redirect permanent / https://ofornecedor.com.br/
</VirtualHost>

# Accessible by HTTPS as both ofornecedor.com.br and www.ofornecedor.com.br
<VirtualHost *:443>
    ServerName ofornecedor.com.br
    ServerAlias www.ofornecedor.com.br

    SSLEngine on
    SSLCertificateFile /etc/letsencrypt/live/ofornecedor.com.br/cert.pem
    SSLCertificateKeyFile /etc/letsencrypt/live/ofornecedor.com.br/privkey.pem
    SSLCertificateChainFile /etc/letsencrypt/live/ofornecedor.com.br/chain.pem

    # ProxyTimeout sets the default timeout for all proxy connections,
    # no need to set "timeout=5" for each one
    ProxyTimeout 5

    # Act as a reverse proxy for 127.0.0.1:8080
    ProxyPass / http://127.0.0.1:8080/
    ProxyPassReverse / http://127.0.0.1:8080/
</VirtualHost>

```

Websockets should work just like that, but if they don't, you'll also need the **rewrite** and **proxy_wstunnel** Apache modules and these lines at the end of the ***:443** vhost:
```

# If this is a websocket request and it starts with "/admin",
# proxy it to 127.0.0.1:8080 using wstunnel
RewriteEngine on
RewriteCond %{HTTP:Upgrade} =websocket [NC]
RewriteCond %{REQUEST_URI} ^/admin(/|$)
RewriteRule (.*) ws://127.0.0.1:8080$1 [P]

```

---

### Post by KuJiM on 2019-05-11
```
ll /var/log/apache2
total 2060
drwxr-x---  2 root adm      4096 May 11 06:25 ./
drwxrwxr-x 10 root syslog   4096 May 11 06:25 ../
-rw-r-----  1 root adm    497533 May 11 21:03 access.log
-rw-r-----  1 root adm    668586 May 11 06:24 access.log.1
-rw-r-----  1 root adm     44547 May  2 06:24 access.log.10.gz
-rw-r-----  1 root adm     29878 May  1 06:24 access.log.11.gz
-rw-r-----  1 root adm     28111 Apr 30 06:24 access.log.12.gz
-rw-r-----  1 root adm     33781 Apr 29 06:24 access.log.13.gz
-rw-r-----  1 root adm     27024 Apr 28 06:24 access.log.14.gz
-rw-r-----  1 root adm     45417 May 10 06:24 access.log.2.gz
-rw-r-----  1 root adm     29131 May  9 06:24 access.log.3.gz
-rw-r-----  1 root adm     30389 May  8 06:24 access.log.4.gz
-rw-r-----  1 root adm     31929 May  7 06:24 access.log.5.gz
-rw-r-----  1 root adm     36622 May  6 06:24 access.log.6.gz
-rw-r-----  1 root adm     30849 May  5 06:24 access.log.7.gz
-rw-r-----  1 root adm     23362 May  4 06:24 access.log.8.gz
-rw-r-----  1 root adm     22347 May  3 06:24 access.log.9.gz
-rw-r-----  1 root adm      3752 May 11 12:51 error.log
-rw-r-----  1 root adm      8618 May 11 06:25 error.log.1
-rw-r-----  1 root adm       539 May  2 06:25 error.log.10.gz
-rw-r-----  1 root adm       344 May  1 06:25 error.log.11.gz
-rw-r-----  1 root adm       340 Apr 30 06:25 error.log.12.gz
-rw-r-----  1 root adm       460 Apr 29 06:25 error.log.13.gz
-rw-r-----  1 root adm       337 Apr 28 06:25 error.log.14.gz
-rw-r-----  1 root adm       700 May 10 06:25 error.log.2.gz
-rw-r-----  1 root adm       341 May  9 06:25 error.log.3.gz
-rw-r-----  1 root adm       340 May  8 06:25 error.log.4.gz
-rw-r-----  1 root adm       340 May  7 06:25 error.log.5.gz
-rw-r-----  1 root adm       461 May  6 06:25 error.log.6.gz
-rw-r-----  1 root adm       336 May  5 06:25 error.log.7.gz
-rw-r-----  1 root adm       342 May  4 06:25 error.log.8.gz
-rw-r-----  1 root adm       341 May  3 06:25 error.log.9.gz
-rw-r--r--  1 root root        0 May 11 00:08 ofornecedor.com.br-access.log
-rw-r--r--  1 root root        0 May 11 00:08 ofornecedor.com.br-error.log
-rw-r-----  1 root adm     87604 May 11 20:51 other_vhosts_access.log
-rw-r-----  1 root adm    231159 May 11 06:24 other_vhosts_access.log.1
-rw-r-----  1 root adm      6088 May  2 05:48 other_vhosts_access.log.10.gz
-rw-r-----  1 root adm      3869 May  1 04:07 other_vhosts_access.log.11.gz
-rw-r-----  1 root adm      5707 Apr 30 06:14 other_vhosts_access.log.12.gz
-rw-r-----  1 root adm      3596 Apr 29 05:09 other_vhosts_access.log.13.gz
-rw-r-----  1 root adm      4691 Apr 28 04:35 other_vhosts_access.log.14.gz
-rw-r-----  1 root adm      7659 May 10 06:22 other_vhosts_access.log.2.gz
-rw-r-----  1 root adm      3975 May  9 05:08 other_vhosts_access.log.3.gz
-rw-r-----  1 root adm      3766 May  8 06:03 other_vhosts_access.log.4.gz
-rw-r-----  1 root adm      4743 May  7 04:05 other_vhosts_access.log.5.gz
-rw-r-----  1 root adm      1345 May  6 05:34 other_vhosts_access.log.6.gz
-rw-r-----  1 root adm      1169 May  5 05:38 other_vhosts_access.log.7.gz
-rw-r-----  1 root adm      4455 May  4 05:10 other_vhosts_access.log.8.gz
-rw-r-----  1 root adm      4674 May  3 04:33 other_vhosts_access.log.9.gz

```

Which log are we after?

I am trying to server my Enonic XP application. 

More about Enonic XP.

[https://discuss.enonic.com/t/enonic-xp-with-https/377](https://discuss.enonic.com/t/enonic-xp-with-https/377)
[https://xp.readthedocs.io/en/stable/operations/linux-detail-service-install.html#linux-detailed-service-install](https://xp.readthedocs.io/en/stable/operations/linux-detail-service-install.html#linux-detailed-service-install)

My Enonic XP instance is started on port 8080. I am trying to serve my app with SSL and with no need of tying the port number.
The public IP is the Public IP of my EC2 instance. 
Not sure what I am missing.

---

### Post by SeijiSensei on 2019-05-11
> **KuJiM said:**
> Which log are we after?
The most recent access.log and error.log. The ones with numerals are backups created by the logrotate program whch runs weekly.

> I am trying to server my Enonic XP application.

I'm not sure I want to delve into a specific application.

> My Enonic XP instance is started on port 8080. I am trying to serve my app with SSL and with no need of tying the port number.
The public IP is the Public IP of my EC2 instance. 
Not sure what I am missing.

On the server machine, try 
```
telnet localhost 8080
```
or, if you have a browser installed like elinks, go to [http://localhost:8080/](http://localhost:8080/).  Do you get a reply from the Enonic app? Try proxying to that rather than the external IP.

Can you not get Enonic to listen on port 443 and use SSL?

---

### Post by KuJiM on 2019-05-13
Hey @dmnur,


I am afraid to say that the config above did not work. It says that I have too many redirects and refuses to connect. 

LoadModule proxy_module /usr/lib/apache2/modules/mod_proxy.so
LoadModule proxy_http_module /usr/lib/apache2/modules/mod_proxy_http.so
LoadModule proxy_wstunnel_module /usr/lib/apache2/modules/mod_proxy_wstunnel.so
LoadModule rewrite_module /usr/lib/apache2/modules/mod_rewrite.so


<VirtualHost *:80>
   ServerName ofornecedor.com.br
   ServerAlias [www.ofornecedor.com.br](www.ofornecedor.com.br)


   ProxyPreserveHost On
   ProxyRequests Off
   ProxyPass / [http://localhost:8080/](http://localhost:8080/)
   ProxyPassReverse / [http://localhost:8080/](http://localhost:8080/)


RewriteEngine on


   RewriteCond %{HTTP:Upgrade} =websocket [NC]
   RewriteCond %{REQUEST_URI} /admin [NC]
   RewriteRule /admin/(.*) ws://exp:8080/admin/$1 [P,L]


   RewriteCond %{HTTP_HOST} !^ofornecedor\.com\.br$
   RewriteCond %{HTTP_HOST} !^$
   RewriteRule ^/(.*) https://ofornecedor.com.br/$1 [L,R]


</VirtualHost>


<VirtualHost *:443>


    ServerName ofornecedor.com.br
    DocumentRoot /var/www/html/


    ProxyRequests Off
    ProxyPreserveHost On


    ProxyPass /admin/event ws://localhost:8080/admin/event
    ProxyPassReverse /admin/event ws://localhost:8080/admin/event


    ProxyPass / [http://localhost:8080/](http://localhost:8080/)
    ProxyPassReverse / [http://localhost:8080/](http://localhost:8080/)


</VirtualHost>

This is the one I got to work. The only problem is that the site won't be secure is if you access it without "www" ofornecedor.com.br.

---

### Post by KuJiM on 2019-05-13
Hi [COLOR=#000000]SeijiSensei.

[/COLOR]I do not think you are able to get Enonic to listen on port 443. 

They recommend using reverse proxy as seen here. [https://xp.readthedocs.io/en/stable/operations/reverse-proxy.html](https://xp.readthedocs.io/en/stable/operations/reverse-proxy.html)

However, that config is not working for me. Maybe I am missing something. 

My site is secure if I access using "www" [www.ofornecedor.com.br](www.ofornecedor.com.br), but that is not the case if you access ofornecedor.com.br

I was able to get my app up and running with this config as I mentioned to dmnur.

[COLOR=#000000]<VirtualHost *:80>[/COLOR]
[COLOR=#000000]ServerName ofornecedor.com.br[/COLOR]
[COLOR=#000000]ServerAlias [/COLOR][www.ofornecedor.com.br]("http://www.ofornecedor.com.br/")


[COLOR=#000000]ProxyPreserveHost On[/COLOR]
[COLOR=#000000]ProxyRequests Off[/COLOR]
[COLOR=#000000]ProxyPass / [/COLOR][http://localhost:8080/](http://localhost:8080/)
[COLOR=#000000]ProxyPassReverse / [/COLOR][http://localhost:8080/](http://localhost:8080/)


[COLOR=#000000]RewriteEngine on[/COLOR]


[COLOR=#000000]RewriteCond %{HTTP:Upgrade} =websocket [NC][/COLOR]
[COLOR=#000000]RewriteCond %{REQUEST_URI} /admin [NC][/COLOR]
[COLOR=#000000]RewriteRule /admin/(.*) ws://exp:8080/admin/$1 [P,L][/COLOR]


[COLOR=#000000]RewriteCond %{HTTP_HOST} !^ofornecedor\.com\.br$[/COLOR]
[COLOR=#000000]RewriteCond %{HTTP_HOST} !^$[/COLOR]
[COLOR=#000000]RewriteRule ^/(.*) https://ofornecedor.com.br/$1 [L,R][/COLOR]


[COLOR=#000000]</VirtualHost>[/COLOR]


[COLOR=#000000]<VirtualHost *:443>[/COLOR]


[COLOR=#000000]ServerName ofornecedor.com.br[/COLOR]
[COLOR=#000000]DocumentRoot /var/www/html/[/COLOR]


[COLOR=#000000]ProxyRequests Off[/COLOR]
[COLOR=#000000]ProxyPreserveHost On[/COLOR]


[COLOR=#000000]ProxyPass /admin/event ws://localhost:8080/admin/event[/COLOR]
[COLOR=#000000]ProxyPassReverse /admin/event ws://localhost:8080/admin/event[/COLOR]


[COLOR=#000000]ProxyPass / [/COLOR][http://localhost:8080/](http://localhost:8080/)
[COLOR=#000000]ProxyPassReverse / [/COLOR][http://localhost:8080/](http://localhost:8080/)


[COLOR=#000000]</VirtualHost>



[/COLOR]Do you see anything wrong with it?

Sorry, but apache2 is not my expertise.

Thank you for helping me out.

---

### Post by SeijiSensei on 2019-05-14
There's only one answer to your question, and that answer is itself a question. Does it work the way you want it to?

---


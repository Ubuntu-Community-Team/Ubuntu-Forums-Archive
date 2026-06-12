---
title: "Apache virtual host to access internal server."
date: 2010-04-20
forum: Server Platforms
---

### Post by zfreak7c5 on 2010-04-20
I'm not sure is this is possible or not, but what I would like to do is take my public address mydomain.com and configure a virtual host something.mydomain.com only instead of having the content on the same server I would like it to point to the IP of my virtual machine that is in my private network and display that page publicly.  Does anyone know if this is possible, or how to do it?  I have done this with port forwards, but would like them both to be on the same port.

---

### Post by terrrorr on 2010-04-20
Hi,

If I understood you right your current setup is:

1. One public IP
2. You are using some sort of router or firewall to create your own LAN
3. You have one host machine which includes another virtual machine.
4. Both have their own Apache server which serves different sites (A. mydomain.com B. somethingelse.mydomain.com)

Please correct me if there is a mistake

Question 1: Why you want to use several servers when you have possibility to use one server with for serving several different sites?

---

### Post by cdenley on 2010-04-20
Sounds like you want a reverse proxy.
[http://httpd.apache.org/docs/2.2/mod/mod_proxy.html#examples](http://httpd.apache.org/docs/2.2/mod/mod_proxy.html#examples)

create your virtualhost
/etc/apache2/sites-available/lanproxy
```

<VirtualHost *:80>
   ServerName something.mydomain.com
   ProxyRequests Off

   <Proxy *>
      Order deny,allow
      Allow from all
   </Proxy>

   ProxyPass / http://internalip/
   ProxyPassReverse / http://internalip/
</VirtualHost>

```

run these commands
```

sudo a2enmod proxy proxy_http
sudo a2ensite lanproxy
sudo /etc/init.d/apache2 restart

```

---

### Post by zfreak7c5 on 2010-04-20
> **cdenley said:**
> Sounds like you want a reverse proxy.
[http://httpd.apache.org/docs/2.2/mod/mod_proxy.html#examples](http://httpd.apache.org/docs/2.2/mod/mod_proxy.html#examples)

create your virtualhost
/etc/apache2/sites-available/lanproxy
```

<VirtualHost *:80>
   ServerName something.mydomain.com
   ProxyRequests Off

   <Proxy *>
      Order deny,allow
      Allow from all
   </Proxy>

   ProxyPass / http://internalip/
   ProxyPassReverse / http://internalip/
</VirtualHost>

```

run these commands
```

sudo a2enmod proxy proxy_http
sudo a2ensite lanproxy
sudo /etc/init.d/apache2 restart

```


Thanks, thats exactly what I wanted.  It's working well, to answer terrrorr's question this is a Server 2003 VM running a streaming audio server, so not something I can just copy the document root over and use.

---


---
title: "Apache alias help."
date: 2009-09-17
forum: Server Platforms
---

### Post by ilukester on 2009-09-17
So,

I have a ubuntu box, lets call it ubu1, that is running Apache2 and is portforwarded to the outside world. Now I also have another ubuntu box, ubu2, that is in my network and hosts a couple of applications on its own apache2 server. Now I was wondering if there was any way that I could access ubu2 files from the outside network threw ubu1...

I tried this on ubu1, but this didnt work.
```

Alias /apps "http://192.168.1.11/apps/"
<Directory "http://192.168.1.11/apps/">
Order Allow,Deny
Allow from All
</Directory>
```

[http://192.168.1.11](http://192.168.1.11) being the address of ubu2... Anything you guys know of that could/will make this work. Thanks in advanced.

---

### Post by t3r0 on 2009-09-17
Take a look at mod_proxy for apache. Thats what you need. 

[http://httpd.apache.org/docs/2.2/mod/mod_proxy.html](http://httpd.apache.org/docs/2.2/mod/mod_proxy.html)


- Tero

---

### Post by ilukester on 2009-09-17
Thanx t3r0 for pointing me in the right direction.

I found my most of my answer from [here]("http://abhirama.wordpress.com/2008/11/03/apache-mod_proxy-in-ubuntu/")

But here is the code that I used to get my server up and running.

1. Install reverse_proxy module

```
sudo apt-get install libapache2-mod-proxy-html
```

2. Install libxml if it is not already installed.

```
apt-get install libxml2-dev
```

3. Since i wanted to pass the /apps folder from ubu2 to ubu1... I added these lines to the apache2.conf

```
ProxyRequests Off

<Proxy *>
        Order deny,allow
        Allow from all
</Proxy>

ProxyPass /apps  http://192.168.1.11/apps/
ProxyPassReverse /apps  http://192.168.1.11/apps/
<Location /apps>
        Order allow,deny
        Allow from all
</Location>
```

4. Restart Apache
```
sudo /etc/init.d/apache2 restart
```

---


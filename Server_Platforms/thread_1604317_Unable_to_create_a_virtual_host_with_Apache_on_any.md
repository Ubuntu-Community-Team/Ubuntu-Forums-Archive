---
title: "Unable to create a virtual host with Apache on any ports other then 80"
date: 2010-10-23
forum: Server Platforms
---

### Post by pcarlos853 on 2010-10-23
Hello, I have just installed Ubuntu Server 10.10, and I installed Webmin 1.520. When I goto Servers --> Apache Webserver --> Create Virtual Host --> I leave everything the default settings but change: Port 81 and Document root "/var/www2/" Then I restart Apache. But when I go to 192.168.1.4:81 I get Firefox can't establish a connection to the server at 192.168.1.4:81 . I have no idea what I am doing wrong. Any help would be greatly appreciated!__

---

### Post by CharlesA on 2010-10-23
I had to add this to /etc/apache2/ports.conf

```
NameVirtualHost *:88
Listen 88

```

Works for me now. :)

Here's /etc/apache2/httpd.conf:

```
<VirtualHost *:88>
    ServerName mars
    DocumentRoot /var/www/port88
</VirtualHost>

```

---

### Post by pcarlos853 on 2010-10-23
Thanks that got it working!

---

### Post by CharlesA on 2010-10-23
Glad it works. Don't forget to mark the thread as solved from the thread tools menu. :)

---


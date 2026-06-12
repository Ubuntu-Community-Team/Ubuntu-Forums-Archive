---
title: "DNS resolves domain, than url changes to ip address"
date: 2013-06-21
forum: Server Platforms
---

### Post by wlraider70 on 2013-06-21
I just added a sub domain to my godaddy hosting.
The main domain is hosted by go daddy. the sub is local to my office.
its on an Ubuntu 12.04 box.

If I go to sub.mydomain.org it works. However the url bar changes to the ip address.
I tied 2 browsers to confirm. Is there something I need to do in apache2?
Also will creating sub.mydomain.org/wow be an issue?

---

### Post by SeijiSensei on 2013-06-21
Do you have a <VirtualHost> stanza that includes sub.mydomain.org in a ServerName or ServerAlias directive?

The answer to your second question is no.

---

### Post by wlraider70 on 2013-06-21
ok IF I understand you I now have


```



 GNU nano 2.2.6             File: /etc/apache2/httpd.conf

<VirtualHost *:80>
    # This first-listed virtual host is also the default for *:80
    ServerName www.apps.wi**.org
    ServerAlias apps.wil**.org
    DocumentRoot /var/www/

</VirtualHost>


```

the root is where i have the index.html file. is that correct?


is this a problem?


```

server@philo:/etc/apache2$ sudo service apache2 restart
 * Restarting web server apache2                                                           apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

       [ OK ]


```

---

### Post by SeijiSensei on 2013-06-21
Add an entry to /etc/hosts like this

```
ip.addr.of.ext_interface  www.apps.xxx.org
```

The first entry is the externally-facing IP address; the second is the hostname.

Restart apache with "sudo service apache2 restart".

This is only necessary when you do not have a DNS with a reverse ("PTR") record configured for the address.

---

### Post by wlraider70 on 2013-06-22
got it. thanks again.

---


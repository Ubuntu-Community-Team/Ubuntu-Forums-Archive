---
title: "apache error"
date: 2009-02-04
forum: Server Platforms
---

### Post by Fertech on 2009-02-04
i can't seem to view my website. i get this error, how do i fix this.

```
fertech@fertech-desktop:~$ sudo /etc/init.d/apache2 restart
[sudo] password for fertech: 
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
fertech@fertech-desktop:~$ 

```

---

### Post by spiderbatdad on 2009-02-04
are you try to view from outside the LAN? Have you tried typing the WAN ip address?
To fix that error add the line:
```
ServerName Your.domain.com
or
ServerName WAN.IP.Address
```to your httpd.conf file

---

### Post by Iowan on 2009-02-04
Verify that /etc/hosts begins something like:
```
127.0.0.1 localhost
127.0.1.1 <hostname>.<domain> <hostname>
```
Your file should have appropriate hostname and (possibly) domain.
That problem actually gets discussed [here]("https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20Apache").

---

### Post by spiderbatdad on 2009-02-04
When in doubt, read the manual:
[http://httpd.apache.org/docs/2.0/mod/core.html](http://httpd.apache.org/docs/2.0/mod/core.html)

In addition to adding ServerName <fqdn or ip> to httpd.conf, if you are using virtual hosts, ServerName should be placed inside a <VirtualHost> section.

---


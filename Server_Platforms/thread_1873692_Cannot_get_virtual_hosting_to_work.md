---
title: "Cannot get virtual hosting to work"
date: 2011-11-01
forum: Server Platforms
---

### Post by &lt;h1&gt;Mckennie&lt;/h1&gt; on 2011-11-01
i have lampp installed, and i am trying to get virtual hosting to work, so i know how to do it in the future. on my local computer (a windows machine) i've put an entry in the hosts file (C:\Windows\System32\drivers\etc\hosts)

192.168.1.66 domain.tld

and i have put the following in the vhosts file on the server

NameVirtualHost *:80

<VirtualHost *:80>
  ServerName [www.domain.tld]("http://www.domain.tld")
  ServerAlias domain.tld *.domain.tld
  DocumentRoot /opt/lampp/media/
</VirtualHost>

then when i go to "domain.tld" its exactly the same as if i went to "192.168.1.66" and if i go to "www.domain.tld" firefox says "server not found". i want to know if there's anything i'm doing wrong

---

### Post by volkswagner on 2011-11-01
Try this in you windows hosts file:

```
192.168.1.66 domain.tld
192.168.1.66 *.domain.tld
```

---

### Post by &lt;h1&gt;Mckennie&lt;/h1&gt; on 2011-11-01
same result :/

---

### Post by &lt;h1&gt;Mckennie&lt;/h1&gt; on 2011-11-14
i needed to uncomment an include in httpd.conf to include httpd-vhosts.conf. i am now officially moving from ubuntu to slackware because this forum has such an awful error rate.

---

### Post by volkswagner on 2011-11-14
Thats interesting.

You did not mention what version of Ubuntu server you were running.

In Ubuntu 10.04 virtualhost is running happily with a blank httpd.conf.

Two relative configs are:

/etc/apache2/apache2.conf:
```
# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

```

/etc/apache2/ports.conf
```
NameVirtualHost *
Listen 80
```

The beauty of Linux is the freedom it offers us to choose.

Enjoy.

---

### Post by Vegan on 2011-11-14
Even though Ubuntu lacks integration components, I can still use it on a VM because webmin allows full access.

If you are using a VM for a web hosting, make sure that port 80 is sent to the right VM

---

### Post by SeijiSensei on 2011-11-14
Virtual host definitions in Ubuntu are stored in /etc/apache2/sites-enabled.  Did you put your custom definition there?

---

### Post by e79 on 2011-11-14
> **<h1>Mckennie</h1> said:**
> i am now officially moving from ubuntu to slackware because this forum has such an awful error rate.

buh-bye.

---


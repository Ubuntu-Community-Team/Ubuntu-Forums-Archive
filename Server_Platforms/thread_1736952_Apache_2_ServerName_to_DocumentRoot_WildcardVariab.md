---
title: "Apache 2 ServerName to DocumentRoot Wildcard/Variable (VirtualHosts)"
date: 2011-04-22
forum: Server Platforms
---

### Post by chrisolof on 2011-04-22
Is anyone aware of a way to take a wildcard in as a subdomain and map it to a folder of the same name as the wildcard?

Here's the way I'm doing things now, which is cumbersome as it requires an entry for each and every subdomain:

File: /etc/apache2/httpd.conf

```
<VirtualHost *:80>
  ServerName a.example.com
  DocumentRoot /var/www/a
</VirtualHost>
```


Here's what I'm hoping exists, but can't find any documentation of it:

```
<VirtualHost *:80>
  ServerName $variable.example.com
  DocumentRoot /var/www/$variable
</VirtualHost>
```

Where $variable would be the wildcard.  If someone requested [http://a.example.com](http://a.example.com) this would serve him/her the /var/www/a folder.

If I could get something like that going I could drastically reduce the size of my /etc/apache2/httpd.conf file and eliminate the need to create one of these VirtualHost entries for each subdomain.  Anyway - hoping it's possible, just not sure how to get there.  Ideas?

---

### Post by volkswagner on 2011-04-22
Interesting idea.  I have never seen such a setup.

This site may give you some help.  If you are capable with .php you may have great success (as the full solution is not spelled out).

[http://www.dedicatedserverhosting.com/2008/02/27/dynamic-subdomains-in-apache/](http://www.dedicatedserverhosting.com/2008/02/27/dynamic-subdomains-in-apache/)

I usually don't put my vhosts in httpd, I prefer individual files.  This won't reduce the work, but can help manage the clutter.

One suggestion:  If you attempt the above, a simple test setup would be to create a new vhost file in /etc/apache2/sites-available for the wild card setup.  This way you won't break any of your existing subdomains.  When you create the above vhost have the file name appear alphabetically first, this way request for new subdomains not specifically listed elsewhere, will get pointed to the new vhost file.

---

### Post by falko on 2011-04-23
Take a look here: [http://httpd.apache.org/docs/2.0/vhosts/mass.html](http://httpd.apache.org/docs/2.0/vhosts/mass.html)

---

### Post by chrisolof on 2011-05-25
I think that's exactly what I was after.  Thanks falko!

---


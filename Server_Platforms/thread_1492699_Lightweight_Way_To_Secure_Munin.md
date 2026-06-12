---
title: "Lightweight Way To Secure Munin"
date: 2010-05-25
forum: Server Platforms
---

### Post by SuperMike on 2010-05-25
For those who don't know, Munin is a way to monitor your server performance over NetSNMP and show it in a web friendly way. You install it like so:

apt-get install apache2 snmpd snmp munin munin-node

And then wait about 2 minutes for stuff to appear in /var/www/munin.

By default, it's not secured from prying eyes. However, I just developed a lightweight way to secure Munin without requiring an ugly BASIC authentication dialog.

It's simple, really. You use two .htaccess files and drop an entry in your /etc/hosts file (or %windir%/system32/drivers/etc/hosts file if on Windows) in order to connect.

In the root of /var/www, I placed this .htaccess file:

```
Options -Indexes

IndexIgnore .htaccess

<FilesMatch "\.(htaccess)">
    Deny from all
</FilesMatch>
<FilesMatch ".*~$">
  Deny from all
</FilesMatch>

RewriteEngine On

RewriteCond %{HTTP_HOST} ^munin\.example\.com$ [NC]
RewriteRule . munin$1 [QSA]

```
Then, in /var/www/munin, I added this .htaccess file:

```
Options -Indexes

IndexIgnore .htaccess

<FilesMatch "\.(htaccess)">
    Deny from all
</FilesMatch>
<FilesMatch ".*~$">
	Deny from all
</FilesMatch>

RewriteEngine On

RewriteCond %{HTTP_HOST} !^munin\.example\.com$ [NC]
RewriteRule .* - [F,L]
```

At that point, you just drop an entry in your local workstation hosts file of:

[ip address goes here]   munin.example.com

So for instance, if my domain was example.com, on IP 10.10.10.10, it would be:

```
10.10.10.10 munin.example.com
```

And now you connect like so:

[http://munin.example.com/](http://munin.example.com/)

And it connects to Munin automatically. However, what's neat about it is that it doesn't disrupt anything else you might be doing underneath /var/www. It simply requires that those who want to web surf into the munin subfolder have a browser address connecting to munin.example.com.

And you don't have to use munin.example.com. You can replace the keyword "munin" with anything you want in your /etc/hosts on your workstation or in your .htaccess file on the line for RewriteCond.

No Apache reboot is necessary. However, note that if you mess back and forth with this, you may have to clear your browser cache between tests so that you aren't using a cached connection.

---


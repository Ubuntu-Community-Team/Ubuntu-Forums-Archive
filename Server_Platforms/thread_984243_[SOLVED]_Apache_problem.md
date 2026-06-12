---
title: "[SOLVED] Apache problem"
date: 2008-11-16
forum: Server Platforms
---

### Post by threetimes on 2008-11-16
I have a dynamic virtual host setup like [this]("http://httpd.apache.org/docs/2.0/vhosts/mass.html#xtra-conf")
vhost.map:
```
mail.peter-server.homelinux.net        /usr/share/squirrelmail
munin.peter-server.homelinux.net    /var/www/munin
```(squirrelmail and munin installed via apt-get)

But when I try to access one of these subdomains I get a 404:
```
The requested URL / was not found on this server.
```Same with SSL.

I am using apache 2.2.8 on ubuntu server 8.04.1.

---

### Post by CrucifiedEgo on 2008-11-16
I dunno about you, but that seems overly complicated.  Have you tried using regular vhosts?  [http://articles.slicehost.com/2008/4/29/ubuntu-hardy-apache-virtual-hosts-1](http://articles.slicehost.com/2008/4/29/ubuntu-hardy-apache-virtual-hosts-1) is a good resource.

---

### Post by threetimes on 2008-11-17
I almost got it to work, but I need SSL (for webmail and such)
[This page]("http://httpd.apache.org/docs/2.2/vhosts/name-based.html") says:
 - Name-based virtual hosting cannot be used with SSL secure servers         because of the nature of the SSL protocol.

Any workaround?

---

### Post by CrucifiedEgo on 2008-11-17
The only way to make that work is to use different IP addresses.  In secure connections, the hostname is sent after the certificates are exchanged, so there's no way to change certs depending on the host.  That said, i believe as long as you're willing to put up with the ssl error popup, you should be able to get it working.  

What is happening now when you try to hit the page using https:// ?

---

### Post by threetimes on 2008-11-17
I disabled ssl (removed the SSLEngine part)
If I try to enable it, apache won't start

I'll post some configuration below

apache2.conf is unchanged
ports.conf:
```
Listen 80
<IfModule mod_ssl.c>
    Listen 443
</IfModule>

```httpd.conf, version without SSL
```
NameVirtualHost *
```httpd.conf, version with SSL:
```
# Some kind of NameVirtualHost statement(s),
# I tried a lot...
<VirtualHost *:443>
SSLEngine on
#SSLOptions +StrictRequire
SSLCertificateFile /etc/ssl/certs/server.crt
#SSLCertificateKeyFile /etc/ssl/private/server.key
</VirtualHost>

```sites-enabled/000-default:
```
ServerAdmin webmaster@peter-server.homelinux.com

#and the default contents...

```sites-enabled/squirrelmail:
```
#Alias /squirrelmail /usr/share/squirrelmail

<Directory /usr/share/squirrelmail>
  #default squirrelmail settings...
</Directory>
<VirtualHost *>
  ServerName  mail.peter-server.homelinux.net
  ServerAlias webmail.peter-server.homelinux.net squirrelmail.peter-server.homelinux.net

  DocumentRoot /usr/share/squirrelmail

#Disabled, because SSL is disabled
#If i enable it, it works as expected

#  RewriteEngine On
#  RewriteCond %{HTTPS} !=on
#  RewriteRule ^(.*) https://%{SERVER_NAME}$1 [R]
</VirtualHost>

```**Edit:** you can test this for yourself, just go to [http://mail.peter-server.homelinux.net]("http://mail.peter-server.homelinux.ne") or [httpS://mail.peter-server.homelinux.net]("httpS://mail.peter-server.homelinux.ne") and see
You should get a SquirrelMail login page with a certificate signed by "Peter" (that's me!).

And for the certificate error, I am the only user, and I trust myself (duh!).
But I still want it to be secure, because it's my private mail, and I want to access it from public places like school (and I don't trust the school network).

---

### Post by CrucifiedEgo on 2008-11-17
I don't think you have mod_ssl enabled -- when i telnet to port 443, it acts like a normal unsecured HTTP connection.  try sudo a2enmod ssl and then restart apache.

---

### Post by threetimes on 2008-11-17
That's not the problem now, it is that I use the non-SSL httpd.conf
I'll enable SSL right now...
Apache won't start, no matter what I try:
```
root@peter-server:/etc/apache2# a2enmod ssl
This module is already enabled!
root@peter-server:/etc/apache2# /etc/init.d/apache2 start
 * Starting web server apache2                                           [fail] 
#removed SSL part of configuration
root@peter-server:/etc/apache2# /etc/init.d/apache2 start
 * Starting web server apache2                                           [ OK ] 
```

---

### Post by CrucifiedEgo on 2008-11-17
OK, try starting apache again with ssl enabled, then post the last few lines of /var/log/apache2/error.log -- that should tell us what's going on.

---

### Post by threetimes on 2008-11-17
Rember this?
```
<VirtualHost *:443>
SSLEngine on
#SSLOptions +StrictRequire
SSLCertificateFile /etc/ssl/certs/server.crt
#SSLCertificateKeyFile /etc/ssl/private/server.key
</VirtualHost>
```
Should be this:
```
<VirtualHost *:443>
SSLEngine on
SSLOptions +StrictRequire
SSLCertificateFile /etc/ssl/certs/server.crt
SSLCertificateKeyFile /etc/ssl/private/server.key
</VirtualHost>
```

Now it works!!!

---

### Post by threetimes on 2008-11-17
I'm not finished yet...

Squirrelmail works, but munin and phpmyadmin don't

httpd.conf:
```
NameVirtualHost *:80
NameVirtualHost *:443
<VirtualHost *:443>
SSLEngine on
SSLOptions +StrictRequire
SSLCertificateFile /etc/ssl/certs/server.crt
SSLCertificateKeyFile /etc/ssl/private/server.key
</VirtualHost>

<VirtualHost *:80 *:443>
  ServerName  mail.peter-server.homelinux.net

  DocumentRoot /usr/share/squirrelmail

  RewriteEngine On
  RewriteCond %{HTTPS} !=on
  RewriteRule ^(.*) https://%{SERVER_NAME}$1 [R]
</VirtualHost>

<VirtualHost *:80 *:443>
  ServerName  pma.peter-server.homelinux.net

  DocumentRoot /usr/share/phpmyadmin

  RewriteEngine On
  RewriteCond %{HTTPS} !=on
  RewriteRule ^(.*) https://%{SERVER_NAME}$1 [R]
</VirtualHost>

<VirtualHost *:80 *:443>
  ServerName  munin.peter-server.homelinux.net

  DocumentRoot /var/www/munin
</VirtualHost>
```

**Edit:** no useful information in the logs...

---

### Post by MJN on 2008-11-18
> **threetimes said:**
> Squirrelmail works, but munin and phpmyadmin don'tYou will have to provide more info than that if you seriously expect anyone to help you.
 
At the very least, post the URL that you trying to reach along with a description of what you expected and what actually happened.
 
Incidentally, all three of your sites appear to work fine from here (successfull SSL handshake, front pages load up) but as you haven't said what you mean by 'doesnt work'...
 
Mathew

---

### Post by threetimes on 2008-11-18
> **MJN said:**
> ...all three of your sites appear to work fine from here...I know what went wrong: I was working from a live-cd from inside my local network. That doesn't use real DNS, but a manulally added hosts entry.
I only added mail.peter-server.homelinux.net, neither pma.peter-server.homelinux.net nor munin.peter-server.homelinux.net.
If I use web-sniffer.net for testing, everything works as expected!

---

### Post by kennedy7 on 2008-12-10
Hey man, i got a website too and got vhost and everything how would i go about setting up squirrel mail? Any help would be appreciated.
Thanks in advance.

---

### Post by MJN on 2008-12-10
> **kennedy7 said:**
> Hey man, i got a website too and got vhost and everything how would i go about setting up squirrel mail? Any help would be appreciated.
Thanks in advance.Start a new thread. Appending a new query to a thread marked 'Solved' could well end up with a reduced audience (if any at all).
 
Mathew

---


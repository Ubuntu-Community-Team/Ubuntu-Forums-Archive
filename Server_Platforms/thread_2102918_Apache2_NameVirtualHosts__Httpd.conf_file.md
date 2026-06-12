---
title: "Apache2 NameVirtualHosts / Httpd.conf file"
date: 2013-01-08
forum: Server Platforms
---

### Post by GRMoreton on 2013-01-08
Hi All

I will apologise in advance of asking a really noobish question when setting up a "NamedVirtualHost" I am new to the whole Apache2 Webserver on Linux game however am learning fast for the last few weeks.  The endless streams of information on the web however are often confusing and in some parts conflicting according to people's viewpoint.  I have a fixed single IP and I want to host multiple websites from my webserver and therefore I have created a NameVirtualHost in the Httpd.conf file. as follows:

 ServerName localhost
NameVirtualHost 86.xx.xx.xx:80


<VirtualHost *>
    DocumentRoot /var/www/
 </VirtualHost>

<VirtualHost 86.xx.xx.xxx:80>
   DocumentRoot /var/www/mydomain1.net
   ServerName nzbscene.net
   ServerAlias [www.xxxx.net]("http://www.xxxx.net") blog.xxxx.net [www.xxxx.xxxxx.net]("http://www.xxxx.xxxxx.net") *.xxxx.net
</VirtualHost>

<VirtualHost 86.xx.xx.xxx:80>
    DocumentRoot /var/www/mydomain2.net
   ServerName scene-it.net
    ServerAlias *.xxx.net [www.xxxx.net]("http://www.xxxx.net") blog.xxxx.net [www.blog.xxxx-it.net]("http://www.blog.xxxx-it.net")
</VirtualHost>

I originally set up "mydomain1" and "mydomain2" in the /Apache2/site-available/ folder which of course was then copied to the "Sites-enabled"  folder via the system lync. 

My question is this : If you are setting up a "Namevirtualhost" config in the \etc\apache2\ httpd.conf file, should you also have the virtual hosts set up in "sites-available"?

again I apologise in advance for probably such a stupid question. I have read so much in recent weeks I have tied myself into a bit of a mental knot 

The outcome of my mental confusion is that I believe I have even managed to confuse Apache2 

Can anyone help?

---

### Post by ScottDeagan on 2013-01-08
> **GRMoreton said:**
> 
My question is this : If you are setting up a "Namevirtualhost" config in the \etc\apache2\ httpd.conf file, should you also have the virtual hosts set up in "sites-available"?


You shouldn't set up virtual hosts in both httpd.conf and in the sites-available directory. If you look at your /etc/apache2/apache2.conf file, you'll see down the bottom: 

```

# Include the virtual host configurations:
Include sites-enabled/

```When you start Apache2, it will go through all your .conf files in the sites-enabled directory and configure your virtual hosts. However, you also shouldn't add config files directly to the sites-enabled directory. Instead, create the virtual host config file in your sites-available directory, and then enable it using:

```

sudo a2ensite myvirtualhost.conf
sudo service apache2 reload

```In my httpd.conf file, all I have is:

```

ServerName testing.local
NameVirtualHost *:80
NamevirtualHost *:443

```

(NOTE: I use a "*" instead of specifying the IP address, as you have done).

I can then easily set up my virtual hosts as follows:

```

<VirtualHost *:80>
  ServerName some.vhost.local
  DocumentRoot /var/vhosts/some.vhost.local/www
  Options FollowSymlinks
  ServerSignature Off
</VirtualHost>

```

By using a wildcard (*) instead of using an IP address, it gives me the convenience of being able to copy a virtual hosts into a dev environment or virtual machine without having to change IP address etc.

---

### Post by GRMoreton on 2013-01-09
Many thanks for the reply Scott. I have now completely removed everything from the httpd.conf file and re-added the configuration into a new file in the apache2/sites-available/   folder. 

I have sill left the "namevirtualhost"  xx.xx.xx.xxx:80 line in ther hhtpd.conf file in addition to the server name as follows: 

ServerName localhost
NameVirtualHost xx.xx.xx.xxx:80

Whenever I reload apache2 I get the  following message in gnome:
[warn] NameVirtualHost *:80 has no VirtualHosts

As mentioned I have read hours and hours of conflicting feedback on various forums when trying to pick up speed on the Linux and apacha2 and there is a suggestion that the error message occurs when you setup multiple "namevirtualhost" statements in different configuration files. for example I have the statement "NameVirtualHost *:80" in the "Ports.conf" file - This being the case, I have read that Apache2 tries to perform the same validation twice as you only ever need 1 x "namevirtualhost" statement in 1 x conf file which then covers all eventualities.
Would you agree with this feedback? 

Again any feedback would be gratefully appreciated.

---

### Post by ScottDeagan on 2013-01-09
> **GRMoreton said:**
> 
I have sill left the "namevirtualhost"  xx.xx.xx.xxx:80 line in ther hhtpd.conf file in addition to the server name as follows: 

ServerName localhost
NameVirtualHost xx.xx.xx.xxx:80

Whenever I reload apache2 I get the  following message in gnome:
[warn] NameVirtualHost *:80 has no VirtualHosts


Try changing "NameVirtualHost xx.xx.xx.xxx:80" to "NameVirtualHost *:80" in your httpd.conf. Make sure there isn't a duplicate "NameVirtualHost *:80" in ports.conf.

Add a virtual host to /etc/apache2/sites-available. Enable it using: a2ensite [filename.ext].

Then: sudo service apache2 restart

Let me know if this gets rid of the warning.

---


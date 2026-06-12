---
title: "Help with apache virtual hosts (multiple websites on 1 server)"
date: 2007-03-20
forum: Server Platforms
---

### Post by aparsons on 2007-03-20
Hello, I'm running Ubuntu Edge 6.10.  I'm also running apache, mysql, coldfusion, and ssh.  I recently moved all of my websites from IIS to Apache2 (rather flawlessly).  However, I'm trying to wrap my head around hostheaders in apache2 - these were a little more simplier in IIS.  

I pretty much have it working, but when I browse to [https://www.websiteA.com](https://www.websiteA.com), the contents of [https://www.websiteB.com](https://www.websiteB.com) are displayed. (Also, if i browse to [https://www.websiteB.com](https://www.websiteB.com), the contents of [https://www.websiteB.com](https://www.websiteB.com) display correctly).

Here is my configuration:

**/etc/hosts:**
```
127.0.0.1       localhost
192.168.1.3     apkcfs1
192.168.1.2     server1
192.168.1.201   hydrogen
192.168.1.110   mythtv
192.168.1.3     www.websiteA.com websiteA.com
192.168.1.3     www.websiteB.com websiteB.com
192.168.1.5     www.websiteB.com websiteB.com #SSL IP
192.168.1.3     www.websiteC.com websiteC.com

```

**/etc/network/interfaces:**
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.3
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

# Second network interface for ssl
auto eth0:1
iface eth0:1 inet static
        address 192.168.1.5
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1


```

**websiteA's configuration**
```
root@apkcfs1:/etc/apache2/sites-available# cat www.websiteA.com.conf
NameVirtualHost 192.168.1.3:80

<VirtualHost 192.168.1.3:80>
ServerName www.websiteA.com
ServerAlias websiteA.com www.websiteA.org www.websiteA.org
DocumentRoot "/var/www/www.websiteA.com"

CustomLog /var/log/apache2/www.websiteA.com/access.log combined
ErrorLog /var/log/apache2/www.websiteA.com/error.log

<Directory "/var/www/www.websiteA.com">
Options FollowSymLinks
AllowOverride None
Order allow,deny
Allow from all
</Directory>
DirectoryIndex index.html index.htm login.cfm index.cfm
</VirtualHost>

```

**websiteB's configuration**
```
root@apkcfs1:/etc/apache2/sites-available# cat www.websiteB.conf
<VirtualHost 192.168.1.3:80>
ServerName www.websiteB.com
ServerAlias websiteB.com
DocumentRoot "/var/www/www.websiteB.com"

CustomLog /var/log/apache2/www.websiteB.com/access.log combined
ErrorLog /var/log/apache2/www.websiteB.com/error.log

<Directory "/var/www/www.websiteB.com">
Options FollowSymLinks
AllowOverride None
Order allow,deny
Allow from all
</Directory>
DirectoryIndex comingsoon.cfm index.cfm index.html index.htm default.html default.htm
</VirtualHost>


<VirtualHost 192.168.1.5:443>
ServerName www.websiteB.com
ServerAlias websiteB.com
DocumentRoot "/var/www/www.websiteB.com"

CustomLog /var/log/apache2/www.websiteB.com/access.log combined
ErrorLog /var/log/apache2/www.websiteB.com/error.log

<Directory "/var/www/www.websiteB.com">
Options FollowSymLinks
AllowOverride None
Order allow,deny
Allow from all
</Directory>
SSLEngine on
SSLCertificateFile /etc/apache2/ssl/www.websiteB.com_cert.pem
SSLCertificateKeyFile /etc/apache2/ssl/www.websiteB.com_key.pem
SSLProtocol all
#SSLCipherSuite HIGH:MEDIUM
DirectoryIndex comingsoon.cfm index.cfm index.html index.htm default.html default.htm
</VirtualHost>

```

My router is forwarding port 443 to 192.168.1.5 and port 80 to 192.168.1.3.

***If a user types in [https://www.websiteA.com](https://www.websiteA.com), I don't want the contents of [https://www.websiteB.com](https://www.websiteB.com) showing up.***

TIA

---

### Post by astrogazer on 2007-03-20
I'm not an Apache expert but I might contribute something anyway.

If you are using HTTPS Apache does not "resolve" the requested domain name,
SSL handshake takes precedence over HTTP. There is no way around this. This is
why a separate IP is needed for each domain that needs to use SSL.

Your router sends all request on port 443 to 192.168.1.5 so it is logical that 
websiteB is served even if you have asked for websiteA.

Why not have http & https for websiteB on 192.168.1.5?

---

### Post by MJN on 2007-03-20
<ignore this post - I was flying off on a tangent!>
 
(P.S. Why no delete function on these forums?!)

---

### Post by aparsons on 2007-03-20
Im no expert either, but from what I was told, HTTPS has to have its own IP address.  Also, I am only issued one IP address from my ISP, so I am forwarding ALL port 80 traffic to my webserver (192.168.1.3) and ALL port 443 traffic to eth:1 of my webserver (192.168.1.5)

---

### Post by Frosty Cold Drink on 2007-03-20
HTTPS does not necessarily need its own IP address.

That said, like astrogazer mentioned, you just plain can't match the host header for an SSL connection until its too late.

---

### Post by Brazen on 2007-03-20
Get rid of the NameVirtualHost directive.  Name Virtual Hosts do not work with SSL, so you have to use IP Virtual Hosts.  Put all of websiteA on 192.168.1.3 and all of WebsiteB on 192.168.1.5.

More info can be found here: [http://httpd.apache.org/docs/2.0/vhosts/name-based.html](http://httpd.apache.org/docs/2.0/vhosts/name-based.html)
and here: [http://httpd.apache.org/docs/2.0/vhosts/ip-based.html](http://httpd.apache.org/docs/2.0/vhosts/ip-based.html)

---

### Post by Quasaur on 2007-05-28
I'm using Feisty on a Dell Inspiron E1505.
i have apache2 serving three virtual hosts...all on lo (127.0.0.1).
I wish to server my virtualhosts on my eth0 as well as my localhost...

do i use Named-Virtualhosts or IP-Virtualhosts...and how?

---

### Post by Frosty Cold Drink on 2007-05-28
> **Quasaur said:**
> I'm using Feisty on a Dell Inspiron E1505.
i have apache2 serving three virtual hosts...all on lo (127.0.0.1).
I wish to server my virtualhosts on my eth0 as well as my localhost...

do i use Named-Virtualhosts or IP-Virtualhosts...and how?

Name-based.

Your VirtualHost tags should look like this
```
<VirtualHost *>
```

And your Listen directive should look like this
```
Listen 80
```

Or if you are using SSL
```
Listen 80
Listen 443
```

---

### Post by Quasaur on 2007-05-28
Thank you for your timely response...

...what about the NameVirtualHost statement...are you saying that I don't need it?

When i placed "Listen 80" and "NameVirtualHost 80" in my /etc/apache2/conf.d/virtual.conf it wouldn't boot...so that question is answered (grin).

But I'm back to Square One; when i try to access the apache2 server on my Ubuntu laptop using a browser from my WinDoze PC using the laptops IP address ([http://192.168.15.100](http://192.168.15.100)) i get th apache2-default directory (like i'm suppose to)

but when i try to use the Ubuntu laptop's name ([http://vistaclm](http://vistaclm)) in a browser from my WinDoze PC i get an error (yes, I've updated the 'hosts' & 'lmhosts' files on the WinDoze PC).

each of the directories is a virtual host.
each of the site files has the following ServerName's & ServerAlias':

default virtual host:
ServerName [www.default.localhost](www.default.localhost)
ServerAlias default.localhost
DocumentRoot /var/www/apache2-default/

dotnet virtual host (copy of my live site [www.clmitchell.net](www.clmitchell.net)):
ServerName [www.dotnet.localhost](www.dotnet.localhost)
ServerAlias dotnet.localhost
DocumentRoot /var/www/dotnet/

phpmyadmint virtual host:
ServerName [www.phpmyadmin.localhost](www.phpmyadmin.localhost)
ServerAlias phpmyadmin.localhost
DocumentRoot /var/www/phpmyadmin/

I want to be able to access the virtual hosts on the Ubuntu laptop using the following URLs (respectively):

[http://vistaclm](http://vistaclm) -- which should go to /var/www/apache2-default/
[http://dotnet.vistaclm](http://dotnet.vistaclm) -- which should go to /var/www/htdocs/
[http://phpmyadmin.vistaclm](http://phpmyadmin.vistaclm) -- which should go to /var/www/phpmyadmin/

Even when i try to access the Ubuntu Laptop from one of the following it doesn't work:

[http://192.168.15.100/default](http://192.168.15.100/default) -- which should go to /var/www/apache2-default/
[http://192.168.15.100/dotnet](http://192.168.15.100/dotnet) -- which should go to /var/www/htdocs/
[http://192.168.15.100/phpmyadmin](http://192.168.15.100/phpmyadmin) -- which should go to /var/www/phpmyadmin/

---

### Post by Frosty Cold Drink on 2007-05-28
> **Quasaur said:**
> Thank you for your timely response...

...what about the NameVirtualHost statement...are you saying that I don't need it?

When i placed "Listen 80" and "NameVirtualHost 80" in my /etc/apache2/conf.d/virtual.conf it wouldn't boot...so that question is answered (grin).
The Listen directive already exists elsewhere. your NameVirtualHost directive should just be the following.

```
NameVirtualHost *
```

> But I'm back to Square One; when i try to access the apache2 server on my Ubuntu laptop using a browser from my WinDoze PC using the laptops IP address ([http://192.168.15.100](http://192.168.15.100)) i get th apache2-default directory (like i'm suppose to)

but when i try to use the Ubuntu laptop's name ([http://vistaclm](http://vistaclm)) in a browser from my WinDoze PC i get an error (yes, I've updated the 'hosts' & 'lmhosts' files on the WinDoze PC).


What is the error?

---


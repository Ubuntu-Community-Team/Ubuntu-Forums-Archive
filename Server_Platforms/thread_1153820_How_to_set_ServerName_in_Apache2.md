---
title: "How to set ServerName in Apache2?"
date: 2009-05-09
forum: Server Platforms
---

### Post by zhanjh on 2009-05-09
I've added these in the file /etc/apache2/httpd.conf

<VirtualHost *>
        ServerName zhanjh_server
        DocumentRoot /var/www
	<Directory /var/www>
		   AllowOverride All
		   Options All
	</Directory>
</VirtualHost>

But when I reload or restart the apache2 I still got this: 
[INDENT]* Restarting web server apache2                                                
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName[/INDENT]

Thank you!

---

### Post by spiderbatdad on 2009-05-09
also put ServerName above the document root section in /etc/apache2/sites-available/default...or whatever virtual host you are using.

---

### Post by zhanjh on 2009-05-09
I added the servername in the /etc/apache2/sites-available/default.But still not working.

/etc/apache2/sites-available/default:
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        ServerName zhanjh_server
        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
		.....
</VirtualHost>

---

### Post by windependence on 2009-05-09
Make sure your /etc/hosts has an entry for itself. Also, make sure your box name IS what you are trying to set it to in Apache. What is the return of the hostname command with no parameters?

-Tim

---

### Post by zhanjh on 2009-05-09
Thank you Spiderbatdad and Windependence.Without your help I cannot resolve it.

But I got a new problem. I found the error message in /var/log/apache2/error.log:
      [Sat May 09 22:27:58 2009] [notice] caught SIGTERM, shutting down
      [Sat May 09 22:27:59 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations

-------------------------------------------------------------
PS&#65306;
/etc/apache2/sites-available/default:
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        ServerName zhanjh.com
        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
    ....
</VirtualHost>

/etc/hosts:
127.0.0.1       zhanjh.com      localhost.localdomain   localhost
127.0.1.1       zhanjh.com

/etc/hostname:
zhanjh.com

---

### Post by daboroe on 2009-05-09
> **zhanjh said:**
> Thank you Spiderbatdad and Windependence.Without your help I cannot resolve it.

But I got a new problem. I found the error message in /var/log/apache2/error.log:
      [Sat May 09 22:27:58 2009] [notice] caught SIGTERM, shutting down
      [Sat May 09 22:27:59 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations

-------------------------------------------------------------
PS&#65306;
/etc/apache2/sites-available/default:
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        ServerName zhanjh.com
        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
    ....
</VirtualHost>

/etc/hosts:
127.0.0.1       zhanjh.com      localhost.localdomain   localhost
127.0.1.1       zhanjh.com

/etc/hostname:
zhanjh.com

How I took some replies it should be this but I might be misunderstanding them as well

```

ServerName zhanjh.com
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
    ....
</VirtualHost>

```

---

### Post by zhanjh on 2009-05-09
Hello daboroe, do you mean put the "ServerName" at the top of the file "/etc/apache2/sites-available/default". I've tried it ,the result turned out to be no differences.

:o I thought the first problem have already be fixed. But I got another new one.

This is the error message in the /var/log/apache2/error.log:
[INDENT]```

[Sat May 09 22:27:58 2009] [notice] caught SIGTERM, shutting down
[Sat May 09 22:27:59 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations

```[/INDENT]
should I just ignore it?

---

### Post by ktritty on 2009-05-10
I had a similar problem.  I changed /etc/hosts so that the IP address matched that of my server.  Then, I had to tweak the ufw too.

[FONT=Courier New]$sudo ufw allow from 0.0.0.0/0 to ip.add.of.server port 80

[FONT=Arial]See if it will work when you replace your domain name with IP addresses only, as a start (that is how I got mine up and running)[/FONT]
[/FONT]

---

### Post by immeëmosol on 2011-01-11
I hope you've all resolved this by now, but for the sake of reference, those last two messages referred to, are *notices*.

They tell that the server has been restarted.

---

### Post by wgroth2 on 2012-10-28
All I had to do was update hosts and the Virtual host entry and default. Thanks for all the info.

br

---


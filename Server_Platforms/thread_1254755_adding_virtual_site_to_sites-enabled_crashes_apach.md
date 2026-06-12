---
title: "adding virtual site to sites-enabled crashes apache2 server"
date: 2009-08-31
forum: Server Platforms
---

### Post by krraleigh on 2009-08-31
I have been trying to add a virtual site to apache2 for about 3 days now, and everytime I "sudo a2ensite filename" and create the sym link apache2 server stops working with no error messages. I look in the error log and I can't seem to find any information on what is causing apache to stop working.
 
What is really interesting is that once the virtual file is added and I try to restart apache2 it always fails. The minute I remove the virtual file "sudo a2dissite filename" and try a restart apache2 works just fine. So why would adding a virtual site to apache2 shut it down? And more importantly where do I look to see why apache2 is failing. I mean there must be a log somewhere that is logging why apache2 is failing?
 
The only info I have is from the apache error.log and this is all it shows:> [Mon Aug 31 04:41:17 2009] [warn] pid file /var/run/apache2.pid overwritten -- Unclean shutdown of previous Apache run?
[Mon Aug 31 04:41:17 2009] [notice] Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.2 with Suhosin-Patch configured -- resuming$
[Mon Aug 31 04:41:58 2009] [notice] Graceful restart requested, doing restart
(2)No such file or directory: apache2: could not open error log file /var/www/log/error.log.
Unable to open logs
 
Can anyone tell me how to find out why apache2 fails when I add virtual sites?
 
Kevin:confused:
 
The web address that shows me how to add virtual sites:
[http://wiki.gandi.net/en/hosting/using-linux/tutorials/ubuntu/virtualhosts](http://wiki.gandi.net/en/hosting/using-linux/tutorials/ubuntu/virtualhosts)
 
virtual site that I am trying to add:
```
<VirtualHost [www.greateropportunites.org]("http://www.greateropportunites.org")>
        ServerAdmin [EMAIL="kraleigh@sbcglobal.net"]xxx[/EMAIL]
        DocumentRoot /var/www/go
        ServerName krr
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/go>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

```

---

### Post by hessiess on 2009-08-31
> **krraleigh said:**
> I have been trying to add a virtual site to apache2 for about 3 days now, and everytime I "sudo a2ensite filename" and create the sym link apache2 server stops working with no error messages. I look in the error log and I can't seem to find any information on what is causing apache to stop working.
 
What is really interesting is that once the virtual file is added and I try to restart apache2 it always fails. The minute I remove the virtual file "sudo a2dissite filename" and try a restart apache2 works just fine. So why would adding a virtual site to apache2 shut it down? And more importantly where do I look to see why apache2 is failing. I mean there must be a log somewhere that is logging why apache2 is failing?
 
The only info I have is from the apache error.log and this is all it shows:
 
Can anyone tell me how to find out why apache2 fails when I add virtual sites?
 
Kevin:confused:
 
The web address that shows me how to add virtual sites:
[http://wiki.gandi.net/en/hosting/using-linux/tutorials/ubuntu/virtualhosts](http://wiki.gandi.net/en/hosting/using-linux/tutorials/ubuntu/virtualhosts)
 
virtual site that I am trying to add:
```
<VirtualHost [www.greateropportunites.org]("http://www.greateropportunites.org")>
        ServerAdmin 
        DocumentRoot /var/www/go
        ServerName krr
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/go>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

```

From what you posted the obvious error is the lack of a end tag for the virtual host, you may also need to add a CustomLog to the virtual host [http://httpd.apache.org/docs/1.3/logs.html](http://httpd.apache.org/docs/1.3/logs.html).

Also you don't want to post your email address on the net unless you want to get spam;).

---

### Post by krraleigh on 2009-08-31
Hi I appreciate the help; I am really stuck here...
 
Here is the file that I am adding in its entirety. I only gave you the pertinent stuff last time.
> <VirtualHost [www.greateropportunites.org]("http://www.greateropportunites.org")>
ServerAdmin xxx
DocumentRoot /var/www/go
ServerName krr
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>
<Directory /var/www/go>
Options Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
allow from all
</Directory>
ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
<Directory "/usr/lib/cgi-bin">
AllowOverride None
Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
Order allow,deny
Allow from all
</Directory>
ErrorLog /var/www/log/error.log
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
LogLevel warn
CustomLog /var/www/log/access.log combined
Alias /doc/ "/usr/share/doc/"
<Directory "/usr/share/doc/">
Options Indexes MultiViews FollowSymLinks
AllowOverride None
Order deny,allow
Deny from all
Allow from 127.0.0.0/255.0.0.0 ::1/128 
</Directory>
</VirtualHost>

 
Can you advise further?
thanx
Kevin

---

### Post by hessiess on 2009-08-31
> **krraleigh said:**
> Hi I appreciate the help; I am really stuck here...
 
Here is the file that I am adding in its entirety. I only gave you the pertinent stuff last time.

 
Can you advise further?
thanx
Kevin

change /var/www/log/error.log to /var/log/http_custom.log(or some file which actually exists) or

```

sudo mkdir /var/www/log

```

Though you don't want your logs in the web root.

---

### Post by krraleigh on 2009-08-31
Hi appreciate the help
 
That is the strangest thing.
The lack of the log file in /var/www/log was the culprit
When I restarted apache2 this time it restarted with no problems.
 
I can finally view my files, and what an incredibly strange way to get here
 
thanx 
Kevin

---

### Post by jpeddicord on 2009-08-31
> **krraleigh said:**
> Hi appreciate the help
 
That is the strangest thing.
The lack of the log file in /var/www/log was the culprit
When I restarted apache2 this time it restarted with no problems.
 
I can finally view my files, and what an incredibly strange way to get here
 
thanx 
Kevin

Error logs are your friend. If they tell you something is wrong, fix it even if it appears unrelated. You'll likely end up with your problem solved. :)

---

### Post by krraleigh on 2009-08-31
Is this a bug with apache2 install?
Seems that it should have installed that directory when I loaded it.
If it is how would I report it so that next guy doesn't get hung out?
 
Kevin

---

### Post by hessiess on 2009-08-31
> **krraleigh said:**
> Is this a bug with apache2 install?
Seems that it should have installed that directory when I loaded it.
If it is how would I report it so that next guy doesn't get hung out?
 
Kevin

Apache dousent create log dirs automatically, there is no need for it to as they dont change often.

---


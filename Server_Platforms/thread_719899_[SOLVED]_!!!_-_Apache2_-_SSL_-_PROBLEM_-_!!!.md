---
title: "[SOLVED] !?!?! - Apache2 - SSL - PROBLEM - ?!?!?!"
date: 2008-03-09
forum: Server Platforms
---

### Post by sevenearths on 2008-03-09
I have apache2 installed and I though I would try to get ssl and https working on my laptop so I followed the following tutorial:

[http://blog.offbytwo.com/2008/01/22/apache2-ssl-in-ubuntu-710-gutsy/]("http://blog.offbytwo.com/2008/01/22/apache2-ssl-in-ubuntu-710-gutsy/")

I didn't know what to do after so tried this tutorial:

[http://ubuntuforums.org/showthread.php?t=51753]("http://ubuntuforums.org/showthread.php?t=51753")

I following it line for line till >apache2-ssl-certificate< on the commandline returned:

```
bash: apache2-ssl-certificate: command not found
```

after which none of this worked:

```
http://localhost:443/
http://localhost:8080/
http://localhost:80/
https://localhost:443/
https://localhost:8080/
https://localhost:80/
```

All of which got me the following:

```
Not Found

The requested URL / was not found on this server.
Apache/2.2.4 (Ubuntu) DAV/2 SVN/1.4.4 PHP/5.2.3-1ubuntu6.3 mod_ssl/2.2.4 OpenSSL/0.9.8e Server at localhost Port 8080
```

So somewhere along the line I mush have offended the apache god. I know doing one tutorial/installation and then just moving on to the next one when nothing would work isn't the cleverest thing in the world, but what can you do.

Can anyone help because Im doing some php development stuff and it has to be in by the morning and Ive got no other platforms to work on
:confused:

(On the bright side of things >http://localhost/< still brings up myphpadmin)

---

### Post by tubezninja on 2008-03-09
I think the instructions you're following are a bit outdated, as[ there is no apache2-ssl-certificate in versions of ubuntu past feisty fawn]("http://rotterdam.ics.uci.edu/drupal/?q=node/128").

If you're using ubuntu 7.10, try the following these instructions:

[https://help.ubuntu.com/7.10/server/C/httpd.html](https://help.ubuntu.com/7.10/server/C/httpd.html)

If you have Apache already working, you can skip down to the "HTTPS configuration" section, which will show you how to create a certificate signing request (CSR), that you can then submit to a Certificate Authority (or sign yourself) and then install.

I was able to follow these same instructions and get SSL working correctly on my server.

---

### Post by Sir.Babau on 2008-03-10
I've gotten myself into a spot of bother. I followed the instructions here:

[http://blog.offbytwo.com/2008/01/22/apache2-ssl-in-ubuntu-710-gutsy/](http://blog.offbytwo.com/2008/01/22/apache2-ssl-in-ubuntu-710-gutsy/)

Then followed the instructions here:

[https://help.ubuntu.com/7.10/server/C/httpd.html](https://help.ubuntu.com/7.10/server/C/httpd.html)

And now Apache seems entirely broken. I can't load a page and sudo /etc/init.d/apache2 restart returns the following:


```

 * Restarting web server apache2                                                httpd (no pid file) not running
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]

```

I've attempted to undo the damage by removing the ssl configuration file in sites-enabled and sites-available. I've also ran a2dismod ssl and removed the lines about SSL from my default configuration file, however it hasn't worked.

Any ideas?

---

### Post by cdenley on 2008-03-10
It sounds like apache is started, but the startup script can't find it's PID. I think this usually happens when it asks you for your SSL passphrase at startup, but you never enter it. When the computer is rebooted, this prompt shows up on the local console. If you don't see any prompt like that, try this
```

sudo killall apache2
sudo /etc/init.d/apache2 start

```

---

### Post by sevenearths on 2008-03-10
We had a big storm last night so I couldn't post the rest of my findings.

I looked in >var/log/apache2/error.log< and found the following:

```
[Sun Mar 09 22:52:46 2008] [error] [client 127.0.0.1] File does not exist: /htdocs
```

So I assumed that apache was looking for a >htdoc< folder somewhere. I ended up creating htdoc folders all over the place. The one that worked was in the root. I can develop for the moment but I would really like >http://localhost:8080/< to look at >/var/www/<, where I had it originaly :(

---

### Post by sevenearths on 2008-03-11
so anybody got any ideas how I can get apached to point to >/var/www< instead of >/htdocs< ???

---

### Post by sevenearths on 2008-03-17
I don't understant is. I've been looking at this problem for some time now...

The file >/etc/apache2/sites-available/default< looks like so 

```
NameVirtualHost *:80
<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
```

The weird this is that every time I type >localhost:80< in a browser I get myPHPAdmin which is located in >/var/www/myphpadmin<.

I have a index.htm file in >/var/www/<. Surely it should load that file.:confused:

Is it possible I have mysql listening in on the same port (80)?

Any help on this would be gratefully recived

---

### Post by sevenearths on 2008-03-17
I tried the recommendations at this post and got the following  ```
arthur@laptop:/etc$ sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                  Syntax error on line 1 of /etc/apache2/httpd.conf:
Invalid command 'localhost', perhaps misspelled or defined by a module not included in the server configuration
                                                                         [fail]

```

:(

---

### Post by cdenley on 2008-03-17
Do you have another site configuration. It sounds like another site configuration (myphpadmin) is read first and made the default. That's why the default configuration link is usually something like "000-default".
```

ls -a /etc/apache2/sites-enabled

```

---

### Post by sevenearths on 2008-03-17
> **cdenley said:**
> Do you have another site configuration. It sounds like another site configuration (myphpadmin) is read first and made the default. That's why the default configuration link is usually something like "000-default".
```

ls -a /etc/apache2/sites-enabled

```

I have got a >000-default< in >/etc/apache2/sites-enabled/<. but it's just pointing to >default< in >/etc/apache2/sites-available/<

I cut down >default< to the following and I still have the error

```
Listen 80

NameVirtualHost localhost 127.0.0.1

<VirtualHost localhost 127.0.0.1>
  DocumentRoot /var/www/
  ServerName localhost
</VirtualHost>
```

To complicat matter further I have ruby-on-rails installed (I followed [this]("http://www.urbanpuddle.com/articles/2007/11/16/install-ruby-rails-on-gutsy-gibbon-nginx-version") tutorial) and it has web server called >nginx< installed with. That might be playing around, but I don't know. I'm not good at config-ing stuff

...later...

Are there any other configuration files that apache uses? like in the home directory?

...later...

Oh! and I've got an empty >httpd.conf< is that good or bad? Plus >ports.conf< just says >Listen 8080<. Should I be listening on 80 as well?

---

### Post by cdenley on 2008-03-17
[http://httpd.apache.org/docs/2.2/mod/core.html#namevirtualhost](http://httpd.apache.org/docs/2.2/mod/core.html#namevirtualhost)

NameVirtualHost should be followed by a hostname or ip, not both. Apache configuration is split into many files (sites-enabled/*,mods-enabled/*,apache2.conf,ports.conf). httpd.conf should be empty since it is only there for compatibility (it used to be the only configuration file). Your ports.conf should have the ports you want apache to listen on. My server uses SSL, so my file has
```

Listen 80
Listen 443

```
Apparently, you put the "Listen 80" line in your site configuration instead, which I think should work, but isn't really correct. All the configuration files are read the same way, it is just split into different files to make it easier to manage.

---

### Post by sevenearths on 2008-03-17
> **cdenley said:**
> [http://httpd.apache.org/docs/2.2/mod/core.html#namevirtualhost](http://httpd.apache.org/docs/2.2/mod/core.html#namevirtualhost)

NameVirtualHost should be followed by a hostname or ip, not both. Apache configuration is split into many files (sites-enabled/*,mods-enabled/*,apache2.conf,ports.conf). httpd.conf should be empty since it is only there for compatibility (it used to be the only configuration file). Your ports.conf should have the ports you want apache to listen on. My server uses SSL, so my file has
```

Listen 80
Listen 443

```
Apparently, you put the "Listen 80" line in your site configuration instead, which I think should work, but isn't really correct. All the configuration files are read the same way, it is just split into different files to make it easier to manage.

right...! just to make stuff simple I've kept my >ports.conf< contents as >Listen 8080< and edited >default< as

```
NameVirtualHost 127.0.0.1

<VirtualHost 127.0.0.1>
  DocumentRoot /var/www/
  ServerName localhost
</VirtualHost>
```

but I still get >/var/www/phpmyadmin/< for >localhost< and >/htdocs/< for >localhost:8080< ](*,)](*,)
:cry::cry:

---

### Post by cdenley on 2008-03-17
Are you reloading your configuration as you change it?
```

sudo /etc/init.d/apache2 reload

```
Some changes, like changing what port it listens to, might require
```

sudo /etc/init.d/apache2 restart

```
Do you have other site configurations? You must have one for port 8080. If not, you probably have it in another configuration file somewhere.

---

### Post by sevenearths on 2008-03-17
I even tried editing my >default< file to

```
NameVirtualHost *:8080

<VirtualHost *:8080>
  DocumentRoot /var/www/
  ServerName localhost
</VirtualHost>
```

and still got >/htdocs/< from >localhost:8080< in the browser (with a  >sudo /etc/init.d/apache2 restart< chucked in)

---

### Post by sevenearths on 2008-03-17
> **cdenley said:**
> Are you reloading your configuration as you change it?
```

sudo /etc/init.d/apache2 reload

```
Some changes, like changing what port it listens to, might require
```

sudo /etc/init.d/apache2 restart

```
Do you have other site configurations? You must have one for port 8080. If not, you probably have it in another configuration file somewhere.

Any ideas where that other configuration file could be located?

---

### Post by cdenley on 2008-03-17
Basically anywhere in /etc/apache2. Try this command.
```

grep -r myphpadmin /etc/apache2

```

---

### Post by sevenearths on 2008-03-17
> **cdenley said:**
> Basically anywhere in /etc/apache2. Try this command.
```

grep -r myphpadmin /etc/apache2

```

tried it just now... didn't return anything. I've also re-edited the >default< file again

```
NameVirtualHost *:8080

<VirtualHost *:8080>
  DocumentRoot /var/www/
  ServerName localhost

    <Directory /var/www/>
        Options FollowSymLinks
        AllowOverride all
        Allow from all
        Order allow,deny
    </Directory>

</VirtualHost>
```

...to no avail :(

...

(I've always wondered how grep works... nice 1!)

---

### Post by cdenley on 2008-03-17
You did try restarting, and it gave no errors? Are you sure something in /var/www isn't redirecting to myphpadmin?
```

grep -r myphpadmin /var/www

```
Apache is the server listening on port 8080, right? Try a non-existent url ([http://localhost:8080/dne](http://localhost:8080/dne)), and it should say something like this at the bottom
```

Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3

```

---

### Post by sevenearths on 2008-03-17
> **cdenley said:**
> You did try restarting, and it gave no errors? Are you sure something in /var/www isn't redirecting to myphpadmin?
```

grep -r myphpadmin /var/www

```
Apache is the server listening on port 8080, right? Try a non-existent url ([http://localhost:8080/dne](http://localhost:8080/dne)), and it should say something like this at the bottom
```

Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3

```

I tried```
localhost:8080/de
```and got```
Apache/2.2.4 (Ubuntu) DAV/2 SVN/1.4.4 PHP/5.2.3-1ubuntu6.3 mod_ssl/2.2.4 OpenSSL/0.9.8e Server at localhost Port 8080
```

don't know why I've still got ssl. I've been trying to get rid of that!

...

things going a bit slow at the moment. I did ```
grep -r phpmyadmin /home/arthur
``` and just waiting to see what it comes up with

...

no joy! :(

---

### Post by sevenearths on 2008-03-17
heres my error log file if it helps

```
[Sun Mar 16 01:05:13 2008] [notice] Apache/2.2.4 (Ubuntu) DAV/2 SVN/1.4.4 PHP/5.2.3-1ubuntu6.3 mod_ssl/2.2.4 OpenSSL/0.9.8e configured -- resuming normal operations
[Sun Mar 16 21:17:12 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sun Mar 16 22:41:43 2008] [notice] Apache/2.2.4 (Ubuntu) DAV/2 SVN/1.4.4 PHP/5.2.3-1ubuntu6.3 mod_ssl/2.2.4 OpenSSL/0.9.8e configured -- resuming normal operations
[Sun Mar 16 22:47:51 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sun Mar 16 22:51:37 2008] [notice] Apache/2.2.4 (Ubuntu) DAV/2 SVN/1.4.4 PHP/5.2.3-1ubuntu6.3 mod_ssl/2.2.4 OpenSSL/0.9.8e configured -- resuming normal operations
[Sun Mar 16 22:55:28 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sun Mar 16 22:59:05 2008] [notice] Apache/2.2.4 (Ubuntu) DAV/2 SVN/1.4.4 PHP/5.2.3-1ubuntu6.3 mod_ssl/2.2.4 OpenSSL/0.9.8e configured -- resuming normal operations
[Sun Mar 16 23:02:43 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sun Mar 16 23:06:26 2008] [notice] Apache/2.2.4 (Ubuntu) DAV/2 SVN/1.4.4 PHP/5.2.3-1ubuntu6.3 mod_ssl/2.2.4 OpenSSL/0.9.8e configured -- resuming normal operations
[Sun Mar 16 23:12:50 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sun Mar 16 23:16:27 2008] [notice] Apache/2.2.4 (Ubuntu) DAV/2 SVN/1.4.4 PHP/5.2.3-1ubuntu6.3 mod_ssl/2.2.4 OpenSSL/0.9.8e configured -- resuming normal operations
[Sun Mar 16 23:34:26 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sun Mar 16 23:38:03 2008] [notice] Apache/2.2.4 (Ubuntu) DAV/2 SVN/1.4.4 PHP/5.2.3-1ubuntu6.3 mod_ssl/2.2.4 OpenSSL/0.9.8e configured -- resuming normal operations
[Mon Mar 17 00:21:37 2008] [notice] caught SIGWINCH, shutting down gracefully
[Mon Mar 17 00:25:11 2008] [notice] Apache/2.2.4 (Ubuntu) DAV/2 SVN/1.4.4 PHP/5.2.3-1ubuntu6.3 mod_ssl/2.2.4 OpenSSL/0.9.8e configured -- resuming normal operations
[Mon Mar 17 00:45:12 2008] [notice] caught SIGWINCH, shutting down gracefully
[Mon Mar 17 00:48:48 2008] [notice] Apache/2.2.4 (Ubuntu) DAV/2 SVN/1.4.4 PHP/5.2.3-1ubuntu6.3 mod_ssl/2.2.4 OpenSSL/0.9.8e configured -- resuming normal operations
[Mon Mar 17 11:22:37 2008] [notice] caught SIGWINCH, shutting down gracefully
[Mon Mar 17 11:23:47 2008] [notice] Apache/2.2.4 (Ubuntu) DAV/2 SVN/1.4.4 PHP/5.2.3-1ubuntu6.3 mod_ssl/2.2.4 OpenSSL/0.9.8e configured -- resuming normal operations
[Mon Mar 17 12:15:08 2008] [notice] SIGHUP received.  Attempting to restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Mon Mar 17 12:15:08 2008] [notice] Apache/2.2.4 (Ubuntu) DAV/2 SVN/1.4.4 PHP/5.2.3-1ubuntu6.3 mod_ssl/2.2.4 OpenSSL/0.9.8e configured -- resuming normal operations
[Mon Mar 17 12:15:28 2008] [error] [client 127.0.0.1] File does not exist: /htdocs/favicon.ico
[Mon Mar 17 12:16:22 2008] [notice] caught SIGWINCH, shutting down gracefully
[Mon Mar 17 12:16:33 2008] [notice] Apache/2.2.4 (Ubuntu) DAV/2 SVN/1.4.4 PHP/5.2.3-1ubuntu6.3 mod_ssl/2.2.4 OpenSSL/0.9.8e configured -- resuming normal operations
[Mon Mar 17 12:23:10 2008] [notice] caught SIGTERM, shutting down
[Mon Mar 17 12:32:46 2008] [notice] Apache/2.2.4 (Ubuntu) DAV/2 SVN/1.4.4 PHP/5.2.3-1ubuntu6.3 mod_ssl/2.2.4 OpenSSL/0.9.8e configured -- resuming normal operations
[Mon Mar 17 12:38:35 2008] [notice] caught SIGWINCH, shutting down gracefully
[Mon Mar 17 12:38:47 2008] [notice] Apache/2.2.4 (Ubuntu) DAV/2 SVN/1.4.4 PHP/5.2.3-1ubuntu6.3 mod_ssl/2.2.4 OpenSSL/0.9.8e configured -- resuming normal operations
[Mon Mar 17 12:46:20 2008] [notice] caught SIGWINCH, shutting down gracefully
[Mon Mar 17 12:46:31 2008] [notice] Apache/2.2.4 (Ubuntu) DAV/2 SVN/1.4.4 PHP/5.2.3-1ubuntu6.3 mod_ssl/2.2.4 OpenSSL/0.9.8e configured -- resuming normal operations
[Mon Mar 17 12:54:36 2008] [notice] caught SIGWINCH, shutting down gracefully
[Mon Mar 17 12:54:47 2008] [notice] Apache/2.2.4 (Ubuntu) DAV/2 SVN/1.4.4 PHP/5.2.3-1ubuntu6.3 mod_ssl/2.2.4 OpenSSL/0.9.8e configured -- resuming normal operations
[Mon Mar 17 13:19:45 2008] [notice] caught SIGWINCH, shutting down gracefully
[Mon Mar 17 13:19:55 2008] [notice] Apache/2.2.4 (Ubuntu) DAV/2 SVN/1.4.4 PHP/5.2.3-1ubuntu6.3 mod_ssl/2.2.4 OpenSSL/0.9.8e configured -- resuming normal operations
[Mon Mar 17 13:47:33 2008] [notice] caught SIGWINCH, shutting down gracefully
[Mon Mar 17 13:50:55 2008] [notice] Apache/2.2.4 (Ubuntu) DAV/2 SVN/1.4.4 PHP/5.2.3-1ubuntu6.3 mod_ssl/2.2.4 OpenSSL/0.9.8e configured -- resuming normal operations
[Mon Mar 17 13:51:12 2008] [error] [client 127.0.0.1] File does not exist: /htdocs/favicon.ico
[Mon Mar 17 13:59:42 2008] [error] [client 127.0.0.1] File does not exist: /htdocs/favicon.ico
[Mon Mar 17 14:02:34 2008] [notice] caught SIGWINCH, shutting down gracefully
[Mon Mar 17 14:02:44 2008] [notice] Apache/2.2.4 (Ubuntu) DAV/2 SVN/1.4.4 PHP/5.2.3-1ubuntu6.3 mod_ssl/2.2.4 OpenSSL/0.9.8e configured -- resuming normal operations
[Mon Mar 17 14:18:41 2008] [notice] caught SIGWINCH, shutting down gracefully
[Mon Mar 17 14:18:51 2008] [notice] Apache/2.2.4 (Ubuntu) DAV/2 SVN/1.4.4 PHP/5.2.3-1ubuntu6.3 mod_ssl/2.2.4 OpenSSL/0.9.8e configured -- resuming normal operations
[Mon Mar 17 14:33:31 2008] [notice] caught SIGWINCH, shutting down gracefully
[Mon Mar 17 14:33:41 2008] [notice] Apache/2.2.4 (Ubuntu) DAV/2 SVN/1.4.4 PHP/5.2.3-1ubuntu6.3 mod_ssl/2.2.4 OpenSSL/0.9.8e configured -- resuming normal operations
[Mon Mar 17 14:50:33 2008] [error] [client 127.0.0.1] File does not exist: /htdocs/de
```

---

### Post by cdenley on 2008-03-17
```

grep -r htdocs /etc/apache2
ls -l /etc/apache2/sites-available/default

```

---

### Post by sevenearths on 2008-03-17
> **cdenley said:**
> ```

grep -r htdocs /etc/apache2
ls -l /etc/apache2/sites-available/default

```

```
grep -r htdocs /etc/apache2
```
returns...nothing! :(

```
ls -l /etc/apache2/sites-available/default
```

returns

```
-rw-r--r-- 1 root root 1524 2008-03-17 14:33 /etc/apache2/sites-available/default
```

---

### Post by cdenley on 2008-03-17
```

grep Include /etc/apache2/apache2.conf

```

---

### Post by sevenearths on 2008-03-17
> **cdenley said:**
> ```

grep Include /etc/apache2/apache2.conf

```

result

```
# Possible values include: debug, info, notice, warn, error, crit,
# Set to "EMail" to also include a mailto: link to the ServerAdmin.
# includes to substitute the appropriate text.
#   Alias /error/include/ "/your/include/path/"
# /usr/share/apache2/error/include/ files and copying them to /your/include/path/, 
# even on a per-VirtualHost basis.  The default include files will display
# The internationalized error documents require mod_alias, mod_include
```

---

### Post by cdenley on 2008-03-17
There is your problem. Your site configuration is not being read. You must have deleted "Include /etc/apache2/sites-enabled/" from your apache2.conf file. I attached what I believe is the default from my gutsy server. I guess if you have no site configuration, it defaults the root directory to /htdocs.

[ATTACH]62888[/ATTACH]

---

### Post by sevenearths on 2008-03-17
> **cdenley said:**
> There is your problem. Your site configuration is not being read. You must have deleted "Include /etc/apache2/sites-enabled/" from your apache2.conf file. I attached what I believe is the default from my gutsy server. I guess if you have no site configuration, it defaults the root directory to /htdocs.

[ATTACH]62888[/ATTACH]

...and the nightmare ends \\:D/:-D\\:D/:-D\\:D/:-D\\:D/:-D

...

(it was the line at the bottom, wasn't it)

---


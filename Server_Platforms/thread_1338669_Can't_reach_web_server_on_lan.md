---
title: "Can't reach web server on lan"
date: 2009-11-26
forum: Server Platforms
---

### Post by Mustafa Ismail Mustafa on 2009-11-26
Hi all,

I've been working on this for hours now and searching the forum for 10-15 minutes before posting has not yielded an answer. I'm not a total newbie, but I am officially moving from a Windows environment to Linux.

Basically, I've setup a (for now) local web server on a separate box (LAMP). Its supposed to be able to handle several virtual hosts by name, but here is what is happening:

Browse to "http://192.168.1.165" I get the standard "It Works!!" page
Browse to "http://192.168.1.165/index.php" I get the standard PhpInfo() results

Now, I've setup 2 domains (one as a clean test after the first repeatedly failed) and with the same result, 404. (I'm browsing as: [http://192.168.1.165/domain1.com](http://192.168.1.165/domain1.com) (every variant too)) and they are all giving me the same thing.

I must be doing something wrong I just can't figure out what it is.

I'm not sure what to post so I've pasted the apache2.conf and the virtual host file for the example "domain1.com"

TIA

apache2.conf
```

ServerRoot "/etc/apache2"

LockFile /var/lock/apache2/accept.lock

PidFile ${APACHE_PID_FILE}

Timeout 20

KeepAlive On

MaxKeepAliveRequests 150

KeepAliveTimeout 2

<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

<IfModule mpm_worker_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}

AccessFileName .htaccess

<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>

DefaultType text/plain

HostnameLookups Off

ErrorLog /var/log/apache2/error.log

LogLevel warn

Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

Include /etc/apache2/httpd.conf

Include /etc/apache2/ports.conf

LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent


ServerTokens Full

ServerSignature On

Include /etc/apache2/conf.d/

Include /etc/apache2/sites-enabled/

ServerName nvHermes

NameVirtualHost *:80

<IfModule mod_ssl.c>
    NameVirtualHost *:443
</IfModule>

```

Domain1.com virtualhost file
```
<VirtualHost *:80>

  ServerAdmin webmaster@domain1.com
  ServerName  domain1.com
  ServerAlias www.domain1.com

  # Index file and Document Root (where the public files are located)
  DirectoryIndex index.html
  DocumentRoot /home/steve/public_html/domain1.com/public


  # Custom log file locations
  LogLevel warn
  ErrorLog  /home/steve/public_html/domain1.com/log/error.log
  CustomLog /home/steve/public_html/domain1.com/log/access.log combined

</VirtualHost>

```

---

### Post by munky99999 on 2009-11-26
> **Can't reach web server on lan**

Browse to "http://192.168.1.165" I get the standard "It Works!!" page
Sure sounds like you can reach it :)

> Browse to "http://192.168.1.165/index.php" I get the standard PhpInfo() results
[https://help.ubuntu.com/9.10/serverguide/C/php5.html](https://help.ubuntu.com/9.10/serverguide/C/php5.html)

Very very simple. You dont require most of those packages.
php5-cli
php5-cgi
php5-mysql
php5-pgsql

Only get those if you really require those.

Otherwise ya. Installing php is smooth.

> Now, I've setup 2 domains (one as a clean test after the first repeatedly failed) and with the same result, 404. (I'm browsing as: [http://192.168.1.165/domain1.com](http://192.168.1.165/domain1.com) (every variant too)) and they are all giving me the same thing.
You set them up in BIND? Or with an online registrar? Or Active directory? I dont follow.

> Domain1.com virtualhost file
<VirtualHost *:80>

  ServerAdmin [email]webmaster@domain1.com[/email]
  ServerName  domain1.com
  ServerAlias [www.domain1.com](www.domain1.com)

Oh. What you are doing wrong is.

Say I register [www.munky.com](www.munky.com). I set it to link up to my webserver box at say 198.103.98.139

Then later since nobody ever goes to my website and it's running on a beast computer. I want to host another website on the server.

So I register [www.munkygonewild.com](www.munkygonewild.com). I set it up to link up to my same webserver box again at 198.103.98.139

What Virtualhosts does. Is make it so. People looking to get to the [www.munkygonewild.com](www.munkygonewild.com) website; will see that website instead of [www.munky.com](www.munky.com)



This doesnt mean you can just put [www.munky.com](www.munky.com) in the website bar and find it on the net because you set it up like that.




Now what you can do. Which you dont need virtualhosts for. Setup on a DNS server. A host record for domain1.com which points to your box.

Now anyone who uses that DNS server for their name resolution. Will get sent to your webserver instead of whatever runs that website for real on the internet.

---

### Post by Vegan on 2009-11-26
try putting the IP address in each client's hosts file.

---

### Post by Mustafa Ismail Mustafa on 2009-11-27
OK, let me put it another way.

The machine is being setup as a web host for several sites on the local lan.  It will not be exposed to the www until later.

Having said that, yes the server is reachable by ping and by browsing to the default site ([http://192.168.1.165/](http://192.168.1.165/) in this case) is reachable.

What I can't seem to figure out how to have several sites hosted and reach those sites.

Meaning, instead of browsing the default site, I should be able to browse the other sites like so:

[http://192.168.1.165/](http://192.168.1.165/)          <--- Default site
[http://192.168.1.165/site1](http://192.168.1.165/site1)   <--- Site1
[http://192.168.1.165/site2](http://192.168.1.165/site2)   <--- Site2

And so on.

Now, what I tried to do was instead of site1 or site2, I'd have site1.com. So browsing to [http://192.168.1.165/site1.com/](http://192.168.1.165/site1.com/) is returning a 404.

I hope that better explains my problem :)

---

### Post by Mustafa Ismail Mustafa on 2009-11-27
Can you provide an example please?

Thanks.

---

### Post by gombadi on 2009-11-27
> 
<VirtualHost *:80>

  ServerAdmin [email]webmaster@domain1.com[/email]
  ServerName  domain1.com
  ServerAlias [www.domain1.com](www.domain1.com)

  # Index file and Document Root (where the public files are located)
  DirectoryIndex index.html
  DocumentRoot /home/steve/public_html/domain1.com/public


  # Custom log file locations
  LogLevel warn
  ErrorLog  /home/steve/public_html/domain1.com/log/error.log
  CustomLog /home/steve/public_html/domain1.com/log/access.log combined

</VirtualHost>


> 
[http://192.168.1.165/](http://192.168.1.165/) <--- Default site
[http://192.168.1.165/site1](http://192.168.1.165/site1) <--- Site1
[http://192.168.1.165/site2](http://192.168.1.165/site2) <--- Site2


When you connect to apache it will try and match the domain you are requesting with the ServerName and ServerAlias entries in its virtualhost entries.

You are requesting a name of 192.168.1.165 but only have domain1.com and [www.domain1.com](www.domain1.com) listed as valid names therefore apache will not use the virtualhost you have shown us.

The way it works is the [http://192.168.1.165](http://192.168.1.165) is translated into the documentroot part defined in the matching virtualhost (in your case this does not match) - /home/steve/public_html/domain1.com/public - and then the /site1 or /site2 is added to the document root to get the full path to the files that apache needs to serve.




Possible solutions -
1 - remove the ServerName and ServerAlias entries so the virtualhost you showed is the default for all unmatched domains. Your site files will then be at /home/steve/public_html/domain1.com/public/site1 and at 
/home/steve/public_html/domain1.com/public/site2. 

2 - if you are going to be using many different domains then create dns entries or entries in your /etc/hosts file so in your browser you enter [http://www.domain1.com/](http://www.domain1.com/), this will be matched by apache and will start looking in the documentroot defined for that virtualhost.


By the way - Log files are your friend - have a look at the log files you have defined in apache as they will tell you a lot about what it is trying to do and what files it is trying to find.

---

### Post by Mustafa Ismail Mustafa on 2009-11-27
First off, let me say thank you. I'm really appreciating the explanations; they really help with my transition.

Now, I tried something a few minutes before your post and to me its just WEIRD.

I moved the directory from *my* directory (/home/steve/public_html/) to /var/www.  and after altering the vhost file to point to the new location, it showed me a directory listing and not a 404! (remember, I'm doing all the changes on the server box through ssh and the browsing from a compeltely different box).

moving it back returned the original problem.

As for the possible solutions:

1. no change. One question, wouldn't the site files then be placed at "/home/steve/public_html/domain1.com/public"   ?

2. This will work on another box? (don't forget, I'm building the server on one box and testing the sites from another)

Many, many thanks.

---

### Post by Vegan on 2009-11-28
You need to change permissions to move the default location for the web server. I am lazy, I made directories under /dev/www to host sites with.

If you want to use user home directories, I suggest /home/user1/www and make that folder 777 and point the site there.


You do not need to modify the apache2.conf file, instead httpd.conf is used for options.

ech vhost is best in a separate file like I do it, so its quick to change one site if needed.

---

### Post by Mustafa Ismail Mustafa on 2009-11-28
> **Vegan said:**
> You need to change permissions to move the default location for the web server. I am lazy, I made directories under /dev/www to host sites with.

**If you want to use user home directories, I suggest /home/user1/www and make that folder 777 and point the site there.**


You do not need to modify the apache2.conf file, instead httpd.conf is used for options.

ech vhost is best in a separate file like I do it, so its quick to change one site if needed.

Wouldn't that be a little dangerous?

I do place each vhost in its own file in the sites-available folder, then I just enable or disable them.

As is, I've tried to place them in the /var/www (and altered each site's vhost file accordingly) but what's happening now is that I get the directory listing of the site's root folder rather than default index.html.  Meaning, if the site was located at /var/www/site1 and the document root (as specified in the vhost file) is /var/www/site1/public and the index.html file is at /var/www/site1/public/index.html, the browser displays the contents of the /var/www/site1 directory.

---

### Post by windependence on 2009-11-28
Yes, it's quite dangerous and not necessary or recommended. When folks don't understand permissions and ownership, they resort to the easiest path to make it "just work".

I just scanned over your post, but from what I got, if you are using this only a local LAN, you don't even need virtual hosts here. Simply set up your web root wherever you want it, say /var/www and then make your other site directories under that one, so you would have a structure like gombadi mentioned:

[http://192.168.1.165/](http://192.168.1.165/) 
[http://192.168.1.165/site1](http://192.168.1.165/site1)
[http://192.168.1.165/site2](http://192.168.1.165/site2) 

To get to the main site, you browse to [http://192.168.1.165/](http://192.168.1.165/)
To browse to site1 you go to [http://192.168.1.165/site1](http://192.168.1.165/site1)
To browse to site2 you go to [http://192.168.1.165/site2]("http://192.168.1.165/site1")

etc. etc.

NO virtual hosts are even necessary here. So your source files would go in these locations:

root (default) site: /var/www
site1:  /var/www/site1
site2:  /var/www/site2

etc.

See where we are going here? Once you specify the site root, with simply subdirectories, you don't need to do anything else.

One more thing. The web server runs as www-data in Ubuntu I believe. After you get all your files in place and are ready to test, you must adjust your permissions and ownership. Here is how I do it:

```
chmod -R 755 /var/www
chown -R www-data:www-data /var/www
```

That's it. Your directory listing problem is another issue. The problem is most likely in your conf file. The line below is either missing, or commented out, or in the wrong place:

```
DirectoryIndex index.html
```

You may want to add other formats as index pages:

```
DirectoryIndex index.html index.shtml index.php
```

I'll read your post a bit closer tomorrow and see if we missed anything. Let me know if you try suggestions and the outcome.

-Tim

---

### Post by Mustafa Ismail Mustafa on 2009-11-28
Thank you so much windependence.  I'm going to try to do exactly that the moment I get back to my computer and I'll get back to you on what's happening.  One other thing, the reason I'm playing around with the virtual hosts is that later on, this server will go live.  How does that twist things?

Again, thank you!

---

### Post by Meskis on 2010-03-04
I think he wnted something like this....
```

<VirtualHost *>
  ServerName [www.xxx.lt](www.xxx.lt)
  ServerAlias [www.xxx.lt](www.xxx.lt)
  DirectoryIndex index.php index.html
  DocumentRoot /var/www/www.xxx.lt/
  <Directory />
    Options FollowSymLinks
    AllowOverride None
  </Directory>
  <Directory /var/www/www.xxx.lt/>
    Options -Indexes FollowSymLinks MultiViews
    AllowOverride None
    Order allow,deny
    allow from all
  </Directory>
  <Directory /var/www/www.xxx.lt/dom1/>
    Options -Indexes FollowSymLinks MultiViews
    AllowOverride None
    Order allow,deny
    allow from all
  </Directory>
  <Directory /var/www/www.xxx.lt/dom2/>
    Options -Indexes FollowSymLinks MultiViews
    AllowOverride None
    Order allow,deny
    allow from all
  </Directory>
  ScriptAlias /dlkz/cgi-bin/ /var/www/www.xxx.lt/dom1/cgi-bin/
  <Directory "/var/www/www.xxx.lt/dom1/cgi-bin">
    Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
  </Directory>
    ErrorLog /var/www/www.xxx.lt/logs/error.log
    CustomLog /var/www/www.xxx.lt/logs/access.log combined
  LogLevel warn
  ServerSignature On
	ProxyPreserveHost On
        ProxyRequests Off
        ProxyPass /dom3/ [http://192.168.1.1/someplace/](http://192.168.1.1/someplace/)
        ProxyHTMLURLMap [http://192.168.1.1/someplace/](http://192.168.1.1/someplace/) /dom3
                <Location /dom3/>
                   ProxyPassReverse  [http://192.168.1.1/someplace/](http://192.168.1.1/someplace/)
                   SetOutputFilter proxy-html
                   ProxyHTMLURLMap /               /dom3/
                   ProxyHTMLURLMap /dom3/          /dom3/
		   RequestHeader   unset   Accept-Encoding	
                </Location>
	
</VirtualHost>
```

---


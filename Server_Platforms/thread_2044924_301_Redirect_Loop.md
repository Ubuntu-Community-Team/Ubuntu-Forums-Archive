---
title: "301 Redirect Loop"
date: 2012-08-20
forum: Server Platforms
---

### Post by bigmonmulgrew on 2012-08-20
Hi guys
I have a small web server running.

It has ubuntu 11.10
It runs apache2 and drupal

I was trying to setup a 301 redirect so I didnt get penalised for duplicate content

I added the line
```
Redirect / http://mysite.co.uk/
```
into the apache sites file

When I tested it I got an error message in the browser saying there is a redirect loop.

Any idea where I start looking for whats causing this or a better way to do it.

---

### Post by koenn on 2012-08-20
What's the original URL you're trying to redirect, the one that would point to the duplicate content ?

---

### Post by bigmonmulgrew on 2012-08-20
actually there are a couple.
the one I'm experimenting with is bigmonmulgrew.co.uk
I'm trying to redirect
[www.bigmonmulgrew.co.uk](www.bigmonmulgrew.co.uk) --> bigmonmulgrew.co.uk

---

### Post by bigmonmulgrew on 2012-08-20
OK i just got it working. I typed this at the top of my apache sites file
```
<VirtualHost www.bigmonmulgrew.co.uk:80>
Redirect 301 / http://bigmonmulgrew.co.uk/
</VirtualHost>
```

I get an error ( 2 actually) when reloading apache

```
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName                                                                                                                                                                
[Mon Aug 20 22:42:20 2012] [error] (EAI 2)Name or service not known: Failed to resolve server name for my.ip.addr.ess (check DNS) -- or specify an explicit ServerName  
```
 

I was getting the one about the server name already
The EAI 2 one is new after applying this change.

It does seem to work. If I type the url with the www into a browser the browser trims the www however I checked it with a couple of SEO tools and they still say its not redirecting.

Any ideas

---

### Post by koenn on 2012-08-20
kinda figures.
You initially had : 
redirect anything that artives "here" to "that site';
now if 'here' and 'that site' are on the same machine, you have an endless loop, because your redirect comes back and is redirected again

using vhosts to identify the incoming URL's and thereby redirecting only the 'old' to the 'new' would fix that. 

That warning you get is a comman one; you can ignore it, or fix it by
- check DNS or /etc/hosts and make sure the server can resolve its own hostname  (ore revese lookup ? I forgot ...)
- set a Servername in your vhost definitionq, like
```

<VirtualHost www.bigmonmulgrew.co.uk:80>
    ServerName bigmonmulgrew.co.uk
    Redirect 301 / http://bigmonmulgrew.co.uk/
</VirtualHost>

```

---

### Post by koenn on 2012-08-20
> t does seem to work. If I type the url with the www into a browser the browser trims the www however I checked it with a couple of SEO tools and they still say its not redirectin
Don't know much about SEO tools, but if you actually see the URL changing in the browser address bar, that's the 301 redirect happening right there:
- you're browser sends a request (old URL)
- the server says : send that request again, to (redirection target)
- your browser sends a request again (new url) -> at this point, you see the change in the address bar

---

### Post by bigmonmulgrew on 2012-08-20
Ok firstly I googled the first error I was getting
To solve this I added 
```
ServerName localhost
```
to /etc/apache2/httpd.conf

I then made the change you suggested adding
```
ServerName bigmonmulgrew.co.uk
```
to my site file.

Now I do get redirected but its as If I've just typed in my servers IP address. I get the holding page for the server.

---

### Post by koenn on 2012-08-21
Sorry, I don't have a clear picture in my head of your website situation and all that; I'm just trying yo point you in a generally right direction.

Your vhost confs may be off a bit, see
[http://httpd.apache.org/docs/2.2/vhosts/name-based.html](http://httpd.apache.org/docs/2.2/vhosts/name-based.html) ; 
then do the redirects in old vhost, with / -> new vhost

---

### Post by bigmonmulgrew on 2012-08-22
Hi guys I finally got it working.
Firstly I found a great tool for checking if the redirect is working here
[http://www.ragepank.com/redirect-check/](http://www.ragepank.com/redirect-check/)

Firstly I added this at the top of my apache site file
```
<VirtualHost *:80>
   ServerName www.bigmonmulgrew.co.uk
     Redirect 301 / http://bigmonmulgrew.co.uk/
</VirtualHost>
```

This worked great except the above site mentioned that bigmonmulgrew.co.uk and bigmonmulgrew.co.uk/index.php would count as duplicate content.

I really like the site because it mentions several ways to solve this problem.

It gave me this code to add to apache
```
RewriteEngine on
Options +FollowSymLinks
RewriteCond %{THE_REQUEST} ^.*/index\.php
RewriteRule ^(.*)index.php$ http://www.bigmonmulgrew.co.uk/$1 [R=301,L]
```

Now I have heard that using rewrite can take up more rescources. I'd rather use a less resource intensive method if possible, although in my situation resources are not an issue
I'm wondering if using both these methods together mean I will only see the resource hit when someone directly accesses index.php. I don't know a great deal about how rewrite works so if anyone  can clarify this then that would be great.
For now though I'm marking the thread as solved.

My full site file is below, although I've removed the admin email address for obvious reasons. 
/etc/apache2/sites-available/bigmonmulgrew.co.uk
```
<VirtualHost *:80>
   ServerName www.bigmonmulgrew.co.uk
     Redirect 301 / http://bigmonmulgrew.co.uk/
</VirtualHost>
<VirtualHost *:80>
ServerAdmin admin@localhost
ServerName bigmonmulgrew.co.uk
ServerAlias test.bigmonmulgrew.co.uk

RewriteEngine on
Options +FollowSymLinks
RewriteCond %{THE_REQUEST} ^.*/index\.php
RewriteRule ^(.*)index.php$ http://www.bigmonmulgrew.co.uk/$1 [R=301,L]

DocumentRoot /var/www/bigmonmulgrew
<Directory />
Options FollowSymLinks
AllowOverride All
</Directory>
<Directory /var/www/bigmonmulgrew>
Options Indexes FollowSymLinks MultiViews
AllowOverride All
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

ErrorLog /error.log

# Possible values include: debug, info, notice, warn, error, 
# crit, alert, emerg.
LogLevel warn

CustomLog /access.log combined

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

---


---
title: "Enable mod_rewrite - normal advice not working"
date: 2008-08-09
forum: Server Platforms
---

### Post by Michael Daly on 2008-08-09
I've enabled mod_rewrite and the following is in the default site-enabled:
```

<Directory />
	Options FollowSymLinks
	AllowOverride All
	Order allow,deny
	allow from all
</Directory> 

<Directory /var/www/>
	Options FollowSymLinks
	AllowOverride All
	Order allow,deny
	allow from all
</Directory> 

```

My virtual server html files are currently in /var/www/ (just one html file) and the virtual host is in sites-available and enabled in sites-enabled.  Everything works fine if I comment out the rewrite statements in the <virtual host> file, but if I enable the rewrite statements, I get:

You don't have permission to access / on this server.

Most advice states that this goes away if *AllowOverride All* is in the default but I still get the problem.  

Any advice would be appriciated - I'm sure it's a trivial oversight.

---

### Post by mbeach on 2008-08-09
Your setup does look good, what is your RewriteRule look like?

---

### Post by mbeach on 2008-08-09
does your error log give you any indication as to what the error is - .htacces not readable?  

by default:
/var/log/apache2/error.log

---

### Post by Michael Daly on 2008-08-09
There's no .htaccess file - everything should be fine with the overall config.

The error.log file only shows Apache restarts etc.  No specific error related to attempting to display the page.  Access.log shows a 403 on the GET (specifically - "GET / HTTP/1.1" 403 274), but that's reasonable considering the "You don't have permission..." error message, I assume.

I've got a rewrite error log, but it never shows anything - the error occurs before the rewrite module executes as far as I can tell.

The rewrite code is just:
```

<IfModule mod_rewrite.c>
RewriteEngine on
RewriteLog /var/log/glk_rewrite.log
RewriteLogLevel 10

RewriteCond %{REQUEST_URI}  !^$ 
RewriteRule ^(.*)$    http://greatlakeskayaker.ca      [F,L,R]
</IfModule>

```

The purpose of this code is just to force any URL pointing to the domain name to display index.html which in turn just shows that the web site is offline (this web site is the backup that I want running when the main site is down for maintenance).

If I change the rewrite code to:

```

<IfModule mod_rewrite.c>
#RewriteEngine on
#RewriteLog /var/log/glk_rewrite.log
#RewriteLogLevel 10

#RewriteCond %{REQUEST_URI}  !^$ 
#RewriteRule ^(.*)$    http://greatlakeskayaker.ca      [F,L,R]
</IfModule>

```

i.e., just comment out the rewrite statements, the web page shows (without the ability to do rewrites).  Uncommented generates the error.

---

### Post by chickpea on 2008-08-10
why do you set "F(=forbidden)" flag? as far as i know setting this flag is supposed to make apache respond a 403 error message. i don't think people would get the index.html file which you want to show them that way. so just deleting "F" flag would solve your problem?

---

### Post by Michael Daly on 2008-08-10
That would be my "DUH" moment!

I copied the rewrite code and changed it a bit.  The stupid part of my brain decided that "F=final" (i.e. instead of "L=last") so I let it go.

That fixes this problem.  

Thanks a bunch!

---


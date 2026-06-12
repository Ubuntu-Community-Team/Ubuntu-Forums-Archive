---
title: "Apache2 rewrite_module not loaded"
date: 2011-03-19
forum: Server Platforms
---

### Post by thunderbirdje on 2011-03-19
Hi everyone,

I need some advice :-)

My rewrite_module is not loaded checked with a [script]("http://www.webune.com/forums/how-to-test-check-if-mod-rewrite-is-enabled-t40.html") and double checked with **sudo apache2ctl -l**. Output: [I][HTML]Compiled in modules:
  core.c
  mod_log_config.c
  mod_logio.c
  prefork.c
  http_core.c
  mod_so.c[/HTML][/I]

One of the Virtual hosts in httpd.conf (probably it's not best practice for Apache2?) is:

[HTML]<VirtualHost *:80>
DocumentRoot /var/www/cms/public
ServerName cms.localhost
</VirtualHost>[/HTML]

The .htaccess file for this Virtual Host in /var/www/cms/public looks like:
[HTML]RewriteEngine On
RewriteCond %{REQUEST_FILENAME} -s [OR]
RewriteCond %{REQUEST_FILENAME} -l [OR]
RewriteCond %{REQUEST_FILENAME} -d
RewriteRule ^.*$ - [NC,L]
RewriteRule ^.*$ index.php [NC,L[/HTML]]

The rewrite_module doesn't work because I always get: HTTP Error 500 (just 'static' pages work perfect.

I tried everything but I'm not a apache2 config specialist so I should ask some help after searching myself for 10 hours now :o

If you need more information I will try to serve it!

Thank you!

---

### Post by freebeer on 2011-03-19
try enabling it. :)

```

sudo a2enmod rewrite

```

should do the trick for you.

---

### Post by thunderbirdje on 2011-03-19
> **freebeer said:**
> try enabling it. :)

```

sudo a2enmod rewrite

```

should do the trick for you.

Sounds great, however **Module rewrite already enabled** while output of **sudo apache2ctl -l** doesn't show the rewrite module loaded? Maybe I can check something else as well?

```
user@computername:~$ sudo a2enmod rewrite
Module rewrite already enabled
user@computername:~$ sudo apache2ctl -l
Compiled in modules:
  core.c
  mod_log_config.c
  mod_logio.c
  prefork.c
  http_core.c
  mod_so.c
```

---

### Post by wongo888 on 2011-03-19
Check that your Apache settings allow htaccess use in the default webroot:

```
$ cat /etc/apache2/sites-available/default
```

Check out the Troubleshooting section in the Apache docs

[http://httpd.apache.org/docs/current/howto/htaccess.html#troubleshoot](http://httpd.apache.org/docs/current/howto/htaccess.html#troubleshoot)

> Most commonly, the problem is that **AllowOverride** is not set such that your configuration directives are being honored. Make sure that you don't have a AllowOverride None in effect for the file scope in question. A good test for this is to put garbage in your .htaccess file and reload. If a server error is not generated, then you almost certainly have AllowOverride None in effect.

If, on the other hand, you are getting server errors when trying to access documents, check your Apache error log. It will likely tell you that the directive used in your .htaccess file is not permitted. Alternately, it may tell you that you had a syntax error, which you will then need to fix.

---

### Post by freebeer on 2011-03-19
Yep.. that was the problem for me.  Not sure if that's the same thing for the OP, though.

The OP was a little further along the path than I was - I hadn't yet gotten to test out redirection yet when I posted.  But once I got my other issue resolved, this one was next on my list and I, too, ran into the issue.

I fixed it by setting AllowOverride All in the <Directory> section of /sites-available/default.

Thanks!

---

### Post by wongo888 on 2011-03-20
Also, check your Apache error logs.

---

### Post by thunderbirdje on 2011-03-20
> **wongo888 said:**
> Also, check your Apache error logs.

Thank you so much wongo! It works (I also had to delete my VirtualHost's settings, which probably messed things up).

To help others:

I've changed **AllowOveride None** into **AllowOveride All** and put garbage in my **.htaccess** file. An *error* was produced in the */var/apache2/error.log*.

To make my "website under construction" work I had to delete all my Virtual Hosts from httpd.conf and I pointed the DocumentRoot in _/etc/apache2/sites-available/default_ to my "website under construction".

```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www/zf_cms/public
	<Directory />
		Options FollowSymLinks
		AllowOverride All
	</Directory>

```

Then putting the right _.htaccess_ information into /var/www/zf_cms/public:

```
SetEnv APPLICATION_ENV development
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} -s [OR]
RewriteCond %{REQUEST_FILENAME} -l [OR]
RewriteCond %{REQUEST_FILENAME} -d
RewriteRule ^.*$ - [NC,L]
RewriteRule ^.*$ index.php [NC,L]
```

Probably there is better practice by making a second VirtualHost or so but I'm not that professional (yet? ;-))

Thanks again!

---


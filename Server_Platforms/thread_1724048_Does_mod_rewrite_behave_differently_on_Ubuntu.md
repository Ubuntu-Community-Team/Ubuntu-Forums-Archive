---
title: "Does mod_rewrite behave differently on Ubuntu?"
date: 2011-04-07
forum: Server Platforms
---

### Post by sjlsam on 2011-04-07
I installed Ubuntu with Apache/PHP as a development server

I followed the steps to enable mod_rewrite (a2enmode rewrite, AllowOverride settings,etc)

mod_rewrite is working, but it seems to be behaving differently from the other servers I work with

Consider the following .htaccess:

```
RewriteEngine on
RewriteRule ^submit/bulk/?$ "submit_bulk.php"
RewriteRule ^submit/?$ "submit.php"
```

On the 4 public web servers I have access to, this code is interpreted correctly - being that if I visit [http://site/submit/bulk](http://site/submit/bulk), I get submit_bulk.php, and if I visit [http://site/submit](http://site/submit), I get submit.php

On my Ubuntu server, though, If I visit [http://localhost/submit/bulk](http://localhost/submit/bulk) I get submit.php instead of submit_bulk.php

It's as if mod_rewrite is ignoring the /submit/bulk rule, or overriding the /submit/bulk with /submit

Does mod_rewrite handle requests differently on Ubuntu? Is it more strict? I am new to mod_rewrite-- it's possible that my rules aren't completely correct and most servers forgive it, but Ubuntu doesn't seem to be

Any help would be greatly appreciated, thank you

---

### Post by BkkBonanza on 2011-04-07
I'm 99.9% sure that mod_rewrite works the same.

One thing is to make sure your browser isn't caching a previous test page. Clearing the cache or using Ctrl-F5 may help get consistent results.

---

### Post by t3r0 on 2011-04-08
Sounds like you have MultiViews enabled for that directory. Disable MultiViews and your rewrites should work as expected... 

- Tero

> **sjlsam said:**
> I installed Ubuntu with Apache/PHP as a development server

I followed the steps to enable mod_rewrite (a2enmode rewrite, AllowOverride settings,etc)

mod_rewrite is working, but it seems to be behaving differently from the other servers I work with

Consider the following .htaccess:

```
RewriteEngine on
RewriteRule ^submit/bulk/?$ "submit_bulk.php"
RewriteRule ^submit/?$ "submit.php"
```

On the 4 public web servers I have access to, this code is interpreted correctly - being that if I visit [http://site/submit/bulk](http://site/submit/bulk), I get submit_bulk.php, and if I visit [http://site/submit](http://site/submit), I get submit.php

On my Ubuntu server, though, If I visit [http://localhost/submit/bulk](http://localhost/submit/bulk) I get submit.php instead of submit_bulk.php

It's as if mod_rewrite is ignoring the /submit/bulk rule, or overriding the /submit/bulk with /submit

Does mod_rewrite handle requests differently on Ubuntu? Is it more strict? I am new to mod_rewrite-- it's possible that my rules aren't completely correct and most servers forgive it, but Ubuntu doesn't seem to be

Any help would be greatly appreciated, thank you

---

### Post by sjlsam on 2011-04-09
> **t3r0 said:**
> Sounds like you have MultiViews enabled for that directory. Disable MultiViews and your rewrites should work as expected... 

- Tero

You are right!

In my 000-default file I notice:

	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride all
		Order allow,deny
		allow from all
	</Directory>

Removing MultiViews seems to fix the problem

Do most hosting servers operate with MultiViews off?

In my distributable version I guess it would be wise to put Options -MultiViews in the .htaccess file in case a server doesn't

---


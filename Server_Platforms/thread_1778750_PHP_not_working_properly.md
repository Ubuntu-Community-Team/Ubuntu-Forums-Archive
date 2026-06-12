---
title: "PHP not working properly?"
date: 2011-06-09
forum: Server Platforms
---

### Post by OriginalAdric on 2011-06-09
I've been running into a problem with PHP on my site. My server is running the generic LAMP stack, and PHP doesn't seem to be working properly. phpinfo() works fine, as does PHPMyAdmin, but when I try to load the php home page I've been working on or the Wordpress blog I installed, it doesn't seem to parse. I'd guess for the home page that it was my code, except that it parses fine on an XAMPP stack that I use for local work.

To see what I mean, the phpinfo test page is located here [http://www.originaladric.com/test.php]("http://www.originaladric.com/test.php").
The PHPMyAdmin panel is located at [http://www.originaladric.com/phpmyadmin]("http://www.originaladric.com/phpmyadmin")
The php test home page is at [http://www.originaladric.com/php_index.php]("http://www.originaladric.com/php_index.php"). It's supposed to load a header, sidebar, and footer thru PHP, but it's obviously not.
And the Wordpress is at [http://www.originaladric.com/blog]("http://www.originaladric.com/blog")

I'm pretty new to running and configuring servers, so please let me know if I've left out any key information that would help diagnose my problem. I did try searching for solutions, but I couldn't find anything that worked.

---

### Post by tgalati4 on 2011-06-09
80% of PHP problems are not allocating enough memory for PHP instances.  Check /etc/php5/apache2/php.ini


tgalati4@hardy-back:/etc/php5/apache2$ grep mem php.ini
memory_limit = 96M      ; Maximum amount of memory a script may consume (16MB)
; If this parameter is set to Off, then memory leaks will not be shown (on
report_memleaks = On
; keeping them in memory.

---

### Post by OriginalAdric on 2011-06-09
> **tgalati4 said:**
> 80% of PHP problems are not allocating enough memory for PHP instances.  Check /etc/php5/apache2/php.ini


tgalati4@hardy-back:/etc/php5/apache2$ grep mem php.ini
memory_limit = 96M      ; Maximum amount of memory a script may consume (16MB)
; If this parameter is set to Off, then memory leaks will not be shown (on
report_memleaks = On
; keeping them in memory.

My php.ini defaults to memory_limit = 128M and report_memleaks = ON. Is that reasonable, or should I increase the limit?

---

### Post by OriginalAdric on 2011-06-09
After doing more testing, I'm even more unsure what the problem is. I tried embedding the phpinfo() function at the end of the page, and it parsed perfectly while still skipping my header, sidebar, and footer files. I'm wondering if it's how I have my includes structured.

The way I'm trying to set up the page, I have /var/www/php_index.php trying to load in /var/www/php_modules/FILE.html as modules of html. So, to load in the header, I have <?php include("/php_modules/header.html"); ?>. Again, the pages all work fine when I'm testing locally using XAMPP, but they fail to load on my webserver.

Am I going about this the wrong way?

---

### Post by wojox on 2011-06-09
Have you tried making it a .php extension and setting the absolute path:

```
<?php include($DOCUMENT_ROOT . "/php_modules/header.php"); ?> 
```

---

### Post by OriginalAdric on 2011-06-09
> **wojox said:**
> Have you tried making it a .php extension and setting the absolute path:

```
<?php include($DOCUMENT_ROOT . "/php_modules/header.php"); ?> 
```

I tried that, but it didn't work. However, my knowledge of PHP is absolutely bare minimum, so I may have not done that properly. When you said to set the absolute path, did you mean to literally just place "$DOCUMENT_ROOT . " in front of the path? If not, how do I set the absolute path?

---

### Post by satanselbow on 2011-06-09
> 
did you mean to literally just place "$DOCUMENT_ROOT . " in front of the path?


Yeah that's what is being said ;)

The path you have your php include - as it is at the moment - is looking in the wrong place for the file it is trying to include ;)

An alternate way of re-writing the code would be to drop the 1st *slash* in your path to the include file ie:

```

<?php include("php_modules/header.php"); ?>

```

---

### Post by OriginalAdric on 2011-06-09
> **satanselbow said:**
> Yeah that's what is being said ;)

The path you have your php include - as it is at the moment - is looking in the wrong place for the file it is trying to include ;)

An alternate way of re-writing the code would be to drop the 1st *slash* in your path to the include file ie:

```

<?php include("php_modules/header.php"); ?>

```

Ok. Dropping the front slash fixed it. Thank you guys for the help. Haha I spent so much time trying to uninstall/reinstall PHP thinking it wasn't running correctly.

---

### Post by tgalati4 on 2011-06-10
The other 20% is: "D'Oh!" :rolleyes:

---


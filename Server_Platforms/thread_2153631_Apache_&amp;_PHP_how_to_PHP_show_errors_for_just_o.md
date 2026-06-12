---
title: "Apache &amp; PHP: how to PHP show errors for just one domain?"
date: 2013-06-11
forum: Server Platforms
---

### Post by kevinx on 2013-06-11
Hello,


I'm running more websites at my Ubuntu 12.04 server. Most of them are php-based websites.

I have one testdomain at my ubuntu server where I test the php-scripts while I am creating the scripts/website. Unfortunatly the testdomain doesn't tell if I made some syntax errors.   

Is there a way to switch on the php error messages for this testdomain only?

Kevin

---

### Post by sandyd on 2013-06-11
If you are using php+fpm....

You can add php settings to /etc/php5/fpm/pool.d/*

There are a few examples at the end of how the php setting should be formatted

If you are using Apache, use the php_admin_value directive (e.x. php_admin_value upload_max_filesize 50M) to set php settings

---

### Post by SeijiSensei on 2013-06-11
First, I'd set the Apache [ErrorLog]("http://httpd.apache.org/docs/current/mod/core.html#errorlog") directive for the testdomain to a separate log file in /var/log/apache2 if you haven't done so already.  I usually just "tail" this file in a terminal window while debugging the website code.  However if you want to enable the display of error messages within the page, add these to the top of your index.php script:

```

error_reporting(E_ALL);
ini_set( 'display_errors','1'); 

```

All my PHP sites include an initialization script before any content is displayed, so I would put these commands in that.  Otherwise you need to put them at the top of index.php and any other .php pages.

In versions of PHP [starting with 5.2.4]("http://www.php.net/manual/en/errorfunc.configuration.php#ini.display-errors"), you would replace '1' with 'stdout' in the ini_set() function.

---

### Post by kevinx on 2013-07-13
Thanks all!

I prefere the [COLOR=#000000]idea SeijiSensei gave[/COLOR]. I working with it for a few weeks and it works fine for me. 

Thanks again!
Kevin

---


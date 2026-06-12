---
title: "Different php.ini for every domain"
date: 2009-06-07
forum: Server Platforms
---

### Post by wattaman on 2009-06-07
How can I use a different php.ini for every subdomain of my domain? I'm using different php scripts and I want to restrict some of them for security reasons. Therefore, all subdomains should have their own personalized php.ini file.
I've tried to just upload them in their public_html folder but it seems they're ignored and only the main php.ini file is used (etc/php5/apache2, if I remember well).
Thank you!

---

### Post by LepeKaname on 2009-06-07
Try this in .htaccess:

SetEnv PHPRC /mypath/dir-inifile

([http://www.php.net/manual/en/configuration.php#72212](http://www.php.net/manual/en/configuration.php#72212))

---

### Post by wattaman on 2009-06-08
OK, I'll try ASAP. Meanwhile, one stupid question: I've disabled in the main php.ini the function parse_ini_file, as instructed by someone (saiz it improves security somehow) - will this cause problems loading secondary php.ini files?
Thx!

---

### Post by LepeKaname on 2009-06-08
According to:
[http://www.php.net/manual/en/configuration.php#53246](http://www.php.net/manual/en/configuration.php#53246)

"SetEnv PHPRC" will only work if you are running PHP as cgi. 
But, [http://www.php.net/manual/en/configuration.php#72212](http://www.php.net/manual/en/configuration.php#72212) 
wrote an example of how to use it if you are running PHP as module.

I tried myself to check who was right. I couldn't make it work running PHP as module. What about you?

But not all are bad news, If you create a .htaccess and write for example this:

php_flag register_globals on
php_flag magic_quotes_gpc on
php_value upload_max_filesize 220M

(forget about "SetEnv PHPRC"). It will work. Only you have to specify at your httpd.conf "AllowOverride All" or "AllowOverride Options" (under <Directory>)

Note: php_flag is set "true/false" variables, for the rest, use php_value.

(taken from: [http://www.askapache.com/2007/php/custom-phpini-tips-and-tricks.html](http://www.askapache.com/2007/php/custom-phpini-tips-and-tricks.html))

> 
I've disabled in the main php.ini the function parse_ini_file, as instructed by someone

Yes, it may not be safe if you allow your users to set their own php.ini file (If you need it, there is a workaround: [http://bugs.php.net/bug.php?id=34949](http://bugs.php.net/bug.php?id=34949))

parse_ini_file must not affect your .htaccess variables.

If you really want to let your users to upload their own php.ini (instead of editing the .htaccess), then you could make a script to parse their php.ini and translate those values into their .htaccess. 

Hope it helps.

---


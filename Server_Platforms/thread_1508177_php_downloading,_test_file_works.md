---
title: "php downloading, test file works"
date: 2010-06-12
forum: Server Platforms
---

### Post by Carleas on 2010-06-12
Hi,
I'm running 8.04 server, and I'm having a problem getting php files to load properly.

After installing phpbb3, the installer script keeps trying to download instead of run.  I confirmed php5 is working by creating a test file that contains
[PHP] <?php phpinfo(); ?>[/PHP]
and that works fine.

Why would php work in the main /www directory, but not in sub-directories?

---

### Post by SlidingHorn on 2010-06-12
Try this out: [https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205](https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205)

---

### Post by Carleas on 2010-06-12
I tried that earlier.  I don't think it's the php5 configuration that's the problem, because the test file loads properly, indicating that php is working.  It's only files within /www/phpbb3/ that are downloading instead of displaying correctly.

---

### Post by SlidingHorn on 2010-06-12
hmm...that's odd.  Is there an .htaccess file in the subdirectory that's affecting the a2enmod?  if there's a file there, please post the contents of it in code tags

---

### Post by Carleas on 2010-06-12
I suspected .htaccess, but I didn't have any luck figuring it out:

```
#
# Uncomment the statement below if you want to make use of
# HTTP authentication and it does not already work.
# This could be required if you are for example using PHP via Apache CGI.
#
#<IfModule mod_rewrite.c>
#RewriteEngine on
#RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization},L]
#</IfModule>

<Files "config.php">
Order Allow,Deny
Deny from All
</Files>

<Files "common.php">
Order Allow,Deny
Deny from All
</Files>
```
Those "Deny from All"s look pretty sinister :lol:

---

### Post by Ryan Dwyer on 2010-06-12
I just installed it using sudo apt-get install phpbb3 and it's working fine. You don't need to run an installer script because that's handled automatically.

---

### Post by Carleas on 2010-06-13
Did you have to add any special repositories to do that?

---

### Post by Ryan Dwyer on 2010-06-13
It's in universe.

---

### Post by Carleas on 2010-06-13
I couldn't get it to install using apt-get, but I don't think that's the problem.  I have the package installed and unzipped on the server, but you need to run the installer using the browser to configure it.

I tried changing .htaccess to
```
AddType application/x-httpd-php .php .htm .html
AddHandler x-httpd-php .php .htm .html
```

and then to 
```
<FilesMatch "\.(htm|html|php)$">
SetHandler application/x-httpd-php
</FilesMatch> 
```

but neither solved the problem.

---

### Post by EdObie on 2010-06-13
My php was working fine about a week ago and now it does exactly as described above. The test file however works fine. I think I ran some updates last week which updated apache and also upgraded to ff 3.5.2. Still can't figure the out what the problem is.

---

### Post by Carleas on 2010-06-14
After reading of a similar problem in [this thread]("http://ubuntuforums.org/showthread.php?t=618525"), I tried Safari and the page loaded correctly (I was using SeaMonkey before).  

I don't think I have any settings that should block the script from loading, so this behavior seems weird.

---


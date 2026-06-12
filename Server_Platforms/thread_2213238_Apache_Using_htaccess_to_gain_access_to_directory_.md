---
title: "Apache: Using htaccess to gain access to directory outside of webroot"
date: 2014-03-25
forum: Server Platforms
---

### Post by vsiege2 on 2014-03-25
I'd like it if my php files were able to access a directory ouside of the webfoot. I believe this possible with .htaccess.

Webroot directory: 
[FONT=Courier]/var/www/vhosts/mydomain.com/subdomains/d-dev/d-a/www[/FONT]

Directory of files I'd likes to access: 
[COLOR=#4C2F2D][FONT=Courier]/var/www/vhosts/mydomain.com/admin/special

Please do not respond with security warnings, I'm aware of them, thank you.[/FONT][/COLOR]

---

### Post by volkswagner on 2014-03-25
Create a directory [alias]("http://httpd.apache.org/docs/2.2/mod/mod_alias.html")
Then adjust permissions for apache to be able to read or write as you prefer.

---

### Post by Lars Noodén on 2014-03-25
Also, there is no need to mess with .htaccess if you yourself have access to the web server's real configuration file.  Easier to keep things there, all in one place.

---

### Post by vsiege2 on 2014-03-25
I don't have access to the apache conf or any of the hosts conf, so the .htaccess is my only option. 

I am trying to access the shell files via the php command [B]shell_exec
[/B]
Will this work using the *Alias* method above?

---

### Post by SeijiSensei on 2014-03-26
You may find that shell_exec() is disabled if you are on a hosted service.  I know I wouldn't give random users the ability to run programs at the shell prompt.

I keep all of my PHP code outside the webroot.  I use require() and include() to access those files.  My index.php file usually looks something like this:
```

<?php
$incdir="/home/seiji/mysite/include/";
$common   = $incdir."common/";
$handlers = $incdir."public/handlers/";
$content  = $incdir."public/content/";

require($common."init.inc");
include($content."index.inc");

?>

```
"Handlers" contains files that are run before the page is displayed, often for forms processing.  "Content" contains the actual HTML code with an occasional sprinkling of PHP as required.  I use the ".inc" suffix (for "include") for these files rather than .php so I can have a rule in Apache that prohibits downloads of files with that extension.

---

### Post by vsiege2 on 2014-04-07
**Thanks for your response using include and require**. The file I want to run is a shell script and not a html, php or js file. It can only be a shell script. 
I don't think your solution would work since I am not trying to incorporate it into the site at all. Again, the security part is not of issue since I have that covered. I have a full root access to the server as well. Is there another solution?

---

### Post by SeijiSensei on 2014-04-08
It sounds like you want to run a shell script in the background, presumably in response to user input?  What if you just give shell_exec() the complete path to the script you want to run?

```
shell_exec("/var/www/vhosts/mydomain.com/admin/special/some_script");
```

Remember that the "www-data" pseudo-user that owns the Apache process must have read and execute privileges on all the directories in that chain and on the script itself.

---


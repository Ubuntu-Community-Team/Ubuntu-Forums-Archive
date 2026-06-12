---
title: "[SOLVED] Server redirection"
date: 2008-05-23
forum: Server Platforms
---

### Post by stringkarma on 2008-05-23
Hi all,
I consider myself halfway into my linux experiment. I have been using it at home for over a year now. I finally got my chance to try it as a server, for a small group forum.

The first time I set it up, in my apache settings somewhere I set it so that when you visit my.page.com what you get immediately is my.page.com/phpBB3/. At the time I did it it seemed so easy that I neglected to remember how I did it, but it involved only changing one line in the default settings.

Now I have done some tinkering, wrecked and reloaded the system, restored the content from a backup, but now I can't figure out how to get my redirect back. All of the help I have found, when tried, gives me my same "it works" site and when I navigate directly to /phpBB3/ gives me an error 404!

So I guess getting good at linux at home does you little good for server administration.
Help a poor struggling re-noob!

P.S. If it matters, the first time I followed the community doc [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) to set up the server. But this second time I just let the TASKSEL do it during Ubuntu installation.

---

### Post by SuperCzar on 2008-05-23
Try putting this in an .htaccess file in the DocumentRoot folder.

```

RewriteEngine on
RewriteRule   ^my.page.com  my.page.com/phpbb3/  [R,L]

```

---

### Post by stringkarma on 2008-05-27
Thanks for the idea, unfortunately, it did not change the behaviour of the site.
Again, it seems that before one of the config files that already existed the first time seemed to have a fairly self evident page redirection command that I used.

Any other thoughts?
Thanks again

---

### Post by stringkarma on 2008-05-27
You know, it comes to me that I have been looking for one answer when another will do. Rather than having apache do the work, I changed the default "it works" page into an html redirect. This seems to work for what I need.
If someone else knows a more elegant solution, or if this is somehow unwise let me know. Thanks.

---

### Post by windependence on 2008-05-27
> **SuperCzar said:**
> Try putting this in an .htaccess file in the DocumentRoot folder.

```

RewriteEngine on
RewriteRule   ^my.page.com  my.page.com/phpbb3/  [R,L]

```

Did you restart Apache after changing the config file?


Here is what I did for my forum. I created a php redirect and pu it in a file like called index.php in my server root directory:

[PHP]<?php 
  header("location:http://dominicanstotheusa.com/forum/"); 
?> 
[/PHP]

That did the trick.


-Tim

---

### Post by stringkarma on 2008-06-01
Thanks, thats much more modern. I really need to take the time to learn php. That is once I learn all there is to know about servers ;-)

---

### Post by windependence on 2008-06-01
> **stringkarma said:**
> Thanks, thats much more modern. I really need to take the time to learn php. That is once I learn all there is to know about servers ;-)

You are quite welcome. I don't know much PHP, but I had seen this done before and it's fast and clean. 

-Tim

---


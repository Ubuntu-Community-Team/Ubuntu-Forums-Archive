---
title: "php files gets downloaded"
date: 2009-03-28
forum: Server Platforms
---

### Post by caymahallesi on 2009-03-28
Hi guys, 

I got this problem again and I don't remember What I did to fix it. 
Could you please remind me again, how to fix this problem.

When I browse my website [http://localhost](http://localhost) browser tries to download or save the file instead of running the script. 

I installed LAMP stack from tasksel after a restart I saw that apache "It works" shows. But PHP files won't.

**Additional to my problem, when I direct browse to a index.html page on my server it works shows up fine. But when I direct browse to the index.php file browser tries to download it.**

Please help.

---

### Post by m3bik on 2009-03-28
Do you have PHP installed and working properly? If so, it might be a setting in apache that is off.. I know you can do it for a website by adding a .htaccess file to the site directory with something like this:

```

AddType application/x-httpd-php5 .php
AddHandler php5-script .php

```

I'm sure this can also be done in one of apache's config files... Not sure which one at the moment, and don't have time to look it up, but I hope this helps?

---

### Post by hyper_ch on 2009-03-29
better run
```

sudo a2enmod php5

```

than manually adding that stuff and restart apache afterwards.

---


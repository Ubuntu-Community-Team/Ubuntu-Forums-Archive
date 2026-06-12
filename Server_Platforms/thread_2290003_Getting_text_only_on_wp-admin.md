---
title: "Getting text only on /wp-admin"
date: 2015-08-08
forum: Server Platforms
---

### Post by Gotlieb on 2015-08-08
Hi,

I am getting the following error, something that has to do with the .htaccess I think.

[ATTACH=CONFIG]263723[/ATTACH]

Thanks in advance

---

### Post by cj13579 on 2015-08-09
Can you share your .htaccess?

---

### Post by Gotlieb on 2015-08-09
Hi

Thanks for replying.

[ATTACH=CONFIG]263745[/ATTACH]

---

### Post by cj13579 on 2015-08-09
Do you have a regular LAMP installation? If so then you shouldn't need the handler lines in that file.
For the memory increase, try the following

```

<IfModule mod_php5.c>
php_value memory_limit 64M
</IfModule>

```

That should work but if it doesn't then you may need to edit the /etc/php5/php.ini file directly.

---

### Post by Gotlieb on 2015-08-09
Like this?

[ATTACH=CONFIG]263746[/ATTACH]

---

### Post by cj13579 on 2015-08-09
Yep, but try getting rid of the AddType and AddHandler directives. You shouldn't need them in a LAMP installation.

---

### Post by Gotlieb on 2015-08-09
Hi

I am getting an eternal error after getting rid of that. :(

---

### Post by Gotlieb on 2015-08-09
Fixed. I could kiss you right now, thank you so much!

---


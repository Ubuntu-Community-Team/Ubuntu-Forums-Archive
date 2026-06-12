---
title: "need some help on redirecting squirrelmail"
date: 2010-09-08
forum: Server Platforms
---

### Post by kustomjs on 2010-09-08
Hey Guys
I am just wondering if anybody tell me how to redirect mail.domain.com/squirrelmail/src/login.php just back to mail.domain.com.

I used this guide:[https://help.ubuntu.com/community/Squirrelmail](https://help.ubuntu.com/community/Squirrelmail)

---

### Post by Demented ZA on 2010-09-08
If you need to access "mail.domain.com/squirrelmail/src/login.php" to get to squirrelmail, I assume you installed Squirrelmail into a subdirectory of your web server (probably /var/www/squirrelmail).

You can't _**"rewrite"**_ mail.domain.com/squirrelmail/src/login.php to mail.domain.com without making squirrelmail inaccesable.

There are other ways though:

You could move squirrelmail. If squirrelmail is the only web content on your web server.

If you don't want to move squirrel or if you have other content, and if you already have an index.html or index.php, you can modify that to include a link to your squirrelmail login.

I suppose you could also use apache's .htaccess file with the mod rewrite function.

Maybe a little more insight on exactly what you are trying to accomplish could help ;)

---

### Post by kustomjs on 2010-09-08
I want to move squirrelmail period so how would I do that.

---

### Post by kustomjs on 2010-09-08
anybody?

---

### Post by Vishal Agarwal on 2010-09-09
you can edit the 'mail.domain.com/squirrelmail/src/login.php' but in such case no body will be able to login to squrriel mail !

If so then edit the login.php and add the following lines to it.

> 
[COLOR=#000000]<html>
[COLOR=#0000bb]<?php
[/COLOR][COLOR=#ff8000]/* This will give an error. Note the output
 * above, which is before the header() call */
[/COLOR][COLOR=#0000bb]header[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]'Location: [http://www.example.com/](http://www.example.com/)'[/COLOR][COLOR=#007700]);
[/COLOR][COLOR=#0000bb]?>
[/COLOR][/COLOR]

This should be the very first lines of the login.php file. 
Before any editing create a backup copy of file for secure editing.

;)

---

### Post by kustomjs on 2010-09-09
well I just want the link from: /squirrelmail/src/login.php to be removed.

---


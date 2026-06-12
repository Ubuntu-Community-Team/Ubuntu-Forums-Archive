---
title: "PHP Write Permissions - Ubuntu Server"
date: 2010-08-23
forum: Server Platforms
---

### Post by matt531320 on 2010-08-23
When installing a little handy thing called Elgg ([http://www.elgg.org/]("http://elgg.org")) I get an error saying: ```
Elgg requires a file called .htaccess to be set in the root directory of its installation. We tried to create it for you, but Elgg doesn't have permission to write to that directory.
```
and
```
We were unable to save the new settings.php
```
Is there a way to fix this? I can install it manually, that's not the issue, but I would like to know how to fix this for future reference (It worked fine in WAMP for me). I changed the folder /var/www to read/write/execute for all users, but it still doesn't work (I thought that might have something to do with it). Your help is greatly appreciated. Thanks.

---

### Post by utnubuuser on 2010-08-24
Are the rwx permissions set recursively, ie sudo chmod **-R** 777 /var/www

Because the message is saying that r+w permission is needed in Elgg's directory, not the server's.

---

### Post by matt531320 on 2010-08-24
That did the trick! Thanks soooo much ;)

---


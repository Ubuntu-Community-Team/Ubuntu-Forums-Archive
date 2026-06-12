---
title: "phpBB issue"
date: 2011-12-10
forum: Server Platforms
---

### Post by DarkSnake-Kobra on 2011-12-10
I'm currently having an issue with phpBB not loading after doing a reinstall of the server. I was told to post to a more appropriate forum as it was out of the scope of their forum.

[http://www.phpbb.com/community/viewtopic.php?f=46&t=2145723#p13084897](http://www.phpbb.com/community/viewtopic.php?f=46&t=2145723#p13084897)

The main problem is that I'm getting a server 500 error(with SRWare Iron while Firefox just shows a blank page) and was told the database seemed fine. This on a Ubuntu 11.10 x32 Server on a Dell Dimension 2400 with the following specs

PHP 5.3.6
phpmyadmin 3.4.5
MySQL 5.1
Apache 2.2.20
1256MB Ram(1GB and 256MB modules)

This is the link to the forum. [http://www.cyberstealthlabs.org/forum](http://www.cyberstealthlabs.org/forum)

---

### Post by lisati on 2011-12-10
This looks more like a server issue than a phpBB issue to me.

My thoughts would be to backup your database (as your thread in in the phpBB forum suggests), completely purge your phpBB installation, reinstall phpBB, and restore your database.

---

### Post by DarkSnake-Kobra on 2011-12-10
Thanks for the reply. That is one thing I missed. I will try that quick and post back the results. :)

---

### Post by DarkSnake-Kobra on 2011-12-10
Awesome it's working. Thank you very much. :) I imported the old database then moved the phpBB created backup to the store folder then I was able to restore it. :)

---

### Post by lisati on 2011-12-10
> **DarkSnake-Kobra said:**
> Awesome it's working. Thank you very much. :) I imported the old database then moved the phpBB created backup to the store folder then I was able to restore it. :)

It's good to hear that you're making progress.

---


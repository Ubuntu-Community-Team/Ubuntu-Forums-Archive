---
title: "weird apache2+php5 behaviour"
date: 2008-06-23
forum: Server Platforms
---

### Post by kenlo on 2008-06-23
Ubuntu 8.04, Apache2 2.2.8-1ubuntu0, php5 5.2.4-2ubuntu5.

Create a <?php phpinfo(); ?> file called test.php at the document root.  Point to [http://yourserver/test.php](http://yourserver/test.php) it will be a phpinfo page.

Now point to [http://yourserver/wrong.php](http://yourserver/wrong.php) you'll get a 404 not found.

Now point to [http://yourserver/test/name.php](http://yourserver/test/name.php) you'll get phpinfo.  Replace "name" with anything it will just work.

Copy test.php to wrong.php.  Guess what.  [http://yourserver/wrong/anything.php](http://yourserver/wrong/anything.php) will just work.

---


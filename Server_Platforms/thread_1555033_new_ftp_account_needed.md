---
title: "new ftp account needed?"
date: 2010-08-17
forum: Server Platforms
---

### Post by bottomsforever on 2010-08-17
Hi all - I've attempted to install FMyScript on [www.cupidstunts.com]("http://www.cupidstunts.com") but so far I just get a blank page. I've raised a ticket with Scriptolution, the makers of FMyScript and they've said they need my FTP details and phpmyadmin details to investigate the error.

I'm a bit wary of giving them these as I use my normal SSH login for FTP and it's a sudo account.

How should I play it? I guess I'd like to create an FTP account that lets them do what they need to do without opening up my system to issues. I thought about chmoding the FMyScript directory to 777 and then giving them a basic FTP account with no access privileges, would this work? And what about phpmyadmin?

Any help would be very much appreciated. Alternatively if anyone knows anything about FMyScript and can see why it's messing up that would also be appreciated :)

---

### Post by cdenley on 2010-08-17
I noticed before that in ubuntu 10.04, apache doesn't seem to print PHP errors in HTTP responses by default. I'm sure this is for security, since error messages can sometimes reveal too much. You should see what error is causing your script to fail by checking apache's error log (by default /var/log/apache2/error.log). Nobody can tell you anything about your site when all they see is a blank page. That is sort of the point.

[http://www.php.net/manual/en/errorfunc.configuration.php#ini.display-errors](http://www.php.net/manual/en/errorfunc.configuration.php#ini.display-errors)
```

grep -A 3 'display_errors' /etc/php5/apache2/php.ini

```

---

### Post by bottomsforever on 2010-08-18
Hi cdenley-
Many thanks for your quick and useful reply. I checked these error logs and realised I had an illegal character in my password. I have now fixed this and the site loads perfectly.
Best wishes to you,
Jamie

---


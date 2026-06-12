---
title: "Apache and Chroot"
date: 2009-09-30
forum: Server Platforms
---

### Post by shoaibi on 2009-09-30
I followed [http://www.howtoforge.com/chrooting-apache2-mod-chroot-debian-etch](http://www.howtoforge.com/chrooting-apache2-mod-chroot-debian-etch)
and when i restart apache at the end of tutorial i get:

```

[Wed Sep 30 10:55:07 2009] [notice] FastCGI: process manager initialized (pid 26842)
[Wed Sep 30 10:55:08 2009] [notice] mod_chroot: changed root to /var/www.
[Wed Sep 30 10:55:08 2009] [alert] (2)No such file or directory: Can't chdir to /var/www
[Wed Sep 30 10:55:08 2009] [alert] (2)No such file or directory: Can't chdir to /var/www
[Wed Sep 30 10:55:08 2009] [alert] (2)No such file or directory: Can't chdir to /var/www
[Wed Sep 30 10:55:08 2009] [alert] (2)No such file or directory: Can't chdir to /var/www
[Wed Sep 30 10:55:08 2009] [alert] (2)No such file or directory: Can't chdir to /var/www
[Wed Sep 30 10:55:08 2009] [notice] Apache/2.2.11 (Ubuntu) DAV/2 SVN/1.5.4 mod_fastcgi/2.4.6 Phusion_Passenger/2.2.4 mod_ssl/2.2.11 OpenSSL/0.9.8g mod_chroot/0.5 mod_perl/2.0.4 Perl/v5.10.0 configured -- resuming normal operations
[Wed Sep 30 10:55:08 2009] [alert] Child 26859 returned a Fatal error... Apache is exiting!
[Wed Sep 30 10:55:08 2009] [alert] (2)No such file or directory: FastCGI: read() from pipe failed (0)
[Wed Sep 30 10:55:08 2009] [alert] (2)No such file or directory: FastCGI: the PM is shutting down, Apache seems to have disappeared - bye

```

Another thing, some deployments/vhosts like redmine.mydomain.com aren't inside /var/www but in /var/redmine, same ghost for phpmyadmin, do i have to create directories and symlink for those as well?

I also use eaccelerator for php applications which uses files in /tmp/eaccelerator. And apache's default logs are inside /var/log. These symlinks are also needed?

Plus: Could anyone tell me how can i run each web application in its own vm?

---

### Post by Bachstelze on 2009-09-30
Since you chrooted to /var/www, the /var/www directory for Apache will be /var/www/var/www. You can either create the dir and move your files there, or change your DocumentRoot to / in the Apache config.

---

### Post by shoaibi on 2009-09-30
i have:
```

root@blade:/var/www# ls -al var/
total 12
drwxr-sr-x  3 www-data www-data 4096 2009-09-30 11:04 .
drwxrwsr-x 10 www-data www-data 4096 2009-09-30 11:04 ..
lrwxrwxrwx  1 root     www-data    9 2009-09-30 11:04 git -> /var/git/
lrwxrwxrwx  1 root     www-data   13 2009-09-30 11:04 redmine -> /var/redmine/
                                                                            drwxr-sr-x  2 www-data www-data 4096 2009-09-30 10:55 run
lrwxrwxrwx  1 root     www-data    9 2009-09-30 11:01 www -> /var/www/

```

Latest Error is:
```

[alert] (40)Too many levels of symbolic links: Can't chdir to /var/www

```

---

### Post by Bachstelze on 2009-09-30
> **shoaibi said:**
> i have:
```

root@blade:/var/www# ls -al var/
total 12
drwxr-sr-x  3 www-data www-data 4096 2009-09-30 11:04 .
drwxrwsr-x 10 www-data www-data 4096 2009-09-30 11:04 ..
lrwxrwxrwx  1 root     www-data    9 2009-09-30 11:04 git -> /var/git/
lrwxrwxrwx  1 root     www-data   13 2009-09-30 11:04 redmine -> /var/redmine/
                                                                            drwxr-sr-x  2 www-data www-data 4096 2009-09-30 10:55 run
lrwxrwxrwx  1 root     www-data    9 2009-09-30 11:01 www -> /var/www/

```

Latest Error is:
```

[alert] (40)Too many levels of symbolic links: Can't chdir to /var/www

```

You have to do one of the two things I told you. Why ask for help if you won't listen to what you're told?

---

### Post by shoaibi on 2009-09-30
Dear, what you are saying isn't possible, i can't change all vhosts config, instead i create a directory named var inside /var/www/ and used symlinks as told on the tutotial link in my earlier post.

---

### Post by Bachstelze on 2009-09-30
> **shoaibi said:**
> Dear, what you are saying isn't possible, i can't change all vhosts config, instead i create a directory named var inside /var/www/ and used symlinks as told on the tutotial link in my earlier post.

You can't do that, as the error demonstrates.

---

### Post by shoaibi on 2009-09-30
strange, then why is the tutorial suggesting it, and its now another site, its one of really good sites :'(

---

### Post by Bachstelze on 2009-09-30
What you can do is

```
sudo mount -o bind /var/www /var/www/var/www
```

It will mostly have te same effect you seem to think a symlink would have, except that it works.

---

### Post by shoaibi on 2009-09-30
Now i get:
```

[Wed Sep 30 17:40:14 2009] [error] [client 119.153.56.166] File does not exist: /var/www/own-sites 

```

With mount | grep www
```

/var/www on /var/www/var/www type none (rw,bind)

```

and 
```

# ls /var/www/
apache2-default  etc  index.html  own-sites  projects  test-projects  usr  var
# ls /var/www/var/www/
apache2-default  etc  index.html  own-sites  projects  test-projects  usr  var

```

---


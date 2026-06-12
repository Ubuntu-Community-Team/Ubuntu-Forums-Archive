---
title: "LAMP reinstall"
date: 2008-12-29
forum: Server Platforms
---

### Post by quikone8 on 2008-12-29
I have installed LAMP and wonder if it would be advantages to start over.  My ultimate goal is to get Wordpress up and running but it seems as if I have got it so screwed up that I can't get to it.  I am also having trouble remotely accessing phpmyadmin remotely.  I noticed that I have Wordpress in three areas;

/etc/wordpress
/usr/share/wordpress
/var/www/blog/wordpress

This is what I get when I try to browse to the ip

404 Not found

Error establishing a database connection

This either means that the username and password information in your wp-config.php file is incorrect or we can't contact the database server at localhost. This could mean your host's database server is down.

    * Are you sure you have the correct username and password?
    * Are you sure that you have typed the correct hostname?
    * Are you sure that the database server is running?

If you're unsure what these terms mean you should probably contact your host. If you still need help you can always visit the WordPress Support Forums.

Is this recoverable or should I just reinstall?  If reinstall, how?

---

### Post by cariboo on 2008-12-29
Just doing a reinstall won't solve the problem, as would have to completely remove all the applications as well as their configuration files

The way I got wordpress to work the last time I played with it was to create a symlink in /var/www, something like this:

```
sudo ln -s /usr/share/wordpress wordpress
```

This will  create a link in /var/www called wordpress, then to access the directory in the firefox address bar type: 

```
http://localhost/wordpress
```

This should get you to the setup page where you can setup your database connection.

Jim

---


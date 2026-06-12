---
title: "HOW TO:  Get Apache To READ The PHP Files"
date: 2010-06-10
forum: Server Platforms
---

### Post by kevin11951 on 2010-06-10
[CENTER]
[SIZE="4"]Get Apache To READ The PHP Files
[/SIZE][/CENTER]

Ok, so I have noticed that on a default install of Debian/Ubuntu, the LAMP stack always wants to force you to DOWNLOAD the PHP file, instead of execute it.  This is bad. (well, good for security, bad for us ;))

Also, once a week at least, I see beginners facing this problem.

So I made this little "HOW TO" for beginners to make it so that apache will actually **execute** their PHP files.

Note:  I am not a security expert, commands in this "how to" are subject to security issues.  Only use them to get a server running, then edit apache for security.

First and foremost, we need to fix permissions of /var/www

While in a terminal on the server (eg. SSH):
```

chown -R www-data:www-data /var/www
chmod -R 0755 /var/www

```

Then we also need to make it so that apache isnt so paranoid about its php scripts (SECURITY ALERT!)

Replace the contents of "/etc/apache2/sites-available/default" with the following (Note: REPLACE the contents of the file, not append!):
```

<VirtualHost *:80>
	DocumentRoot /var/www/

</VirtualHost>

```

Now, lets restart apache, and apply the new settings:
```

apache2ctl restart

```

Thats it!  Now, just clear you browsers cache, and reconnect to the server's site.

PS.  Can we make this a sticky, so I can others can point to it?

---

### Post by lisati on 2010-06-10
Try clearing your browser cache. If that doesn't help, try the tips here: [https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205](https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205)

---

### Post by kevin11951 on 2010-06-10
> **lisati said:**
> Try clearing your browser cache. If that doesn't help, try the tips here: [https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205](https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205)

Well, I am not having the problem, other users are, that's why I made this "how to"...

---

### Post by cb951303 on 2010-06-15
does this work with UserDir?

---


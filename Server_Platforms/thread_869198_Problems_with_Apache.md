---
title: "Problems with Apache"
date: 2008-07-24
forum: Server Platforms
---

### Post by seuzy13 on 2008-07-24
I am having some problems getting Apache 2 to work correctly. The document root is currently /var/www and all files that are in this directory run correctly in the browser, including php, etc. 

Now, I have a subdirectory called html with some website design files in it. When I type [http://localhost/html](http://localhost/html) into the address bar, I get /var/www/html/index.php all looking correctly as would be expected, but none of the links that link to files in the same folder work. Also if I type [http://localhost/html/index.php](http://localhost/html/index.php) into the address bar, my browser just sits there with the loading icon spinning and never comes up with anything. This applies to all files in subdirectories under /var/www.

Any ideas? Thanks.

---

### Post by mbeach on 2008-07-24
which user owns the html folder?
```

cd /var/www
ls -lad html

```

Does it look like: 
drwxr-xr-x 2 root root 4096 2008-07-24 22:23 html

or
drwxr-xr-x 2 www-data www-data 4096 2008-07-24 22:23 html

---

### Post by seuzy13 on 2008-07-25
drwxr-xr-x 6 root root 4096 2008-07-21 16:06 html

---

### Post by seuzy13 on 2008-08-04
What do I do to fix this?

---

### Post by mbeach on 2008-08-04
sorry for the delay
```

sudo chown -R www-data:www-data /var/www/html

```
which will change the ownership of all the files in /var/www/html to www-data (the user Apache runs as).  Give that a whirl and see what happens.

Good luck
mb.

---

### Post by seuzy13 on 2008-08-04
Okay, it is working now. Thank you. :)

---

### Post by seuzy13 on 2008-11-27
Well, this method had been working, but as of late, I ran into the problem again. What should I do?

---


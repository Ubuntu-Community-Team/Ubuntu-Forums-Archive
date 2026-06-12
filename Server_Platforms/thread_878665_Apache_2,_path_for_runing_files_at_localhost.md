---
title: "Apache 2, path for runing files at localhost?"
date: 2008-08-03
forum: Server Platforms
---

### Post by masoud23 on 2008-08-03
Hi

When i am runing apache2 at localhost, where do i put my php or html files to be able to run them? where can i sett the path for my files?

tanks in advance

---

### Post by windependence on 2008-08-03
In your Apache configuration files, you can set the document root to whatever you want. The default should be /var/www, but you don't have to put it in your files. 

On the local network, you can just enter the IP address of your server or you can use [http://localhost](http://localhost). 

If you want to access the server by name, you will have to put an entry in your /etc/hosts file to let the machine know how to resolve the name.

-Tim

---

### Post by masoud23 on 2008-08-03
I can find localhost, it works, but wher do i put my php files? which catalog?

---

### Post by arkopII on 2008-08-03
Your files should be in /var/www which is the default configuration as windependence said. Then you can use DocumentRoot to change that default path.

---

### Post by windependence on 2008-08-03
If he uses /var/www, he just needs to put his php and html files in that directory. DocumentRoot does not have to be changed.

-Tim

---

### Post by masoud23 on 2008-08-03
tanks!

---

### Post by mknarr on 2010-04-24
Hello masoud23,

If I'm not mistaken the file you are looking for is

/etc/apache2/apache2.conf  

Or at least it is in /etc/apache2/_______

Also remember if you change any of the root directories you need to give the new root folders the proper privileges ( read/write/execute...and so on)

If you like GUI's look up a program called "webmin" it allows you to edit your apache2/ftp/php/sql... settings through a web interface. 

Hope this helps. :D

---

### Post by cdenley on 2010-04-24
> **Traveling-coder said:**
> I still don't feel that the question was answered though.  So now it's clear that you can set the location, but where do you go to do that and what steps must you take to accomplish it?

Let me know please.  Thanks!

You're asking how to copy files?
```

sudo cp /path/to/src/index.php /var/www

```

Make sure the user www-data can read them
```

sudo chmod a+r /var/www/index.php

```

If you want to change DocumentRoot, edit /etc/apache2/sites-available/default, then reload apache
```

sudo /etc/init.d/apache2 reload

```

---

### Post by doepain on 2010-04-26
I am think the issue that I am having can be addressed in this thread.

I am having issues with my Apache2 site executing some PHP, and the support for the product advised me to place the path for PHP on the $PATH for Apache user.

Now I know its not literally for the www-data user, and I scoured the apache.conf file for any mention of PHP and I have not seen anything.  To be honest I am not a 100% sure where apt-get dropped the PHP5 installation either.

Any advice?

---

### Post by cdenley on 2010-04-26
> **doepain said:**
> I am think the issue that I am having can be addressed in this thread.

I am having issues with my Apache2 site executing some PHP, and the support for the product advised me to place the path for PHP on the $PATH for Apache user.

Now I know its not literally for the www-data user, and I scoured the apache.conf file for any mention of PHP and I have not seen anything.  To be honest I am not a 100% sure where apt-get dropped the PHP5 installation either.

Any advice?

That doesn't seem to have anything to do with this thread. Also, there is no installation path for where apt-get installs php5. It installs different components in different directories. I suggest you create a new thread, and include the advice from the product support you mentioned word-for-word or provide a link.

---


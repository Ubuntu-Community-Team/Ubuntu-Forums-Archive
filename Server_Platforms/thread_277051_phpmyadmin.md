---
title: "phpmyadmin"
date: 2006-10-13
forum: Server Platforms
---

### Post by lugos on 2006-10-13
Hello,

I just installed phpmyadmin on my Ubuntu Server 6.06, but when I typed [http://127.0.0.1/phpmyadmin](http://127.0.0.1/phpmyadmin) I get a 404 not found.  Is there something else I need to do?

Thanks in advance for the help,
lugos

BTW, I do see the phpmyadmin directory in /var/www

---

### Post by plewisfdx on 2006-10-13
In the document root (in your case /var/www hopefully) check to see whats in that phpmyadmin directory.

Mine is a symlink to /usr/share/phpmyadmin which works for me.

---

### Post by lugos on 2006-10-14
Is there any configuration that I need to do?  Or should it work right after install?

It looks like my phpmyadmin directory is also a symlink to /usr/share/phpmyadmin.

---

### Post by lugos on 2006-10-14
OK, I think I figured out what's wrong.  I am hosting a website off of my server.  127.0.0.1 is not /var/www, it is actually /var/www/my_website_directory.  I somehow configured 127.0.0.1 to point to the same directory as my website.  Is there a way I can change it so that the root for localhost is /var/www again?  I must have done it when I was messing around with the virtual hosts configuration.

---

### Post by lugos on 2006-10-14
If I can't change where 127.0.0.1 points to without changing where my website points to, is there a way I can block access to phpmyadmin?  Because if 127.0.0.1 points to the same directory my website is at, then that means anyone can access phpmyadmin from the internet (that's assuming I move phpmyadmin directory to reside under the root for my website).  All they have to do is type in [www.mywebsite.com/phpmyadmin](www.mywebsite.com/phpmyadmin), is that correct?

---

### Post by lugos on 2006-10-14
OK, I've figured it out.  After sitting here and thinking about it (I'm a little slow, sometimes it takes me a while), I decided to change the default virtual host back to its default configuration and create a new virtual host for my website.  It worked!  Now I can access phpmyadmin using [http://127.0.0.1/phpmyadmin](http://127.0.0.1/phpmyadmin), and my site is still accessible from the Internet.

Some may think I'm wasting my time posting when nobody is responding but me.  However, posting sometimes gets me into think mode and actually helps a great deal, even when not many people respond.  And hopefully this will help somebody in the future.

Thanks Ubuntu Forums!

---

### Post by kafkaian on 2006-10-19
> **lugos said:**
> Some may think I'm wasting my time posting when nobody is responding but me.  However, posting sometimes gets me into think mode and actually helps a great deal, even when not many people respond.

Good on you lugos - good positive attitude :KS

---


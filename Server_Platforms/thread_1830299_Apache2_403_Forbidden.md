---
title: "Apache2 403 Forbidden"
date: 2011-08-21
forum: Server Platforms
---

### Post by ReneW on 2011-08-21
I have just installed ubuntu 11.04, and after some prodding about i have the system running as i want it, so want to add my www to it aswell.

I found on the website for Gallery3, what i want to use the www for, this post [http://gallery.menalto.com/node/99832](http://gallery.menalto.com/node/99832).

I ran that line to install apache and all other concerning and when connecting to localhost in the web browser i can see the it works message.

Now the problem starts with me wanting to change the /var/www to /home/site/www.
When i do this i keep getting forbidden. I have added the path into the httpd.conf, the default and used varaity of options seen about the options indexes etc.
Furthermore i have tried with chown to set the site to root, www-data and my own account, but none worked.

Could anyone plese help me to fix this.
Thank you!

---

### Post by elliotbeken on 2011-08-21
i used to move the apache 2 directory to my home dir but you dont need to you can just create a symbolic link to the var/www

Ln -s /path/to/real/file  /path/to/location/of/link

---

### Post by ReneW on 2011-08-21
I tried this...

renamed the www to [www.bak](www.bak)
ln -s /home/site/www /var/www
reloaded the browser and now i get 403 forbidden aswell

---

### Post by wojox on 2011-08-21
> **ReneW said:**
> I tried this...

renamed the www to [www.bak](www.bak)
ln -s /home/site/www /var/www
reloaded the browser and now i get 403 forbidden aswell

Here's how I do it [sudo a2enmod userdir]("http://ubuntuforums.org/showpost.php?p=11076015&postcount=5")

---

### Post by ReneW on 2011-08-21
> **wojox said:**
> Here's how I do it [sudo a2enmod userdir]("http://ubuntuforums.org/showpost.php?p=11076015&postcount=5")

I get the same results still... the /www/var still works, the /home doesnt

is there maybe some kind of user or group stuff i have to fix / add or whatever in this new 11.04 version?

---

### Post by Sanados on 2011-08-22
my guess would be that the webserver has no rights to access those files.
Can you list the file rights in your home directory?

The files should be readable by group apache2.

---

### Post by ReneW on 2011-08-22
yep it was the rights, apparently the whole HOME was set to my own, instead of root.

I changed this and it worked straight away.

Happily going on fixing my www now.

Thank you for your help and thinking with me.

---


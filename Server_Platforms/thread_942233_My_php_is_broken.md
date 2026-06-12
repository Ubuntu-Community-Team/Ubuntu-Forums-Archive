---
title: "My php is broken"
date: 2008-10-09
forum: Server Platforms
---

### Post by icantfindausername on 2008-10-09
Ok, well this is something I've never experienced before. I've had a lamp setup running gutsy studio and it worked fine before and after I installed ispconfig.  Anyway, I got my ftp working so I decided I would try and see if php would work.  

So I made a file: phptest.php which contains only the opening and closing tags.


<?php
?>

This is what is shows in the browser when I test the file.

[COLOR="Red"][B]
Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/var/www/phptest.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0[/B][/COLOR]



Any advice?  I searched for the error but everything related was for mysql.

---

### Post by TomB19 on 2008-10-09
Are you sure the owner/permissions are correct for the file?

---

### Post by icantfindausername on 2008-10-14
your right, I did chmod -R 777 /var/www/   and it worked.


Now how do I prevent this from happening again?  This is what is happening, I create the php file in Dreamweaver on a windows box, upload it by ftp to my /var/www/ folder and it doesn't have permission to run what it needs to run. I have to manually do the chmod -R 777 each time I add a new file then it works.

---

### Post by altonbr on 2008-10-14
This is the command I use to setup PHP and Apache:

```
sudo aptitude -y install apache2.2-common php5 && sudo rm -r /var/www && mkdir /home/$USER/localhost && sudo ln -s /home/$USER/localhost /var/www && echo "Your install was successful! You may now delete this file (/home/$USER/localhost/index.html)" | tee /home/$USER/localhost/index.html
```

What this does is it installs Apache 2.2 and PHP 5, removes /var/www (so if you have anything useful in there, make sure to back it up), creates a folder in /home/$USER/localhost (where $USER is the current user running the script) and then links /var/www to /home/$USER/localhost so you don't need to mess with Apache configuration files.

This enables you to use a folder right in your home directory (called 'localhost') to edit PHP files. You can access them via [http://localhost](http://localhost) and there is no need to mess with file permissions.

Ask for any clarification if you need any!

---

### Post by lykwydchykyn on 2008-10-15
Which ftp server are you using?  You should be able to set some kind of permissions mask or default permissions settings in your ftp server settings.  How exactly to do that depends on the particular ftp software you're running.

---

### Post by altonbr on 2008-10-15
> **lykwydchykyn said:**
> Which ftp server are you using?  You should be able to set some kind of permissions mask or default permissions settings in your ftp server settings.  How exactly to do that depends on the particular ftp software you're running.

He's not using FTP, but rather a localhost install.

---

### Post by lykwydchykyn on 2008-10-15
> **altonbr said:**
> He's not using FTP, but rather a localhost install.

Hmm.... don't know how I got that idea:

> 
This is what is happening, I create the php file in Dreamweaver on a windows box, upload it by ftp to my /var/www/ folder and it doesn't have permission to run what it needs to run. I have to manually do the chmod -R 777 each time I add a new file then it works.


---

### Post by Iowan on 2008-10-15
[This]("https://help.ubuntu.com/community/ApacheMySQLPHP") is a useful help page - check the topic about alternate site locations.

---

### Post by altonbr on 2008-10-15
So what others have been saying:

 * either make the ownership of the folder your own (by either my shortcut method or running 'sudo chown $USER:$USER /var/www') or,
 * make sure your FTP is setting the permissions properly

Either of those sound reasonable to me.

@lykwydchykyn: my fault for not reading that properly

---


---
title: "Help with virtual hosts on a server that does not have a domain!"
date: 2006-04-24
forum: Server Platforms
---

### Post by Elif Tymes on 2006-04-24
Ok, here's the deal:

I have Apache2 configured with PHP/MySQL/Mod_rewrite/Mod_curl/etc. all the stuff I need to use for my work. This is fine and dandy.

Now, what I want to do is have one folder

/var/www/

be my "localhost" directory

and another folder

/home/username/www/

Be my localhost/username directory.

However, I can't figure out how to do this.

I've copied the /etc/apache2/sites-available/default to /etc/apache2/sites-available/username and created the symbolic link for /etc/apache2/sites-enabled/username

it reads the config file just fine, but I can't figure out how to configure it so that the /home/username/www directory is accessible via localhost/username.

Any help would be much appreciated.

---


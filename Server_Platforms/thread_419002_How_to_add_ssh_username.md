---
title: "How to add ssh username?"
date: 2007-04-22
forum: Server Platforms
---

### Post by dwhs.info on 2007-04-22
I have following problem:i have one ssh username,id admin,for ssh.If i want root access,i simply type sudo su -.But the problem is,when i am normal user,i cant access to www directory(only as root can go in)and then problem is when i operate as root,directoryies and files which i create there it is non accesible by ftp user unless i chmod them to 776 which is not good beacuse that is security risk(i mean what i sense of having all directoryies 776)So i want to have ssh user which will  be copy of ftp user.

---

### Post by strixy on 2007-04-22
> when i am normal user,i cant access to www directory

that's a feature of the system and one I'm sure you appreciate.

You can use 

sudo ls /var/www

and work on /var/www out of your home dir that way. A little time consuming...

Or, create a group like, www-admin and then chgrp -R www-admin /var/www 

I don't see anything wrong with 774 permissions. (feel free to correct me)

Anything that's sensitive (eg. config.php files) you place in /var/web-safe and ln to them from /var/www. If you have more than one person working under www-admin group, create a sub group like, sub-www-admin and specify which files or dir's you want them to have access to. So long as your top admin has privileges in both groups, you're fine.

Another alternative would be to turn on public-html directories in apache. A little quality time with mod_vhost_alias will even let you turn    domain.com/~user    into    user.domain.com

---

### Post by dwhs.info on 2007-04-27
> **strixy said:**
> that's a feature of the system and one I'm sure you appreciate.

You can use 

sudo ls /var/www

and work on /var/www out of your home dir that way. A little time consuming...

Or, create a group like, www-admin and then chgrp -R www-admin /var/www 

I don't see anything wrong with 774 permissions. (feel free to correct me)

Anything that's sensitive (eg. config.php files) you place in /var/web-safe and ln to them from /var/www. If you have more than one person working under www-admin group, create a sub group like, sub-www-admin and specify which files or dir's you want them to have access to. So long as your top admin has privileges in both groups, you're fine.

Another alternative would be to turn on public-html directories in apache. A little quality time with mod_vhost_alias will even let you turn    domain.com/~user    into    user.domain.com
You mean 776 chmod,not 774

---


---
title: "Web Server (initial set up question)"
date: 2009-09-06
forum: Server Platforms
---

### Post by mattsilv on 2009-09-06
Please forgive me if this is a really silly question, but I am trying to set up a LAMP web server on a fresh install of Ubuntu.  I followed these instructions:

```

sudo apt-get install apache2
sudo apt-get install php5
sudo apt-get install libapache2-mod-php5
sudo /etc/init.d/apache2 restart

```

So far so good, but when I try to save a file in /var/www/ to test the install (phpinfo.php for example) it gives me this error:

```
Error writing phpinfo.php: Permission denied 
```

This must be a simple permissions error, as it does not seem to think I am the owner of the /var/www folder.  I am VERY new with Linux, so any help is greatly appreciated.  Thank you!

---

### Post by makariolewis on 2009-09-06
Correct, by default you won't have permissions to write to /var/www. You can fix this by either changing the permissions of /var/www to 777 with 'sudo chmod -R /var/www' or you can change ownership by using 'sudo chown -R username:username /var/www' in the terminal.

OR you can just add yourself to the group by going to System > Administration > Users and Groups, choosing Manage Groups, and adding yourself to the www group. (I believe it's called www, but I'm not quite sure. I don't have a web server on this laptop anymore.)

---

### Post by infallible on 2009-09-07
for ease, and security I prefer to use a separate working directory chowned to my user account, with symlinks in /var/www.

ie
mkdir /home/infallible-web/www/vhost_one
ln -s /var/www/vhost_one ~/vhost_one

---


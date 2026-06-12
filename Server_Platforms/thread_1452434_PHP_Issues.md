---
title: "PHP Issues"
date: 2010-04-11
forum: Server Platforms
---

### Post by Cavs23 on 2010-04-11
Basically I installed php, apache2, and mysql a few days ago via the package manager. I then realized it wasn't the most up to date version. (It was 5.2.10) I then tried installing php from the tar.gz from php.net. I made sure that I wiped all of the php config files and folders from my computer first and then installed. After a few hills I got it running. My php-cli is 5.3.1 but my php when I do phpinfo() on local host is still 5.2.1.

What must I do to change this?

---

### Post by s_ø on 2010-04-13
Try to use this command to find the php module.
```
locate libphp
```
There will probably be 2.
Now open php.load
```
sudo nano /etc/apache2/mods-available/php5.load
```
Edit to point to the new module you have installed.

Btw, why are you in such a hurry to get the latest version, its not more than 9 days old. And as far as i ca see it will be a part of lucid.

---

### Post by #Reistlehr- on 2010-04-13
don't forget to update your sym-links from /php/5.3.1/path/bin to /usr/bin so you can execute php-cli if need-be

---


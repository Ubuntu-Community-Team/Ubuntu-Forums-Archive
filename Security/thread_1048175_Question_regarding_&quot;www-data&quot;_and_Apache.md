---
title: "Question regarding &quot;www-data&quot; and Apache2"
date: 2009-01-23
forum: Security
---

### Post by gprint on 2009-01-23
Question regarding "www-data" and Apache2 ....

I am running a 'local-only' apache2 server on Ubuntu 8.04. I also have joomla 1.5 installed.

I have my document root set up to be in my home user directory ie: home/me/www/mysite, versus var/www default in root.

Here's my problem ....

I create a swf file using SwishMax. Swf file works very well. When it is created, I dump it into a file in my home directory. It's file permissions are fine - set for me as the user.

Then, I go to my browser, login to my local Joomla site here on my computer. 

I then go to Joomla Media Manager and upload the just-created swf file. It uploads fine.

However, upon checking the swf file itself, it's ownership is now "www-data", which from what I understand, is Apache2. From this point, it doesn't matter what I do, I cannot get that swf file to display in Joomla.

Do I need to change something in order to have uploaded files STAY owned by me as the user, and not become owned by www-data?

Thanks

---

### Post by Dr Small on 2009-01-23
Being owned by www-data should not be a big deal. But check the permissions on the file once uploaded and verify that they are at least 755 (rwx-rx-rx).

---


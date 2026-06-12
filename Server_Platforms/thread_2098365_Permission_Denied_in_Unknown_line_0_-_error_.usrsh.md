---
title: "Permission Denied in Unknown line 0 - error .:/usr/share/php:/usr/share/pear"
date: 2012-12-26
forum: Server Platforms
---

### Post by ladro1987 on 2012-12-26
Hi all,
I have two big problems which I don't understand if it are related.

I'm a beginner, I come back from Windows and this are my first "serious" problem with Ubuntu.

Two days ago, I installed LAMP from this tutorial:
[http://www.jeremymorgan.com/tutorials/linux/how-to-install-apache-php-and-mysql-on-ubuntu-12-dot-10-quantal-quetzal/](http://www.jeremymorgan.com/tutorials/linux/how-to-install-apache-php-and-mysql-on-ubuntu-12-dot-10-quantal-quetzal/)
and all was right.

After, I have installed PEAR libraries from this tutorial (below, where the "like" are 53), following all procedure:
[http://superuser.com/questions/55055/how-to-install-an-updated-version-of-pear-phpunit-on-ubuntu](http://superuser.com/questions/55055/how-to-install-an-updated-version-of-pear-phpunit-on-ubuntu)
and also, got a good end.

Well now...
1) My first problem is that I don't see the .htaccess' files, neither into my external HD (I sow it in Windows and the files are there). I don't think that this issue, could be related with the second but I don't exclude nothing.
2) The second issue, is worse then the above. I don't be able to see my local websites because every times which I try to look it, I get this <snip> error:

**Warning**:  Unknown: failed to open stream: Permission denied in **Unknown** on line **0**

**Fatal error**:  Unknown: Failed opening required  '/var/www/lavori/Untitled Folder/Untitled Folder/index.php'  (include_path='.:/usr/share/php:/usr/share/pear') in **Unknown** on line **0**

What is this? Which permission was denied?
I set up a vhost and I get that error both with address "http://www.prova.local/" and "http://localhost/lavori/prova2/sito/". I tried unsuccessfully a lot of ways and now I'm very very hopeless.
I would like to work with Ubuntu, I like it and I think that it could be very very good for my work. I would hate to leave it for this stupid problem but really I do not what to do! :(

I want specify too, that the local websites are into the "/var/www/" folder and I set up the permissions both 777 and 775 getting the same result.

I hope that anyone could save me from this stupid but big problem! :-)

I hope to hear from anyone soon!

Good Christmas

Roberto

---

### Post by newbie-user on 2012-12-29
For the first problem, any file or folder name starting with a period is a hidden file, so you'll have to ```
ls -a
``` in the command line or Ctrl+H in the gui if you want to see .htaccess.

As for the second problem, is there supposed to be a colon in /usr/share/php:/usr/share/pear?

---


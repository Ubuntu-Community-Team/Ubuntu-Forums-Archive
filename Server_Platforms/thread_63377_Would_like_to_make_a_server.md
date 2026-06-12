---
title: "Would like to make a server"
date: 2005-09-07
forum: Server Platforms
---

### Post by mobo on 2005-09-07
With php, apache and mysql installed i want to install my forum. This may seem relatively simple for most but Im stuck here. I need to get my forum package into the var/www/ folder. It appears that I dont have permission to write to that folder. Im guessing this is part of the security that these distros are know for.

That being said, what is the procedure for moving, folders into the www  folder ?

---

### Post by TheDanMan on 2005-09-07
apt-get install mysql-server
apt-get install php4
apt-get install apache2
apt-get install shorewall

Default mysql version for ubuntu is version 4.  Should be fine for the more common forum packages.

Shorewall is to lock down your box.  I think there are some howtos on this forum.  You might consider installing webmin, [http://www.webmin.com](http://www.webmin.com), and virtualmin, [http://webmin.com/index8.html](http://webmin.com/index8.html).  Both will make it easier for you exponentially.  Then if you want you can even throw up a couple other domains for friends.

To move your files to your /var/www/, try:
sudo mv /file/path/to/files/* /new/file/path/to/files/

---

### Post by pistoli on 2005-09-07
IF you want file access you could also change the owner of /var/www with this:
sudo chown <your user name here> /var/www

---

### Post by az on 2005-09-07
You may also just do

sudo nautilus

---

### Post by mobo on 2005-09-07
Ok guys im on the move now and will reply back tomorrow. I did a test machine and got all up and running with the forum in the directory and the php installed and functioning. There was an issue with the database however. Something about my account not having the correct prveledged. Would I have to run some type of command to give my account priveledges to create and run mysql databases as well ?


And thanks to all for your replies...

---

### Post by lao_V on 2005-09-08
A better solution would be to install any apps (cms, forum etc) onto your home directory and just make a VirtualServer entry in apache confs. 

To resolve the DB privliege issue have a look at the GRANT statement on mysql docs. Something like  ```
GRANT all priviliege on *.* to user@host
```

---

### Post by mobo on 2005-09-08
Well, frustrated I am.... :-#  :-#  :-#  :-#  :-#  :-# 

I opened mysqlcc and created a database named forum, gave it a username of mobe and set a password.


Then used your command modified:
GRANT all priviliege on *forum* to mobo@localhost

It lists a bit of info in the terminal window but I can not still start the database

---

### Post by lao_V on 2005-09-08
Follow this guide/tutorial on [mysql]("http://dev.mysql.com/doc/mysql/en/tutorial.html")
Let us know if you still have any problem

---

### Post by mobo on 2005-09-08
i better put this away for a while. Im quite frustrated now and its probably not going to happen..

Thanks anyway...

---

### Post by mobo on 2005-09-08
Ok I did something crazy and It worked..So its clearly a user permission thing..

mysqladmin -u root password db_user_password

I used root  and db_user_password and was able to connect

Go figure..

---

### Post by lao_V on 2005-09-08
Obviously you need to login as root before giving permissions to a user - just like you did when you created your user account :-)

---

### Post by LordHunter317 on 2005-09-08
[QUOTE=lao_V]To resolve the DB privliege issue have a look at the GRANT statement on mysql docs. Something like  ```
GRANT all priviliege on *.* to user@host
```[/QUOTE]This is a bad thing as you've essentially made two superuser accounts in the database.

Never, ever, ever do this.

---

### Post by cbudden on 2005-09-08
mobo, what theme are you using, i like the colour of your panel.

---


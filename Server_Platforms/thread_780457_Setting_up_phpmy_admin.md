---
title: "Setting up phpmy admin"
date: 2008-05-03
forum: Server Platforms
---

### Post by Jeztastic on 2008-05-03
Hi,

Have been trying to set up torrentflux using phpmy admin. Attempting to create a user, however I am getting this error message:

```
jez@server:~$ mysqladmin –u jez –p create torrentflux
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'jez'@'localhost' (using password: NO)'
```

Phpmyadmin seems to have defaulted my password to my sudo password, but I'm not sure why it's not giving me the option to enter my password at this stage. 

Thanks!

Jez

---

### Post by PseudoOne on 2008-05-03
```
(Using password: NO)
```

Means you did not supply a password to MySQL?

---

### Post by Alien Collective on 2008-05-03
If for some reason the password entry prompt isn't displaying (I don't see why not) you can also specify your password in the command itself. If your password were 12345:

```
mysqladmin -u jez -p12345 create torrentflux
```

Note that there is no space between the -p and the password.

Be aware that since the command will be briefly visible in top, there is the potential for someone else to get your password this way, but if you have the server to yourself that shouldn't be a concern.


*Edit: Sorry, I forgot that you were running phpMyAdmin. You can run that command from the command line if necessary, but why PMA shouldn't be working I'm not sure. Can you view and edit your databases normally otherwise?*

---

### Post by Jeztastic on 2008-05-04
> **PseudoOne said:**
> ```
(Using password: NO)
```

Means you did not supply a password to MySQL?


I have been attempting to do this. However I am getting an error message: 

I am inputting this in myPHPadmin:

```
SET PASSWORD FOR root@localhost=PASSWORD(‘12345’);
```

And getting this error:

```
Error

SQL query:

SET PASSWORD FOR root@localhost = PASSWORD( ‘12345’ )

MySQL said: Documentation
#1064 - You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'â€˜12345â€™)' at line 1 
```

I am a bit flummoxed as I don't know SQL, I'm following a guide to try and get torrentflux running.

---

### Post by ikt on 2008-05-05
First time I installed torrentflux I had a ton of trouble, was up till 4am, however months later I tried again and did it flawlessly first time.

When you are installing mysql it asks for a password, whatever you put in there is then used to login to phpmyadmin and configure mysql.

> jez@server:~$ mysqladmin –u jez –p create torrentflux

I'm still fairly new to the whole process, but if you are using phpmyadmin:

[http://img.cihar.com/phpMyAdmin.png](http://img.cihar.com/phpMyAdmin.png)

why create tables via the command line? :confused:

---

### Post by Jeztastic on 2008-05-05
Thanks for the tip - the guide may be pretty old - didn't realise I could do all that stuff via the GUI. Seem to be up and running now!

---


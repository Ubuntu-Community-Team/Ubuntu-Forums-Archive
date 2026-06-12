---
title: "[SOLVED] Securing the Initial MySQL Accounts"
date: 2007-08-23
forum: Server Platforms
---

### Post by southernman on 2007-08-23
I am following the guide at [http://dev.mysql.com/doc/refman/5.0/en/default-privileges.html]("http://dev.mysql.com/doc/refman/5.0/en/default-privileges.html") but have a couple of questions for clarity.

1- My first question / concern is regarding the annonymous accounts. Since I will be the only user on the server... it should be safe to do away with these. That would be the proper thing to do.. right? :/ 

2- My next question is in setting the root password. On a previous practice install, I only did:
```
mysql> SET PASSWORD FOR 'root'@'localhost' = PASSWORD('newpwd');

```
When I later restarted mysql, it failed saying something like:
> error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'

So I followed [this thread]("http://ubuntuforums.org/showthread.php?t=112505") I found by searching Google which removed the error and restarts / startups didn't hiccup any longer.

The question I suppose is... Did that error come because I didn't do the next command from the mysql manual which would be:
```
mysql> SET PASSWORD FOR 'root'@'host_name' = PASSWORD('newpwd');

```

3- My next question regards the "hostname" as outlined in this statement
```
mysql> SET PASSWORD FOR 'root'@**'host_name'** = PASSWORD('newpwd');

```

Is the hostname (in bold) suppose to be the same as the servers hostname as setup in /etc/hosts or what. I wasn't sure what to put there, even after reading the entire manual page including all the comments at the bottom, so I ignorantly opted to forgo it completely! I know... the only stupid question are the ones not asked (for the most part at least).

---

### Post by southernman on 2007-08-23
I found the answer to question number three... how to find the hostname.

Advice still respectfully requested on the first two questions.

Thanks in advance

---

### Post by LaRoza on 2007-08-23
> **southernman said:**
> I am following the guide at [http://dev.mysql.com/doc/refman/5.0/en/default-privileges.html]("http://dev.mysql.com/doc/refman/5.0/en/default-privileges.html") but have a couple of questions for clarity.

1- My first question / concern is regarding the annonymous accounts. Since I will be the only user on the server... it should be safe to do away with these. That would be the proper thing to do.. right? :/ 

2- My next question is in setting the root password. On a previous practice install, I only did:
```
mysql> SET PASSWORD FOR 'root'@'localhost' = PASSWORD('newpwd');

```
When I later restarted mysql, it failed saying something like:

So I followed [this thread]("http://ubuntuforums.org/showthread.php?t=112505") I found by searching Google which removed the error and restarts / startups didn't hiccup any longer.

The question I suppose is... Did that error come because I didn't do the next command from the mysql manual which would be:
```
mysql> SET PASSWORD FOR 'root'@'host_name' = PASSWORD('newpwd');

```


Deleting the annonymous accounts is a good practice.

When you log on, use this:

```

mysql -u *userName* -p

```
You will be asked for your password.

If you are going to be using MySQL, you should create a new user, that has limited permissions, being root is dangerous.

---

### Post by az on 2007-08-23
If you are running the LAMP stack on a single machine (the default behaviour) mysql does not listen for connections from the network, so you don't need to set a root password for anything but localhost.

---

### Post by KevinM1 on 2007-08-23
Here's what I did for my MySQL security:

1. Removed all users from mysql.users except root@localhost, root@127.0.0.1, and debian-sys-maint.

2. Renamed my root user to something else.  So, currently, I have no user that's root@localhost or root@127.0.0.1.

3. Created a new user for scripts to use.  Restricted their privileges to SELECT, INSERT, UPDATE, and DELETE.

I think that's really the crux of it.  Just limit how many points of entry there are, limit what public/script users can actually do (I'm a bit weary about even allowing them to delete rows, but some of my scripts call for it), and try to protect root as much as possible by giving it a good password and perhaps even changing root's username.  So, right now I have three users: my root account, my script account, and the debian-sys-maint account.  No one else is allowed in.

If you're going to be accessing your database via scripts (especially through web forms and what not), the rest just comes from good coding practice.  Never trust user input, always check that input and escape it before inserting it into the database, etc.

---

### Post by southernman on 2007-08-23
Thank you - LaRoza, AZ (I know I saw your "z" around here somewhere), and KevinM1

When I listed the users from mysql it only showed 3 (debian-sys-maint and 2 root). Nothing found in the forum of anon so I am guessing here, that this is something the LAMP installation does by default? NO?

No fret on me writing any scripts, let alone that require interaction with MySQL anytime soon. I may install Word Press or Joomla but now KevinM1 has me wondering why when setting up a database for Word Press, the install guide tells you to GRANT ALL PRIVILEGES to the new user and database. My guess is it's ok so long as it is a seperate database entirely.

My (as all installs are I presume) there are two other accounts other than the debian-sys-maint and that being:

root@localhost (full blown privileges)
root@hostname (only SELECT, INSERT, UPDATE, DELETE, CREATE)

#2 actually has me stumped as well... but I'll do a bit of google research on that TOO.

---

### Post by KevinM1 on 2007-08-23
> **southernman said:**
> Thank you - LaRoza, AZ (I know I saw your "z" around here somewhere), and KevinM1

When I listed the users from mysql it only showed 3 (debian-sys-maint and 2 root). Nothing found in the forum of anon so I am guessing here, that this is something the LAMP installation does by default? NO?

No fret on me writing any scripts, let alone that require interaction with MySQL anytime soon. I may install Word Press or Joomla but now KevinM1 has me wondering why when setting up a database for Word Press, the install guide tells you to GRANT ALL PRIVILEGES to the new user and database. My guess is it's ok so long as it is a seperate database entirely.

My (as all installs are I presume) there are two other accounts other than the debian-sys-maint and that being:

root@localhost (full blown privileges)
root@hostname (only SELECT, INSERT, UPDATE, DELETE, CREATE)

#2 actually has me stumped as well... but I'll do a bit of google research on that TOO.

If you're using pre-made scripts (like a blog or CMS), I recommend just using what their instructions say to do.  Their code may have some advanced database voodoo going on behind the scenes.  Just be sure that you monitor what other users (if any) are signing up for those sites/services.  I'm not too familiar with Joomla, but I know PHP-Fusion gives site administrators the ability to manually authorize  potential users before letting them run wild on a site.  It helps to secure such sites from drive-by porn bots.

---

### Post by southernman on 2007-08-23
Thanks for confirming that Kevin. I suspected as much but wanted to be certain.

---

### Post by southernman on 2007-08-23
Forgot to take my own advice in marking my post as solved.

Thanks again for the help!

---


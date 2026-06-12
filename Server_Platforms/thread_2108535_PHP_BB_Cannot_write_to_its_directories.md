---
title: "PHP BB Cannot write to its directories"
date: 2013-01-24
forum: Server Platforms
---

### Post by Extol11 on 2013-01-24
So installed my lamp server using Lubuntu 12.10 and setup the writting permissions the way the official pdf guide says to: 

```
sudo chgrp -R webmasters /var/www
sudo find /var/www -type d -exec chmod g=rwxs "{}" \;
sudo find /var/www -type f -exec chmod g=rws  "{}" \;
```
I created a folder called forum and unzipped phpbb there and created a database for it and gave it a name. So I go to the phpbb url by using 127.0.0.1/forum and in the requirements list everything is fine except the last requirements. 

```
cache/:
Found, Unwritable
files/:
Found, Unwritable
store/:
Found, Unwritable

config.php:
Found, Unwritable
images/avatars/upload/:
Found, Unwritable

```

It seems I have to give the website permission to write to those files but I have no idea on how to do this. The website itself can't be added to a usergroup, can it? How do I do this?
Edit: This is PhpBB 3.0.1 BTW.

---

### Post by SeijiSensei on 2013-01-24
The Apache server runs as user www-data in group www-data. The simplest solution is to assign the directories to group www-data and make them writable by that group:
```

sudo chgrp -R www-data /var/www/whereever
sudo chmod -R g+w /var/www/whereever

```

If you want to have a separate "webmaster" group, you can either add the www-data to that group, or have www-data own the directories itself with group webmaster and the group-writable switch enabled as above.

---

### Post by Extol11 on 2013-01-24
> **SeijiSensei said:**
> The Apache server runs as user www-data in group www-data. The simplest solution is to assign the directories to group www-data and make them writable by that group:
```

sudo chgrp -R www-data /var/www/whereever
sudo chmod -R g+w /var/www/whereever

```

If you want to have a separate "webmaster" group, you can either add the www-data to that group, or have www-data own the directories itself with group webmaster and the group-writable switch enabled as above.

I'd like to add www-data to the "webmaster" group. What I did was change "webmaster" with my user name (group) and I'm going to be writting directly there. How do I add www-data to that group? And thanks a lot for the help.

---

### Post by SeijiSensei on 2013-01-24
```
sudo usermod -G webmaster www-data
```

Using -G makes webmaster a secondary group, which is what you want.  The -g switch assigns a primary group, the one that you belong to after logging in.

---

### Post by Extol11 on 2013-01-26
> **SeijiSensei said:**
> ```
sudo usermod -G webmaster www-data
```

Using -G makes webmaster a secondary group, which is what you want.  The -g switch assigns a primary group, the one that you belong to after logging in.

Ok. I'm going to try it today (first chance I've had). So this will make a second group whose "parent" is my main group? And I get to use any name I want for it or do I have to strictly use webmaster?

---

### Post by SeijiSensei on 2013-01-26
You have to create the group first with the addgroup command, then add users to it.

Users have a "primary" group to which they are assigned at login.  Nowadays a group is created for each user with the same name as the username and the same numerical ID as well.  However a user can belong to many other groups.  The command I gave is designed to assign a user to one of those secondary groups.

Each user is represented by an entry in the file /etc/passwd that looks like this:

```
seiji:1000:1000:Seiji's House:/home/seiji:/bin/bash
```

The first number is the user's ID; the second is the primary group ID.  In the file /etc/group you'll find a corresponding entry like this:

```
seiji:x:1000:
```

which creates a group named "seiji" with group ID 1000.  If you had a user "joe" that you wanted to put in seiji's group, you can use the command I gave above, or just append "joe" to the end of this record in /etc/group like this:

```
seiji:x:1000:joe
```

That grants joe a secondary membership in group seiji.

---


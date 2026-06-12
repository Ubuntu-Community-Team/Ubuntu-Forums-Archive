---
title: "Why doesn't a new MySQL user have its own list of databases?"
date: 2009-07-21
forum: Server Platforms
---

### Post by avahi on 2009-07-21
I have the user 'root', it has about 5 databases. I made a new user, and ran a 'show databases;' command on its account. Why can it see Root's databases? I want to make it so each user can only see and manage their own DBs. How can I accomplish this?

Thanks

---

### Post by grantemsley on 2009-07-21
You need to set the permissions appropriately.  phpMyAdmin is the easiest way to manage the permissions.

---

### Post by Kolipoki on 2009-07-21
> **grantemsley said:**
> You need to set the permissions appropriately.  phpMyAdmin is the easiest way to manage the permissions.
Avahi: Give PHPMyAdmin a try. Is webbase managed and you won't want to do anything without it after trying it.```
sudo apt-get install phpmyadmin
```After installing it, just go to [http://yourdomain.com/phpmyadmin](http://yourdomain.com/phpmyadmin) and log in with you MySQL root (or privileged user) password. (Would be even better if you got SSL on that server so you can log in with HTTPS)

---

### Post by NewbieNik on 2009-07-21
or if you prefer maintainence from the ubuntu desktop:-

sudo apt-get install mysql-admin

It appears in your Application -> Programming Menu.. 
My sql admin tool of choice.(See what I did there? My sql..get it?)

---

### Post by cariboo on 2009-07-21
You can also give a user the same privileges as root with the following command. Start the mysql console and at the prompt type:

```
grant all privileges on *.* to <user>@'localhost'
identified by '<password>' with grant option;
grant all privileges on *.* to <user>@'%'
identified by '<password>' with grant option;
```

The second line starting with grant also allows that user remote access.

---


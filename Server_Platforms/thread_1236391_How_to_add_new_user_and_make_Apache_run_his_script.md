---
title: "How to add new user and make Apache run his scripts as this user."
date: 2009-08-10
forum: Server Platforms
---

### Post by resha on 2009-08-10
Hello!

I need to dynamically create Ubuntu user (let's say *testuser*) with home folder containing *~/www* folder and make this folder accessible by URL like */~testuser/*. More than that, I need Apache to run scripts from this folder as *testuser*. And also, I need to do this without restarting Apache every time I create new user.

I know how to create user with home folder containing *www* folder. But I've stuck on initial Apache configuration to support my described needs and what I need to do to have this system work dynamically.

Help, please :) Tnx.

---

### Post by Brazen on 2009-08-10
> **resha said:**
> Hello!

I need to dynamically create Ubuntu user (let's say *testuser*) with home folder containing *~/www* folder and make this folder accessible by URL like */~testuser/*. More than that, I need Apache to run scripts from this folder as *testuser*. And also, I need to do this without restarting Apache every time I create new user.

I know how to create user with home folder containing *www* folder. But I've stuck on initial Apache configuration to support my described needs and what I need to do to have this system work dynamically.

Help, please :) Tnx.

I'm pretty certain there isn't going to be any way to run scripts as anything other than the apache user (www-data by default, I think).  I think your are going to have to find a different way to do what you want to do.

---

### Post by resha on 2009-08-10
> **Brazen said:**
> I'm pretty certain there isn't going to be any way to run scripts as anything other than the apache user (www-data by default, I think).  I think your are going to have to find a different way to do what you want to do.
Apache is running under user, that is set by "User" property in Apache conf. So, I thought about dynamically changing this property or maybe the way to change this for different virtual hosts...

---

### Post by Brazen on 2009-08-11
> **resha said:**
> Apache is running under user, that is set by "User" property in Apache conf. So, I thought about dynamically changing this property or maybe the way to change this for different virtual hosts...

It would probably be possible to change the user in the conf file, but then apache would have to be stopped and restarted, which I imagine would cause havok.

I supposed you could queue up the tasks, either in a database table or a parseable text file, and then have that database or text file read and executed by something else.

How often do the scripts need to be run?  You could set up a cron job for each user to check on new tasks every 5 minutes, 30 minutes, 1 minute, or whatever works good for your needs.

It would work something like this:
1) create a text file in the users home directory and give apache write access to it (maybe call it ~/apache_worker)
2) have apache write the script to this file
3) set up cron job as user (read 'man crontab' for info) to execute file and then empty it (so it doesn't get executed again until apache rewrites it)

Depending on the usage, this may be enough.  This isn't really a queue though, so if apache tries to rewrite the file while cron is executing it, it will probably fail or cause other problems.  I would probably use an sqlite database and as apache needs scripts run, have apache add them to the database.  Then have the cronjob read the database and delete the database entries as they are run (or mark the script as 'ran', if you want to keep a record).  This would really only take slightly more effort to set up than the plain text file approach.

---

### Post by hessiess on 2009-08-11
> **Brazen said:**
> I'm pretty certain there isn't going to be any way to run scripts as anything other than the apache user (www-data by default, I think).  I think your are going to have to find a different way to do what you want to do.

suexec

---


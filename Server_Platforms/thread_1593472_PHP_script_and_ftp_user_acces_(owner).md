---
title: "PHP script and ftp user acces (owner)"
date: 2010-10-11
forum: Server Platforms
---

### Post by flodulv on 2010-10-11
When i create folders in a PHP script fom my website, the folder is created but has owner "33"
My ftp user have an other "Owner ID" than this.
So i can't delete or edit the files that is created.
How can i fix this.

I'm running Ubuntu 10.04 on a VPS server.
ISPconfig3
proftpd
i think i have LAMP (it was installed with a script from my hosting company)

Also the safe_mode is off.

Hope anybody can help me here. i'm very new at ubuntu :confused:

---

### Post by flodulv on 2010-10-12
Sorry for bumping, but this is a issue that i need to solve.
Is there anyone that know how to fix this ?

---

### Post by Thirtysixway on 2010-10-12
> **flodulv said:**
> Sorry for bumping, but this is a issue that i need to solve.
Is there anyone that know how to fix this ?

It's because the webserver is its own user. What you can do is run 

sudo chown user:group foldername

and that will change the permissions (change user:group to whatever you need of course..)  You could look into using the suPHP apache module 

[http://www.howtoforge.com/install-suphp-on-various-linux-distributions-for-use-with-ispconfig-2.2.20-and-above](http://www.howtoforge.com/install-suphp-on-various-linux-distributions-for-use-with-ispconfig-2.2.20-and-above)

This is supposed to help solve some permission issues.  What it does is make PHP execute as the user who owns the php file. This way, new files/folders that are created will still be accessible by you :)

---

### Post by flodulv on 2010-10-14
Thanks for reply, but i can't get this to work.
There is some errors, and my server don't accept these.
I'm runnng ubuntu 10.04 and ispconfig 3

---


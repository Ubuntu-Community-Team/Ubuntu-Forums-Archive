---
title: "Trouble creating password for mysql user"
date: 2010-01-21
forum: Server Platforms
---

### Post by green351 on 2010-01-21
Hi,
I've been following the instructions here: [http://www.jonathanmoeller.com/screed/?p=1261](http://www.jonathanmoeller.com/screed/?p=1261) for installing wordpress (I'm planning on making a website for my brother's business).  I've gotten down to where I start running mysql using
**mysql -u root –p**
 then i did 

 **CREATE DATABASE wordpress;**
which seemed to work fine.  then i did **CREATE USER wordpressuser;**
 which also worked.  But then when I tried to set a password using
[B]
SET PASSWORD FOR wordpressuser = PASSWORD(“password”);[/B]
I get the following error message:
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '“password”)' at line 1

I tried several different passwords including the one to log into mysql, a password with only lowercase letters, with letters and numbers, and one with upper case and lower case and numbers and symbols.  Does anybody know what might be going on?

thanks

---

### Post by cdenley on 2010-01-21
You need single quotes, not double.
```

SET PASSWORD FOR wordpressuser = PASSWORD('password');

```

---

### Post by green351 on 2010-01-21
Thanks that worked!

---


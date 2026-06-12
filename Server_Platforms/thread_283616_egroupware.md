---
title: "egroupware"
date: 2006-10-24
forum: Server Platforms
---

### Post by mwerlberger on 2006-10-24
Hi!

I just wanted to egroupware to my new server. The problem that an apt-get install egroupware wants to install quite a lot of php4 stuff. I want to stick to php5 and dont install anything lower than that. On the homepage of egroupware it says that it works with php5 only. So why does the deb file wants to install quite a lot of things correlated to php4?

Thanks for any help,
 Manuel

---

### Post by bluefrog on 2006-10-25
What's the egroupware version available in ubuntu repo? what is the actual version available on egroupware.org?

The difference comes from there I believe.

James

---

### Post by Abhi Kalyan on 2006-11-08
> **mwerlberger said:**
> Hi!

I just wanted to egroupware to my new server. The problem that an apt-get install egroupware wants to install quite a lot of php4 stuff. I want to stick to php5 and dont install anything lower than that. On the homepage of egroupware it says that it works with php5 only. So why does the deb file wants to install quite a lot of things correlated to php4?

Thanks for any help,
 Manuel
I have tried out only phpgroupware, 
giving you the list of aspects that i installed, in numerical order
1. Apache2
2. MySQL
3. php-5
4. php support for mysql
5. phpmyadmin (for MySQL administration using browser)
6. phpgroupware.
Well thats where it all stands.
Cheers Please do post back on egroup wasre, Am trying out that now.

---

### Post by djdicbob on 2006-11-16
The repository version is 1.0.0.009.  Egroupware's svn version is now 1.2.xxx.  I have installed the repository version and it works fine, except it doesn't install all the applications properly.  When I get that fixed, I will post back!

---

### Post by DRicher33 on 2006-11-16
Hi there,

Don't know if you still need help but I successfully got egroupware working by doing the following:

Before you do anything make sure your apache and mysql is working and you can log into mysql with root etc

1.  Run the apt-get install egroupware and then cancel it
2.  apt-get install all the php5 and non-egroupware packages first from the list created by apt
3.  run the install of egroupware again and make sure you didn't miss any other packages..all you should see is the egroupware-* etc in apt.
4.  if you only see the egroupware left then let it install.

Worked for me on edgy and avoids apt installing php4 files

---


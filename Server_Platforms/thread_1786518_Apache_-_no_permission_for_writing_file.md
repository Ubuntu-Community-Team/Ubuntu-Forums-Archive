---
title: "Apache - no permission for writing file"
date: 2011-06-19
forum: Server Platforms
---

### Post by Ajantis on 2011-06-19
Hello,

I'm trying to familiarize myself with Apache and general server administration. I've enoucntered one problem though.

I'm running Debian and DirectAdmin and of course Apache2.

When I create new user, the home directory is user:user. Perfectly fine, Apache can access all files and they display correctly. But Apache cannot write any files, saying no permission.

If I chown the directory to apache, server can easily write everything, but at the same time if I log in to SSH with my user/pass, I cannot do anything with those files as obviously they belong to apache.

I tried adding www-data and apache as secondary groups to my user but for no avail. I'm pretty confused, I would like the directory and all files to be owned by user, but at the same time I would like Apache to be able to write/modify files in it.

Is it possible?

Sorry if this question is dumb, I tried googling and checking on the forums but either I couldn't find, it doesn't help or I don't get it :P

---

### Post by BkkBonanza on 2011-06-20
It's generally a bad idea to give Apache write perm on all your files. A good compromise is to designate one subdir to be for writeable files and make that one have Apache group write perms. This limits what can be altered by anyone who compromises a script or gains control via Apache. 

I typically own the files with rw perm, and give the apache group (commonly called www-data) r perm except for a special directory where it can also have w perms. This has proven over the years to be fucntional enough to work for me.

---


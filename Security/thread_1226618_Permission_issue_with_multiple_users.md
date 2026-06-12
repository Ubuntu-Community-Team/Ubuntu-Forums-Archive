---
title: "Permission issue with multiple users"
date: 2009-07-29
forum: Security
---

### Post by sdlyr8 on 2009-07-29
Okay so I'm trying this in a different category. Might be a better place to ask....

I have a small website project that a friend and I are working on and it's located on my ubuntu box. I made him a user account and added him to the admin group. I thought I set the right permissions on the files but I guess not because he can only read, and not write. And I can only read but not write to his files (without sudo).

He's using dreamweaver on a windows machine so I can't expect him to be able to sudo, and I would rather not have to either since I use Eclipse mainly.

Starting from scratch... what settings do I need to set in order for us to be able to edit each others files (all in /var/www only) and so that newly created files get permissions that we can both use?

---

### Post by bodhi.zazen on 2009-07-29
Probably the easiest way is to put both users in the www-data group and run a script to change the group and permsions of files in /var/www

to root.www-data 

permissions 660 for files 770 for directories.

You can use other techniques such as alc or changing your umask values, takes more effort.

[http://www.cyberciti.biz/faq/linux-setup-shared-directory/](http://www.cyberciti.biz/faq/linux-setup-shared-directory/)

---

### Post by sdlyr8 on 2009-07-30
Thanks for your help! That works.... almost.

Everything works fine when I do it, but then when he goes and creates a file, it gets set to '-rw-r--r--' and I can't edit it. Same goes the other way too. I've played with setting umask to a+rw but nothing seems to work. I tried the link you sent too. Now when a file gets created, it keeps the www-data group. SO.. I guess the only problem I have is needing to change the default permissions when files get created

---

### Post by bodhi.zazen on 2009-07-30
Yes, it does not happen automatically.

A better solution is what is called acl or access control lists.

See this thread : 

[http://ubuntuforums.org/showthread.php?t=145741](http://ubuntuforums.org/showthread.php?t=145741)

---

### Post by sdlyr8 on 2009-07-30
Thanks for your help! That did it! :)

---

### Post by bodhi.zazen on 2009-07-30
You are most welcome.

---


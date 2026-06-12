---
title: "my website needs write access"
date: 2007-11-15
forum: Server Platforms
---

### Post by downat420 on 2007-11-15
Kubuntu 7.10
PHP 5
mysql
apache2

I am using dolphin community builder v6.0. I logged in to test the new user and new profile creation.  I can see that there is a user (the one i created) but the profile page for that user does not load.  I get a 404 not found.  

Dolphin resides in
/var/www/website/community

I believe dolphin is trying to create a directory in community.
example:
/var/www/website/community/profile
because the url is website/community/profile

I know that the mysql database is working because the user information is searchable on the site.  What do I need to do to correct profile issue?

Thanks in advance everyone,
Zach

---

### Post by downat420 on 2007-11-16
I found out I need to take a look at the Apache configuration. Somewhere in there the User and Group are specified.  I think the users are userweb and groupweb.  I am guessing I will have to chmod my directories for write access for those users?  Does this sound correct?  How would I do this?

---

### Post by downat420 on 2007-11-27
does anyone have any ideas, it has been a week or better and I have tried changing all my AllowOverride directives from

AllowOverride None
to 
AllowOverride All

Anyone know what I am missing?

---


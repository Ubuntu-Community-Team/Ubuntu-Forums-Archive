---
title: "phpbb2"
date: 2006-06-27
forum: Server Platforms
---

### Post by sidefx on 2006-06-27
I hope this is the right forum for this, apologies if it's not.  I'm trying to install a test phpbb2 forum on my local machine following these instructions:

[https://help.ubuntu.com/community/Phpbb2HowTo](https://help.ubuntu.com/community/Phpbb2HowTo)

but when trying to access localhost/phpbb2 I get the following error:

Warning: require(/etc/phpbb2/config.php) [function.require]: failed to open stream: Permission denied in /usr/share/phpbb2/site/config.php on line 24.

The only thing on line 24 of config.php is the mysql password for my 'phpbb2' user. I've checked and the database is created and this user definately has access rights to it, and the password I have there is definately right...

Could anyone suggest what I might be doing wrong or where I might start trying to diagnose it?

---

### Post by sidefx on 2006-06-27
Ah, don't worry, found the problem - /etc/phpbb2 didn't have the right permissions. Sorry. :-/

---


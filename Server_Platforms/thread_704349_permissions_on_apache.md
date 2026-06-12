---
title: "permissions on apache"
date: 2008-02-22
forum: Server Platforms
---

### Post by Mitis on 2008-02-22
hi !

First, since this is my first post, I want to say big Hello to everyone ;)

I want my server a multiuser server, where any php script called by browser will be executed in the "permission-contents" of the user it belongs to.

So, if I have /home/user1/www/test.php and users calls test.php through a browser and that scripts uploads file, that file will have a permissions of user1 and not apache2 user - "apache2" is default apache user in my apache config.

Can anyone suggest a solution ? Changing any permissions with chmod either on server or in the php scripts is not an option.

Thanks in advance.

---

### Post by rapiscan on 2008-02-25
Hello there.

I believe the suPHP apache module is what you're looking for.  You can check it out here:
[http://www.suphp.org/Home.html](http://www.suphp.org/Home.html)

---


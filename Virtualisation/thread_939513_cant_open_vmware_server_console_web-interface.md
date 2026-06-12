---
title: "cant open vmware server console web-interface"
date: 2008-10-06
forum: Virtualisation
---

### Post by ChristianWentzel on 2008-10-06
HI

I am new to ubuntu and vmware.

I have installed vmware server 2 wich is managed throug a web interface but i cant open the interface.

fire fox says : Firefox can't establish a connection to the server at 127.0.0.1:8333. Though the site seems valid, the browser was unable to establish a connection

Please help
Thanks

---

### Post by bluemuppet on 2008-10-06
Try putting https:// in front of it.
At a command prompt, I typed vmware, and it launched a browser straight to the correct URL.

Furthermore:
You have to accept the SSL certificate the site is putting forward.

In firefox you should be able to add an exception to allow this to happen. If you dont even get this far, then maybe your firefox security level needs to be turned down in the preferences.

Have a look at the second post on this page:
[http://support.mozilla.com/tiki-view_forum_thread.php?comments_parentId=167887&forumId=1](http://support.mozilla.com/tiki-view_forum_thread.php?comments_parentId=167887&forumId=1)

Once you've logged in, tell me the user (eg root) you used, as I cant seem to get past that bit.

---

### Post by ChristianWentzel on 2008-10-06
Hi
The url i get in my browser is [https://127.0.0.1:8333/](https://127.0.0.1:8333/)

there is nothing about adding exeptions.

When i run vmware from a terminal as root i get :
(firefox:23565): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by ChristianWentzel on 2008-10-08
I have found the solotion to my problem:
when i downloaded the install package i accedentely downloaded the RPM image.
being 500mb i decided to convert it to debian using alien.

I installed it and everything looked fine but it was not.

I just downloded the deb package and installed it and every thing is working fine.

the username and password i used was root and my root password as set with th cli.

thanks
Christian

---


---
title: "phpmyadmin issues , help!"
date: 2010-05-19
forum: Server Platforms
---

### Post by AresArtemis1 on 2010-05-19
hi,  any professionals, how to configure phpmyadmin, to let only the  root user is permitted to login into web based phpmyadmin control panel?

because I am setting up a web server, and I create some new mySQL user, but I find those new mySQL user login into mySQL through the web based phpmyadmin, the new mySQL user can delete any other new user account and database, and the new mySQL user even can see others in his mySQL manager interface web page.



any simple way can prevent new mySQL user deleter others account and see each other?




best thanks and regards,


:guitar::guitar::guitar::guitar::guitar:

---

### Post by sahabcse on 2010-05-19
when ever you create new user in mysql. he has privileges to access his database only. If we want to give access to other user database you have to give the grant access.

---

### Post by atroxes on 2010-05-19
If you log into your PhpMyAdmin web-interface as a root user, you will find a tab at the top called "privileges" which is where you assign permissions to your users.

Hope this helps.

---


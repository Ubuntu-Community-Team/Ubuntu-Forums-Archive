---
title: "mailserver migration"
date: 2009-11-11
forum: Server Platforms
---

### Post by Yipikaye on 2009-11-11
Hi all,

i'm planning to migrate the company's mailserver from mac os x 10.4 sever to ubuntu 8.04 LTS.
since this is my first mail server i have some questions 
-the thing i worry about is migrating the mail stored on the server and the user database.
does anyone have experience with this?
-what do i need install/modify to create virtual users instead of system users?
-also i was thinking about using roundcube as a web client but is it as save as squirrelmail? 
thanks

wessel

---

### Post by TuckLive on 2009-11-11
Not to hijack your thread, but I also would like to know if RoundCube is as safe as Squirrelmail.

---

### Post by mok0 on 2009-11-12
Instead of 8.04, consider 9.10 (or 9.04), where there's a new Ubuntu-supported mail stack that works pretty much out of the box. You simply install the package dovecot-postfix and most of the work is done.

---


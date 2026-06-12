---
title: "apache 403 error with changed www root"
date: 2011-02-09
forum: Server Platforms
---

### Post by xxTTcc on 2011-02-09
Hello all!
I don't know if this the right place to ask this question. If not excuse me.

I installed apache server on my ubuntu and I've changed the www folder in etc/apache/.../default from /var/www to home/user/www but now i have

Forbidden

You don't have permission to access / on this server.

So how to give permission. Thanks a lot in advance.

---

### Post by uRock on 2011-02-09
Bump for move to Server Platforms sub-forum.

---

### Post by wormyblackburny on 2011-02-09
Lets start with your httpd.conf file and do a getfacl of your home, user, and www folder. Post the contents of each (dont forget to use the code tags)

getfacl /home
getfacl /home/user
getfacl /home/user/www

---

### Post by elico on 2011-02-10
did you check these directories owners and permissions ?
it most likely from wrong permissions.

---


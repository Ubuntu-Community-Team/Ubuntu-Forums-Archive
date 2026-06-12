---
title: "users-permisions"
date: 2008-07-31
forum: Server Platforms
---

### Post by hirohitosan on 2008-07-31
Hi there.
I run Apache web server on my computer. 
I have 2 users: user1 and user2
in /etc/apache2/http.conf I set up the ```
UserDir		public_html
```
I created on both home users the folder public_html.
for the user1 I can read with a web browser the content of the:
my.server/~user1, but for the user2 I get an error message:
my.server/~user2 -> Forbidden
You don't have permission to access /~user2/ on this server.

I guess that is a matter of user permissions or groups. What kind of permissions should I add to user2 for reading with a web browser the content of the user2/public_html folder?

Thanks a lot

---

### Post by ChumleyEX on 2008-07-31
check out the permissions for each directory

> cd /home/USERNAMEHERE
ls -l


it should give you something like this

> -rw-r--r-- 1 root root 166 2007-03-07 21:02 welcome.msg


you want the one that doesn't work to match the one that works. More then likely you just need to change to something like the one above by typeing this next command in user2's home folder

> sudo chmod 744 public_html

hope that helps. 

[http://catcode.com/teachmod/](http://catcode.com/teachmod/)

---


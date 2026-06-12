---
title: "Problem with mysql connection"
date: 2017-10-01
forum: Server Platforms
---

### Post by dam034 on 2017-10-01
Dear users,

I'm developing a game server, and this uses mysql to store data.

I installed LAMP server and I try to access to mysql via phpmyadmin without problems. These are the data related to the database:
```
Host: localhost
User: mtasa
Pass: (none)
Dbname: mtasa
```
I want to specify I can access this db via phpmyadmin without problems.

Now we go to the game server, it's MTA San Andreas, I get this error when I try to connect to mysql:
```
WARNING: [mie]/prova/mysql.lua:4: Bad usage @ 'dbConnect' [Can't connect to local MySQL server through socket '' (111)]
```
This is the lua code in script file:
[php]db = dbConnect('mysql', 'dbname=mtasa;host=localhost;port=3306;', 'mtasa', '', "share=1")[/php]

I think the problem is on mysql, not in lua file.

How can I fix this issue? Help!

---

### Post by wildmanne39 on 2017-10-01
*Thread moved to **Server Platforms for better fit**.*

---

### Post by dam034 on 2017-10-01
Thanks for moving the thread, but there is anyone to help me?

---

### Post by wildmanne39 on 2017-10-01
You need to give it time we are a community of volunteers all across the world and most people have not had a chance to see your post yet and the person that can help may not be online right now. If no reply in 12 hours you can bump your thread to keep it on the front page.

---

### Post by darkod on 2017-10-01
The error message seems to be clear that your dbConnect statement is wrong. I would start by confirming the correct syntax for that statement. Also, the message seems to say it is trying to connect via socket while it looks like the mysql is running on standard port 3306, not socket.

---

### Post by dam034 on 2017-10-01
I thought a thing: how can I specify the socket?


Thanks

---

### Post by darkod on 2017-10-01
You should find more info here: [https://dev.mysql.com/doc/refman/5.5/en/connecting.html](https://dev.mysql.com/doc/refman/5.5/en/connecting.html)

---

### Post by dam034 on 2017-10-02
I specified the socket as **/var/run/mysqld/mysqld.sock** and now it works.

Thanks for the help

---


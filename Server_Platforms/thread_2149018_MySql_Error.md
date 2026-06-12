---
title: "MySql Error"
date: 2013-05-27
forum: Server Platforms
---

### Post by TheMattVid on 2013-05-27
I have recently installed mysql on my server using putty. I created a password for the "root" user when it prompted me to create one.

When I type in the command:
mysql -u root -p
It asks me for my password. When I type it in and hit enter, it give me this message:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

I am sure that the password is correct, so what am I doing incorrectly?

---

### Post by Lars Noodén on 2013-05-27
The syntax looks ok.  Maybe you mistyped your root password when you entered it the first time.  You can reset the mysql root password but have to hop through a few easy hoops to do so:

[https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)

Later, looking ahead you might think about MariaDB.  It's a drop in replacement and works with MySQL databases as-is.  It's not in the Ubuntu repositories yet though.

---

### Post by TheMattVid on 2013-05-27
Thanks for the suggestion. It asked me to verify the password when I made it, and I even had it written down, so I am absolutely sure that it is correct, but I will try the password reset anyway. If anybody has any different explanations for this error (because I have heard that error messages can mean multiple possibilities), please help me out.

---

### Post by remeny on 2013-05-27
You said you used putty to install and set it up. This helped me out tons
[http://dev.mysql.com/doc/refman/5.1/en/access-denied.html](http://dev.mysql.com/doc/refman/5.1/en/access-denied.html)

---

### Post by TheMattVid on 2013-05-28
The problem ended up being the characters I was using in my password.

---


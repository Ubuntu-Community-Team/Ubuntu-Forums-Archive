---
title: "MySQL can't assign root@locahost password."
date: 2006-07-03
forum: Server Platforms
---

### Post by wjc on 2006-07-03
I installed mySQL successfully and it appears to be running correctly.  However, when I try to set the 'root@localhost' password, it returns the following error (I've replaced the password I'm trying to give it with XXXX):

[B]xxx@ubuntu01:~$ mysqladmin -h localhost -u root password XXXX
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'[/B]

I've tried using "root@localhost"  and it returns another error:
[B]mysqladmin: connect to server at 'root@localhost' failed
error: 'Unknown MySQL server host 'root@localhost' (1)'
Check that mysqld is running on root@localhost and that the port is 3306.
You can check this by doing 'telnet root@localhost 3306'[/B]

Any help would be greatly appreciated.
-Will

---

### Post by evilghost on 2006-07-03
Do it as sudo or su.

---

### Post by wjc on 2006-07-03
Thanks for the quick response.  I tried that, but unfortunately I got the same results as before.

---

### Post by evilghost on 2006-07-03
Is mysql listening on TCP 3306?

You could:

```

telnet localhost 3306

```

or

```

netstat -apvtu|grep -i 3306

```

to see.

---

### Post by wjc on 2006-07-03
Yes, I can telnet in.  This might help, I ran a query against the 'User' table and it contains 3 user accounts.  
HOST          USER                     PASSWORD
localhost      root                      xxxxxxxxxxx
ubuntu01     root
localhost      debian-sys-maint     xxxxxxxxxx

So I tried:  mysqladmin -h localhost -u ubuntu01 password XXXX
and: mysqladmin -h localhost -u root root@ubuntu01 password XXXX

and i got the following:
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root@ubuntu01'@'localhost' (using password: NO)'

---

### Post by Daveyboy on 2006-07-04
I had a similar problem. Try this;

mysql -u root -p <enter>
should then prompt you for pswd.

---

### Post by Abhi Kalyan on 2006-11-04
> **wjc said:**
> I installed mySQL successfully and it appears to be running correctly.  However, when I try to set the 'root@localhost' password, it returns the following error (I've replaced the password I'm trying to give it with XXXX):

[B]xxx@ubuntu01:~$ mysqladmin -h localhost -u root password XXXX
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'[/B]

I've tried using "root@localhost"  and it returns another error:
[B]mysqladmin: connect to server at 'root@localhost' failed
error: 'Unknown MySQL server host 'root@localhost' (1)'
Check that mysqld is running on root@localhost and that the port is 3306.
You can check this by doing 'telnet root@localhost 3306'[/B]

Any help would be greatly appreciated.
-Will
MY GOD!
Guys i had a major time out with the proper syntax GRHHH!!!
exactly as i typed it atlast, does every comma and space matter so much, GRHHH!

SET Password = PASSWORD( 'sathyam' );

this i typed after logging into the mysql,
after loads of trying i found that me being so dumb had set my password to
"newrootsqlpassword"
Please laugh

Thank you guys You are wonderful
Love you all

---


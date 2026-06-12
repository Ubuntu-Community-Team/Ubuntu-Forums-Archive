---
title: "mysql problems"
date: 2008-06-30
forum: Server Platforms
---

### Post by jcr1 on 2008-06-30
Hi all,

I am trying to set up torrentflux as per the howto:

[http://ubuntuforums.org/showthread.php?t=268985&highlight=howto+torrentflux](http://ubuntuforums.org/showthread.php?t=268985&highlight=howto+torrentflux)

i have installed the seperate packages and got as far as testing php works. But now i am at the stage where it says to add a password...

when i run the command I get :

```
serveradmin@jcrserver:~$ mysqladmin -u root password newpassword
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

```

Don't know what I am doing tbh... I was hoping just following the howto step by step I would be ok.

BTW I am trying to set this up remotely through ssh in a terminal... if it matters.

---

### Post by dynamethod on 2008-06-30
try:

mysql -u root -p


then it will ask you for your password, type it in and see what happens

---

### Post by jcr1 on 2008-07-01
ok will try that...thanks!

god I wish putty would work from my work computer!! have to wait to get home tonight. things take a very long way this way!

---


---
title: "Change MySQL root password...."
date: 2006-05-12
forum: Server Platforms
---

### Post by und3rtug4 on 2006-05-12
Hi there!!

I was setting one mysql server, and when i typed :

mysqladmin -u root password "desired password"

...i enter the wrong one!!

My question is:

How do I change the root password to the one i want, in order to access my mysql server? ](*,) 

Kind regards

---

### Post by und3rtug4 on 2006-05-12
i try with:

mysqladmin -u root password "new password"

... and I get:

mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'root@localhost' (Using password: NO)'

:confused: :confused: :confused:

---

### Post by und3rtug4 on 2006-05-12
Well, i fixed the problem....

since i had to install phpmyadmin, i log in with it and changed the password!;) 

But that was not the end of the quest, because i still wanna know how to change it on the command line!

If i'm already logged on, just typing SET PASSWORD = PASSWORD( 'new password' )  would do it!

But imagine the previous scenario, but, i didnt remenber the password in order to log in!!!
What would I have to do to change the password?? :confused: :confused:

Props to all :mrgreen: :mrgreen:

---

### Post by Socratez on 2006-05-15
I ran into this the other day and I had to do a little quick fix .... I found this on the net somewhere

shell> kill `cat /mysql-data-directory/hostname.pid`

shell> mysqladmin -u root password 'mynewpassword'

shell> mysqladmin -h hostname flush-privileges

[B]Alternatively, you can set the new password using the mysql client: 

[/B] 1. Take down and restart mysqld with the --skip-grant-tables           option as described above. 
2. Connect to the mysqld server with:           shell> mysql -u root mysql
3. Issue the following commands in the mysql client:[FONT=monospace]
[/FONT]mysql> UPDATE user SET Password=PASSWORD('mynewpassword')    ->             WHERE User='root';[FONT=monospace]

4. [/FONT]mysql> FLUSH PRIVILEGES;

After this, you should be able to connect using the new password. You can now stop mysqld and restart it normally.

---

### Post by Abhi Kalyan on 2006-11-04
> **und3rtug4 said:**
> Hi there!!

I was setting one mysql server, and when i typed :

mysqladmin -u root password "desired password"

...i enter the wrong one!!

My question is:

How do I change the root password to the one i want, in order to access my mysql server? ](*,) 

Kind regards
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

### Post by felixnine on 2008-01-01
i did this:

```
sudo dpkg-reconfigure mysql-server-5.0
```

---

### Post by generic_idea_machine on 2008-05-01
:KS> **felixnine said:**
> i did this:

```
sudo dpkg-reconfigure mysql-server-5.0
```

---


---
title: "problem installing Opencart on Ubuntu server 9.04"
date: 2009-09-14
forum: Server Platforms
---

### Post by metalf8801 on 2009-09-14
I've been trying to install opencart_v1.3.2 on Ubuntu server 9.04 but I can't get past step 2. I have been trouble shooting for quite awhile.

Here's what's happening 
Everything on step 1 has a green check or it says writeable which I believe is how it should look if not please tell me. I have created a blank mysql database called cart and I have created a mysql user with All Privileges called daniel. So when I get to step 2 I fill everything in like this

Database Host: localhost [COLOR="Red"]I have also trying using 127.0.0.1 and the servers ip address from another computer[/COLOR]
*User: daniel
Password: [COLOR="Red"]I have set up a mysql users with and without a password[/COLOR]
*Database Name: cart
Database Prefix: [COLOR="Red"]I've just been leaving this blank
[/COLOR]
2. Please enter a username and password for the administration.
*Username: admin        [COLOR="Red"]I've tried lots of different names[/COLOR]
*Password: password     [COLOR="Red"]and lots of different password[/COLOR]
*E-Mail: [email]myemail@yahoo.com[/email] [COLOR="Red"]could it be a problem that I'm using a yahoo email address and not a local email server?
[/COLOR]

after I that I always get this message 
> Error: Could not connect to the database please make sure the database server, username and password is correct!

If anyone could help that would be great
thank you
Dan

---

### Post by abaden on 2009-09-14
Have you installed phpmyadmin? You can easily add it with
```
sudo apt-get install phpmyadmin
```

It's a very nifty software package that allows you to graphically manage MySQL databases and users, and the privileges associated with each. I suspect that's where your problem is. Once you've installed it via apt-get you can access is at [http://localhost/phpmyadmin](http://localhost/phpmyadmin) 

As far as everything else goes you should not be having any problems. Your hostname is indeed localhost (regardless of where you are installing some - the hostname is relative to the location of the web server, so if your web server and mysql server are on the same host then localhost is correct), and your user and database name should be acceptable. Make sure that your user is actually granted the requested privileges on the database - again phpmyadmin can help you with this.

Also, your email shouldn't matter, since the setup is failing on database creation. The email is just for forgotten passwords, etc.


Alex

---

### Post by metalf8801 on 2009-09-20
it turns out all I had to do was to enter 
sudo su 
on the server before I installed opencart

---


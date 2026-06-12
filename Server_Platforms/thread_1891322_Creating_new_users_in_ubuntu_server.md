---
title: "Creating new users in ubuntu server"
date: 2011-12-05
forum: Server Platforms
---

### Post by DanHorniblow on 2011-12-05
Hi, I want to be able to create a new user on the server through a web interface.

This is for a hosting solution I am creating for my work.

Is it possible to do this in php or something similar?

Many thanks Dan

---

### Post by CharlesA on 2011-12-05
Webmin would work, I suppose. I just ssh in and create the users that way, but that's just me.

---

### Post by 2F4U on 2011-12-05
Besides webmin, here is another solution:

[https://help.ubuntu.com/10.04/serverguide/C/ebox.html](https://help.ubuntu.com/10.04/serverguide/C/ebox.html)

---

### Post by DanHorniblow on 2011-12-05
Hi, Thanks for the reply

This process needs to be automated, I am creating a hosting system where a student, at the college where I work, can navigate to a web server and create an account.

This would then give them FTP access because proftpd is installed, and will also create them a MySQL account.

All that I need to do after is work out how to create a symlink from their home directory to "/var/www/".

Any Ideas?

---

### Post by CharlesA on 2011-12-05
I don't know how you'd be able to do that without having them run a script themselves.

I know there is such a thing as a webshell, but that would be a huge security risk.

EDIT: I guess you could have the student update a database and have a script that pulls that data from the db. Not sure how to do that though.

---

### Post by DanHorniblow on 2011-12-05
> **CharlesA said:**
> I don't know how you'd be able to do that without having them run a script themselves.

I know there is such a thing as a webshell, but that would be a huge security risk.

Ok, ill do some more research.

Is there a way of almost forwarding variables from php to bash, because then I could write a simple bash script which creates an account with the name and password the user provided.

The whole point of this new system is to eliminate the need of admin staff to create each user account on the server.

Cheers

---

### Post by CharlesA on 2011-12-05
> **DanHorniblow said:**
> Ok, ill do some more research.

Is there a way of almost forwarding variables from php to bash, because then I could write a simple bash script which creates an account with the name and password the user provided.

The whole point of this new system is to eliminate the need of admin staff to create each user account on the server.

Cheers

I think you can do that, but it would be a lot of work as you would need to sanitize the input to ensure that your box doesn't get owned.

In the end, you'd have to weigh the risks. How many students register per day?

---

### Post by drdos2006 on 2011-12-05
You would have to design a user interface with a database [http://dabodev.com/](http://dabodev.com/)

regards

---

### Post by DanHorniblow on 2011-12-05
I have already created a system written in php and html with a MySQL backend.

It allows students to register, when a student registers a DB entry is made of their Student number (username), First name, last name and the date they registered.

An admin is then required to login and approve the students, this is because the system will be externally assessable and anyone can register.

Once a student is approved they can get to a page which will give them their FTP login details and MySQL login details.

I would like to be able to write either a bash script and call it from php in the admin page or code php to:

[LIST]
[*]Create a local user on the server with a home directory for FTP access
[*]Symlink that home directory to "/var/www/"
[*]Create a MySQL user which allows students to create multiple databases of there own for example "student1" could have two DBs named "student1_DB1" and "student1_DB2".
[/LIST]

Not that many students would register every day, but about 200 - 250 maybe more at the start of a year or semester.

Students would be administering their databases via phpmyadmin.

Any more information or advice would be brilliant.

---

### Post by CharlesA on 2011-12-05
Well if they are written to a database, you could just query the db and pass on that info to a bash script.

Might be a bit tricky to code since you would have to make sure the value returned from the db is what you expect.

---


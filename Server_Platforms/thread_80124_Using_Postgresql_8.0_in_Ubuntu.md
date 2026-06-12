---
title: "Using Postgresql 8.0 in Ubuntu?"
date: 2005-10-21
forum: Server Platforms
---

### Post by OneSeventeen on 2005-10-21
I installed postgresql 8 using apt-get, and it seems to have worked, but I don't really know what to do from here.

pg_ctl returns "command not found" and each time I try to create a user it says:
"createuser: could not connect to database template1: FATAL:  user "root" does not exist"

I was logged in as root when doing this, trying to create a user named "test".

Do I need to create a database, or log in some other way first before creating users?  And do I need to create a linux user account for each of my postgres user accounts?

Also, when I try to connect from my PC it asks me if I'm sure postgresql is really running at the IP I specified.  I'm sure its running, now if it is allowing stuff, I don't know.

I told pg_hba.conf to use md5 on all users coming from my IP, but since I don't have pg_ctl on my machine for some reason, I can't restart the server to see if that is it.

My logs just show that there were "incomplete startup packest", and there were no signs of attempts at a remote connection.


It may also be of interest that I installed most of my packages using one apt-get install line, meaning apache2, php5, postgresql, mysql4, and quite a few apache and php modules.

Do I need to reinstall stuff?

**EDIT:**
My goal is by the end of this to be able to create 2 users, one for reading and writing, and one for administering and creating databases.  I want both users to be able to log in from my machine (which has a static IP) to the server, using PGAdminIII, and I also want to be able to use the reading/writing user with PHP5.

As it stands, the only customization I've done is a little apache2.conf customizing, pg_hba.conf customizing, and network/interfaces customizing.

---

### Post by LordHunter317 on 2005-10-21
[QUOTE=OneSeventeen]I installed postgresql 8 using apt-get, and it seems to have worked, but I don't really know what to do from here.

pg_ctl returns "command not found" and each time I try to create a user it says:
"createuser: could not connect to database template1: FATAL:  user "root" does not exist"

I was logged in as root when doing this, trying to create a user named "test".[/quote]Just like all other databases:
**Database users aren't the same as system users**.  Just because you're logged in as root at the console means **nothing**.  

The only account PostgreSQL ships with is the database superuser, "postgres".  He also has a system account, named "postgres".  

Because of the default authentication setup, the only way to run super-user database commands is do to this:```
sudo su postgres -c "command"
```

>  And do I need to create a linux user account for each of my postgres user accounts?No.

> Also, when I try to connect from my PC it asks me if I'm sure postgresql is really running at the IP I specified.Your PC is remote?   PostgreSQL only allows TCP/IP connections from localhost by default.

> but since I don't have pg_ctl on my machine for some reason, I can't restart the server to see if that is it.You do, and that's not how you restart the server.  Use /etc/init.d/postgresql

> My goal is by the end of this to be able to create 2 users, one for reading and writing,Why?  You should create users based on the applications, and what needs they have.

>  and one for administering and creating databases.Use the existing postgres account, unless you have a very good reason not to.

---

### Post by theQmaster on 2005-10-22
It's available ? Shut!

I had an application on windows 8.0 and I had to move backward when I change  d from windows to ubuntu.

Any easy way to upgrade ? Or I have to migrate the schema and data to the new dbserver ?

theQMaster
Affordable Stock Photography
[http://www.goodstockimages.com](http://www.goodstockimages.com)

---

### Post by OneSeventeen on 2005-10-22
LordHunter,
I am creating the first 2 users for my first application, and I figured if someone showed me how to get started, then I would be able to repeat/modify the steps for each application I make.

And thanks for clarifying a lot of the little things up, I'm still confused on a few parts, but we'll see what happens when I su to postgres.

The reason I want a superuser other than postgres, is the only way I know to access the postgres account is by SSHing in, and doing the sudo su postgres trick, whereas I would like to administer my database from my work PC via PGAdminIII, because I am still a slave to at least some sort of GUI.  (As my SQL skils increase, I look forward to comand-lineing it, but until then I need to be able to create databases and users with something more graphical, even if it is just phppgadmin (but I would prefer pgadmin running on my windows machine)

I am trying to get away from MySQL in favor of PostgreSQL due to its more advanced features, but with those features comes a lot more responsibility and a lot more steps to take getting a good/secure database up and running, so any help is appreciated!

I'll try creating users again, and I'll post back with more questions I'm sure!

---

### Post by LordHunter317 on 2005-10-22
[QUOTE=OneSeventeen]The reason I want a superuser other than postgres, is the only way I know to access the postgres account is by SSHing in, and doing the sudo su postgres trick, whereas I would like to administer my database from my work PC via PGAdminIII, because I am still a slave to at least some sort of GUI.[/quote]I highly recommend you create an account for yourself and give it a DB password.  Make it an owner of whatever databases you need to work on, however, don't make a a true superuser.  Don't give it the ability to create users or databases.

While that makes those two tasks a PITA, niether are very common, and it gives a modicum of extra protection.

---

### Post by OneSeventeen on 2005-10-24
Okay, I have created a user by su'ing to postgres, then issuing the createuser command.

It said it worked fine.  :)

Now, I just need to figure out how to connect to it.  PGAdminIII gives me the error:
> could not connect to server: Connection refused
Is the server running on host "129.24.210.32" and accepting TCP/IP connections on port 5432?

Any tips?

I'm connecting remotely from my own machine that has a static IP, and my pg_hba.conf file has the following line:
```
host    all         all         my.ip.add.ress        md5
```

How can I tell if my server is allowing stuff in via port 5432?  And how can I be sure postmaster is running?  Do I need to restart postmaster after changing the pg_hba.conf file?

help?

---

### Post by LordHunter317 on 2005-10-24
Yes, you must be restart.  You gave the user a password, right?

Also, unless you setup SSL, everything will be cleartext on the wire, so make sure you're on a trusted network.

---

### Post by OneSeventeen on 2005-10-24
Well, I actually have the SSL certificate that was given to me back when this server was a debian server (same domain and same IP), could I reinstall that certificate without having to bother thawte as long as it is the same domain name and IP?

Thanks for letting me know that though, I don't know why I thought it would be encrypted.


I'll restart the server and see if that helps.

---

### Post by OneSeventeen on 2005-10-24
Okay, restarted the server, and still no go.  I don't even have a log file for pg_hba or anything (which I though Postgres makes when users attempt to connect)

Is there a way to see if postgresql is listening to the TCP/IP port?

---

### Post by LordHunter317 on 2005-10-24
[QUOTE=OneSeventeen]I don't even have a log file for pg_hba or anything (which I though Postgres makes when users attempt to connect)[/quote]The server logs in /var/log/postgresql.

> Is there a way to see if postgresql is listening to the TCP/IP port?sudo netstat -pln, but it ought to be.  It may have be artifically limited to localhost, however.

---

### Post by OneSeventeen on 2005-10-24
It was initially limited to localhost.

I told it to listen to my static IP, and it then appeared in netstat showing it was listening, but I still can't connect remotely for some reason.

Could this have something to do with going through a wireless router?  (i.e. do I need to forward some ports on my machine at home?)

---

### Post by LordHunter317 on 2005-10-25
Perhaps.  I would personally tell to not listen to any IP, so it listens on every interface on that box.

---

### Post by OneSeventeen on 2005-10-25
Okay, switching from listening to my IP to listening to '*' made it work, and after fixing some pg_hba.conf errors, I got it to work!

Now, the big question is:
Is it possible to limit remote access to a specific subnet rather than a specific IP?

It would be nice to just have it so only computers in my subnet at work can log in via pgAdmin.  (all the computers that need to access it are on the same subnet as the server, if that makes a difference)

---

### Post by syslink on 2005-12-04
guys where exactly is the pg_hba.conf file? I cant seemt to find nor the postgresql data directory..

---

### Post by penguinman007 on 2005-12-06
I installed everything with the letters postgresql in it from the synaptic package manager.

Of course no icons were added to my desktop or to my programs group.

But I discovered that if I type postmaster I will be actually starting the postgres database server.

However when I type postmaster nothing infact happens.

So, anyway, let me know when all these problems are sorted out.

---


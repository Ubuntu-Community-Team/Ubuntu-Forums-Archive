---
title: "Trying to start mySQL server running but i fail."
date: 2011-10-05
forum: Server Platforms
---

### Post by Deicider on 2011-10-05
I installed mySQL client and server, now am trying to run the server, i do:

/etc/rc.d/init.d/mysqld start 

as the site suggests but i get "no such file or directory".

What do i do?

---

### Post by Dangertux on 2011-10-05
Try this

```

sudo /etc/init.d/mysql start

```

That should do it.

---

### Post by Deicider on 2011-10-05
> **Dangertux said:**
> Try this

```

sudo /etc/init.d/mysql start

```

That should do it.

I try this and i get:

Rather than invoking init scripts through /etc/init.d, use the service( 8 )
utility, e.g. service mysql start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start ( 8 ) utility, e.g. start mysql




Am not sure whats that.

---

### Post by Deicider on 2011-10-05
anyone?

---

### Post by SeijiSensei on 2011-10-05
Use "sudo service mysql start" instead.

---

### Post by Deicider on 2011-10-06
> Use "sudo service mysql start" instead.

Did that and i got:
start: Job is already running: mysql


Which is weird, anyway.

I tried to set a pass with:
```
mysqladmin -u root password newpass
```

And i got:
```
error:'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
```

---

### Post by Deicider on 2011-10-06
would a format help? cause i haven't done one in years and i guess things got messy in the system files.

---

### Post by DavidBeijer on 2011-10-06
have you checked if that socket actually exists? You should see it with 
```

ls /var/run/mysqld

```

You could also try reinstalling or update your mysql install via apt.

---

### Post by Ryan Dwyer on 2011-10-06
I'm guessing you didn't install MySQL from a repository but from downloading a .deb file or something.

Remove everything you've done relating to installing MySQL, then run

```
sudo apt-get install mysql-server
```

It should install MySQL from the repository, prompt you to set a MySQL root password and start it running for you.

---

### Post by Deicider on 2011-10-06
i used the apt way, i removed it and installed several times, same thing.

Also in 'ls /var/run/mysqld'

There is nothing, its empty.
Why is that?

---

### Post by SeijiSensei on 2011-10-06
Try

sudo service mysql stop
sudo service mysql start

Any better?

---

### Post by Deicider on 2011-10-06
> **SeijiSensei said:**
> Try

sudo service mysql stop
sudo service mysql start

Any better?

I run stop, and it works nicely, but when i start it executes forever something, like when you're typing something to execute and it waits till it gets done, on the standby.
I can't type anything, i can only shift+z it.

Though i opened another terminal and tried to set password and it still can't find the sock.

I read some tutorials again and it seems i dont have a config file that i should have.

Anyone can paste the sample here?

---

### Post by Deicider on 2011-10-06
I also tried through different MySQL GUI programs to connect to the server and it gives messages like:
 
"/var/run/mysqld/mysqld.sock( 2 )"

---

### Post by jazzon on 2011-10-06
version 10.04 the config file is in /etc/mysql/  and should be called my.cnf .  The attached file is basically an out-of the box config file.  I renamed it to add .txt to make sure it would upload ok.  Also are trying to use it remotely or at the keyboard?

---

### Post by Deicider on 2011-10-07
> **jazzon said:**
> version 10.04 the config file is in /etc/mysql/  and should be called my.cnf .  The attached file is basically an out-of the box config file.  I renamed it to add .txt to make sure it would upload ok.  Also are trying to use it remotely or at the keyboard?

I did that, i can start and stop the server but if i try to do anything else it says "access denied for user 'root'@'localhost'".

Remote or keyboard? what do you mean?
The server is on my laptop, a local server i suppose.

---

### Post by Deicider on 2011-10-07
Now that i have the config file, i removed client and server and installed them again.

Still the same, no matter i do, through terminal or GUI it ALWAYS says :

 Access denied for user root@localhost (using password yes/no)

Even if its a simple connect, anything.
I tried my password, i tried without password, with root, user etc etc, i tried everything, it seems that i can't access the server no matter what, only start/stop it.

---

### Post by Deicider on 2011-10-07
Gawd, its been 2 days of search on the internet with no results, i'll be using windows for this one since its working perfectly there, linux while its fast and virus free has the habit of creating problems where there shouldn't exist.

Anyway, thnx for your input guys! ;D

---


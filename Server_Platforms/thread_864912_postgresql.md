---
title: "postgresql"
date: 2008-07-20
forum: Server Platforms
---

### Post by xyious on 2008-07-20
hi !

i have had this problem before, several times....

i tried to change the configuration files to where it would work and it never did. so i went apt-get remove --purge postgresql, and apt-get autoremove.
then i deleted the configuration files and reinstalled postgresql. needless to say the configuration files are still gone. 
how can i fix that ?

---

### Post by windependence on 2008-07-20
They're probably there, just in a different location. Also, postgres writes the conf file to the data directory when you initialize the database.

Try this:

```
sudo find / -name postgresql.conf
```


-Tim

---

### Post by xyious on 2008-07-20
xyious@Melanie:/etc$ sudo find / -name postgresql.conf
[sudo] password for xyious:
xyious@Melanie:/etc$


no config file....

---

### Post by windependence on 2008-07-20
Do you have a /var/lib/postgresql/data  directory?

-Tim

---

### Post by xyious on 2008-07-20
this might also help ....

xyious@Melanie:/etc$ sudo /etc/init.d/postgresql-8.2 status
[sudo] password for xyious:
Version Cluster   Port Status Owner    Data directory                     Log file
xyious@Melanie:/etc$ sudo /etc/init.d/postgresql-8.2 start
xyious@Melanie:/etc$ sudo /etc/init.d/postgresql-8.2 restart
xyious@Melanie:/etc$

---

### Post by xyious on 2008-07-20
> **windependence said:**
> Do you have a /var/lib/postgresql/data  directory?

-Tim

nope, i do have a /var/lib/postgresql directory, but it's empty.

---

### Post by windependence on 2008-07-20
Could be here also: 

/etc/postgresql/8.2/main/postgresql.conf

At any rate it may not matter where you put it, although the defualt is the data directory /var/lib/postgresql/data. You can start postgres by specifying the data directory location. It can literally be anywhere.

I'm looking for a default config file for you. You also have to initialize the database before you do anything. Do you know how to do that?

-Tim

---

### Post by xyious on 2008-07-20
> **windependence said:**
> Could be here also: 

/etc/postgresql/8.2/main/postgresql.conf

At any rate it may not matter where you put it, although the defualt is the data directory /var/lib/postgresql/data. You can start postgres by specifying the data directory location. It can literally be anywhere.

I'm looking for a default config file for you. You also have to initialize the database before you do anything. Do you know how to do that?

-Tim

i don't have an /etc/postgresql directory, since i deleted it before the reinstall....
and i have not worked with postgre before, i have some experience with mysql tho. so no i don't know how to initialize the database.

---

### Post by windependence on 2008-07-20
Don't worry about the directory, it should be created during the install. First, you probably want to uninstall everything cleanly. There are commands to do this that will completely clean up your install so we can do a fresh install. 

Postrgesql is a great database, on par with Oracle. Good choice. Fortunately, I have lots of experience with it, but mostly on BSD. I am sure I can help you.

We need to know how did you install it and uninstall it. Did you use Aptitude (apt-get)? Once we know how you installed it, we can tell you how to clean up so we can do a fresh, good install, and then I can walk you through getting it set up. Let me know, but don't try to uninstall yourself, wait until I give you the correct command.

-Tim

---

### Post by xyious on 2008-07-20
i installed it with apt-get install postgresql
then i took a lot of time trying to figure out how to set the configuration correctly and failed (mostly in /etc/postgresql/....
then i uninstalled it with apt-get remove postgresql.
took a bit of time to reinstall and uninstall to get the settings back the way they were, failed.
so then i went with apt-get remove --purge postgresql, then apt-get autoremove.
then i deleted the /etc/postgresql* directories and some other postgresql directories.
then i installed with apt-get install postgresql, but the /etc/postgresql directory wasn't recreated.
that's when i wrote my first post, it's unchanged since then.

---

### Post by windependence on 2008-07-20
OK then. Try:

```
sudo dpkg -P postgresql
```

If that doesn't work, then:

```
sudo aptitude purge postgresql
```

Let me know how that works out.

-Tim

---

### Post by xyious on 2008-07-20
the first one did work, however i've done the second one as well, also successful.
now, should i reinstall ?

---

### Post by windependence on 2008-07-20
Yep now I would do a fresh install. I usually don't recommend rebooting Linux or Unix but in this case I would before installing.

-Tim

---

### Post by xyious on 2008-07-20
no help, still the same.

---

### Post by windependence on 2008-07-21
OK, after you install, then try this:


```
sudo adduser postgres
mkdir /usr/local/pgsql/data
sudo chown postgres /usr/local/pgsql/data
sudo su - postgres
/usr/local/pgsql/bin/initdb -D /usr/local/pgsql/data
/usr/local/pgsql/bin/postgres -D /usr/local/pgsql/data >logfile 2>&1 &
/usr/local/pgsql/bin/createdb test
/usr/local/pgsql/bin/psql test
```

Post any errors you get here and we'll go from there. If you have the time, I will help you when I am here. :)

-Tim

---

### Post by xyious on 2008-07-21
i've reinstalled postgre, then installed the thing from the sources, i'm done till after the line below.

> **windependence said:**
> 
/usr/local/pgsql/bin/initdb -D /usr/local/pgsql/data


the rest of em i haven't done because i want to get the /etc/init.d/postgresql-8.2 script to work, in case the computer ever crashed.

---

### Post by windependence on 2008-07-21
Well you should set up the server first and test it, then we can get the start at boot thing working, it's easy. the script has to reference the correct directory in which the database resides, in this case /usr/local/pgsql/data. Sometimes Postgres installs things in weird places but we can figure that out. ;)

-Tim

---

### Post by xyious on 2008-07-28
just wanted to let you know that i made it work, finally.
took me so long mostly for a lack of time....

still haven't got the init script to work, however, not sure if i'm gonna keep trying. if i had the time i definitely would.

---


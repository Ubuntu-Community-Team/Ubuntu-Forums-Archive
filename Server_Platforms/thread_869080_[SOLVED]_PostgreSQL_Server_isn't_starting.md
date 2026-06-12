---
title: "[SOLVED] PostgreSQL Server isn't starting"
date: 2008-07-24
forum: Server Platforms
---

### Post by Dr Small on 2008-07-24
I installed postgresql, postgresql-common and postgresql-8.2. I then went to run:
```
root@mycroft:/home/drsmall# /etc/init.d/postgresql-8.2 start
 * Starting PostgreSQL 8.2 database server    
```

Everything looked like it was starting, but if I run:
```
root@mycroft:/home/drsmall# psql
psql: could not connect to server: No such file or directory
	Is the server running locally and accepting
	connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?

```

Also, if I run:
```
root@mycroft:/home/drsmall# /etc/init.d/postgresql-8.2 status
Use of uninitialized value in getpwuid at /usr/bin/pg_lsclusters line 28.
Version Cluster   Port Status Owner    Data directory                     Log file
8.2     main      5432 down   root     /var/lib/postgresql/8.2/main       /var/log/postgresql/postgresql-8.2-main.log

```

I am really stumped at why it won't start, and I am not getting any errors. Can someone please give me a hint?

I need to get my PostgreSQL server up so I can get Openfire running.

Thanks,
Dr Small

---

### Post by k_grdn on 2008-07-24
Hi,

Do you have a postgres user on your system?


Possibly getpwuid is looking in /etc/passwd for the uid of a user that does not exist, or could be cause your root.


Try creating the postgres user, also check pg_hba.conf to make sure your accepting connections from the local host, also clarify which interfaces postgresql is listening on after successful startup.

Also sudo su - postgres if user exists you must connect with this user.

Try createdb test; psql test (as postgres)

Use netstat to verify and connect to the listening address.


How did you install postgres?

If manually have you created the initial database?


Regards,


k_grdn

---

### Post by windependence on 2008-07-24
You have to start it by specifying the data directory, OR set the environment variable for it.

Did you initialize the database?

```
$ /usr/local/pgsql/bin/initdb -D /usr/local/pgsql/data
```

The -D option in the previous command is the location where the data will be stored. This location can also be set with the PGDATA environment variable. If you have set PGDATA, the -D option is unnecessary. If you would like to use a different directory to hold these data files, make sure the postgres user account can write to that directory.

To start postgresql in the foreground (probably not what you want:

```
$ /usr/local/pgsql/bin/postmaster -D /usr/local/pgsql/data'
```

To start it in the backgound:

```
$ /usr/local/pgsql/bin/pg_ctl -D /usr/local/pgsql/data -l /tmp/pgsql.log start

```

There also should be a startup script out there so you can use pgctl start.

```
pgctl -D /usr/local/pgsql/data start
```

-Tim

---

### Post by Dr Small on 2008-07-24
How did I install it?
```
sudo apt-get install postgresql-common postgresql-8.2
```

Do I have the postgres user on my system?
Yes. It was created as soon as postgresql-8.2 was installed. Here is the entry from /etc/passwd:
```
postgres:x:105:113:PostgreSQL administrator,,,:/var/lib/postgresql:/bin/bash
```

Running:
```
sudo /etc/init.d/postgresql-8.2 start
```
Still does not start the postgresql server.

How am I checking? By using:
```
ps aux | grep postgresql
```

I copied the /etc/postgresql/8.2/main/ directory (and contents) from my previous working state, to this system, so I thought I could keep the settings.

netstat does not show postgresql running either.

Running:
```
sudo su - postgres
```
Logs me in as the postgres user. Then, running:
```
createdb test; psql test
```
Outputs to:
```
createdb: could not connect to database postgres: could not connect to server: No such file or directory
	Is the server running locally and accepting
	connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?
psql: could not connect to server: No such file or directory
	Is the server running locally and accepting
	connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?

```

Also, on a sidenote, every command that you mentioned, windependence, did not work. Maybe I am still missing something that I should have installed. I don't know.

Dr Small

---

### Post by windependence on 2008-07-25
Hmmm... I know your experiance level is at or above mine but I ran a message board on pgsql for 3 or 4 years so I have some experience. This IS really baffling. The biggest problem I had was realizing that to get it to work I always had to specify the data directory in the start command. Mine was even harder because it was chrooted. Let me think about this and see if I have some more ideas for you. 

What were the errors you got when trying those commands? Same ones as before?

-Tim

---

### Post by Dr Small on 2008-07-25
Sorry for not mentioning those errors last time.

Basically. the files don't exist:
```
/usr/local/pgsql/bin/initdb -D /usr/local/pgsql/data
-bash: /usr/local/pgsql/bin/initdb: No such file or directory

/usr/local/pgsql/bin/postmaster -D /usr/local/pgsql/data
-bash: /usr/local/pgsql/bin/postmaster: No such file or directory

/usr/local/pgsql/bin/pg_ctl -D /usr/local/pgsql/data -l /tmp/pgsql.log start
-bash: /usr/local/pgsql/bin/pg_ctl: No such file or directory

pgctl -D /usr/local/pgsql/data start
-bash: pgctl: command not found
```

Like I mentioned before, I think I am missing some packages or something here, because it looks like alot of stuff is missing.

Dr Small

---

### Post by k_grdn on 2008-07-25
Hi,

You will find the binaries required to initialize the DB etc.. in:

/usr/lib/postgresql/8.3/bin

dpkg -L postgresql-8.3 will give you the location of all related files etc...

Set the bin PATH for postgres and try initilaizing the DB, sure when installing from apt your prompted to perform this action, did you decline?  The DB would have been created in /var/lib/postgresql/8.3/main.  Also necessary startup script would have been created in init.d.
 
Regards,

K_grdn

---

### Post by Dr Small on 2008-07-25
Ok, so here's what I have did now, and the outcome of it:
```
sudo mkdir -p /usr/local/pgsql/data
sudo chown -R postgres:postgres /usr/local/pgsql/
sudo su - posgresql
cd /usr/lib/postgresql/8.2/bin/
./initdb -D /usr/local/pgsql/data
./postgres -D /usr/local/pgsql/data
```

The server then starts in the foreground of my terminal, so I opened another SSH session to the server, logged in as postgres and ran 'psql', and it worked.

Ok. Now my question is, how do I get this thing to work properly, without having to do this everytime? Rewrite the /etc/init.d/postgresql-8.2 init file, or is there a simplier way around this?

Thanks for all your help so far,
Dr Small

---

### Post by Dr Small on 2008-08-25
I finally sat down and rewrote the init.d file for postgresql, and I finally have it starting and stopping by this file correctly, as it should be.

PostgreSQL is finally working on my server. Woo-hoo!
Anyhow, here is the file:
```
#!/bin/sh -e

#################################
## Script rewriten by Dr Small ##
#################################

PGVER='8.2'
BINPATH="/usr/lib/postgresql/$PGVER/bin/"
PGUSER='postgres'
PGLOG='/tmp/pgsql.log'
PGDIR='/usr/local/pgsql/data'

start()
        {
cd $BINPATH
su $PGUSER -c "./pg_ctl -D $PGDIR -l $PGLOG start"
        }

stop()
        {
cd $BINPATH
su $PGUSER -c "./pg_ctl -D $PGDIR -l $PGLOG stop"
        }


case "$1" in
    start)
        start
        ;;
    stop)
        stop
        ;;
    restart)
        stop
        start
        ;;
    *)
        echo "Usage: $0 {start|stop|restart}"
        exit 1
        ;;
esac

exit 0
```

Thanks to everyone for their continual help which led me to be able to fix the problem in the end, (**ahem**, even though it was 4 weeks later (lazyiness on my part)).

Dr Small

---

### Post by BrnN8r on 2008-09-07
I had the same problem:
```

root@mycroft:/home/drsmall# /etc/init.d/postgresql-8.2 status
Use of uninitialized value in getpwuid at /usr/bin/pg_lsclusters line 28.
Version Cluster   Port Status Owner    Data directory                     Log file
8.2     main      5432 down   root     /var/lib/postgresql/8.2/main       /var/log/postgresql/postgresql-8.2-main.log
```

It's basically saying it can't find the default PGDATA directory /var/lib/postgresql/8.2/main. It may be easier to just create the default PGDATA directory and then initdb /var/lib/postgresql/8.2/main. This would mean you wouldn't have to rewrite the init.d script too.

---

### Post by Dr Small on 2008-09-07
> **BrnN8r said:**
> I had the same problem:
```

root@mycroft:/home/drsmall# /etc/init.d/postgresql-8.2 status
Use of uninitialized value in getpwuid at /usr/bin/pg_lsclusters line 28.
Version Cluster   Port Status Owner    Data directory                     Log file
8.2     main      5432 down   root     /var/lib/postgresql/8.2/main       /var/log/postgresql/postgresql-8.2-main.log
```

It's basically saying it can't find the default PGDATA directory /var/lib/postgresql/8.2/main. It may be easier to just create the default PGDATA directory and then initdb /var/lib/postgresql/8.2/main. This would mean you wouldn't have to rewrite the init.d script too.
Ah well. I'm not that smart. Thanks for sharing that though! :)

---

### Post by Hashimi on 2009-07-13
Hi 

When i run:

$ sudo /etc/init.d/postgresql-8.3 start

I have face with this message:

 * Starting PostgreSQL 8.3 database server                                        Error: /var/lib/postgresql/8.3/main is not accessible or does not exist
                                                                         [fail]

What can i do?

I also installed postgresql-8.4.0 but in init.d it is 8.3.

---

### Post by Hashimi on 2009-07-13
After i replace my init.d/postgresql-8.3 with Dr Small s modified version from first page; i get this message:

pg_ctl: another server might be running; trying to start server anyway
pg_ctl: could not start server
Examine the log output.

---

### Post by PrivateLifeOfPlants on 2009-11-26
Hi, The problem seems to be a broken dependency issue. I posted a solution to this issue in the following thread:

[http://ubuntuforums.org/showthread.php?p=8389411&posted=1#post8389411](http://ubuntuforums.org/showthread.php?p=8389411&posted=1#post8389411)

---


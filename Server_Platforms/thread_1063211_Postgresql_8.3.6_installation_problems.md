---
title: "Postgresql 8.3.6 installation problems"
date: 2009-02-07
forum: Server Platforms
---

### Post by EvanKroske on 2009-02-07
I'm trying to set up Django on my Linux, but when I try to install PostgreSQL, it says that it can't find readlines or xlib. First, it says it can't find readlines, then, when I tell it to ignore readlines, it says that it can't find xlib. It says it may be looking in the wrong directory, but I really don't know where it should be looking and how to make it look. Has anybody else had this problem and fixed it?

---

### Post by windependence on 2009-02-08
Are you trying to install from the GUI or command line. Try to apt-get the package from the command line. Post any screen shots here or cut and paste your terminal output. We can't help you without some more details.

-Tim

---

### Post by EvanKroske on 2009-02-08
First, I don't know how to install software from a GUI in linux. Second, here are my installation instructions from the readme file:
```

./configure
gmake
su
gmake install
adduser postgres
mkdir /usr/local/pgsql/data
chown postgres /usr/local/pgsql/data
su - postgres
/usr/local/pgsql/bin/initdb -D /usr/local/pgsql/data
/usr/local/pgsql/bin/postgres -D /usr/local/pgsql/data >logfile 2>&1 &
/usr/local/pgsql/bin/createdb test
/usr/local/pgsql/bin/psql test

```
I get all the errors on the very first step, ./configure. I know that the gmake command is no make, but it's irrelevant because the first step fails. Here's an exercpt of what I get when I run ./configure:
```

configure: error: readline library not found
If you have readline already installed, see config.log for details on the
failure.  It is possible the compiler isn't looking in the proper directory.
Use --without-readline to disable readline support.

```
When I tried skipping readline, I just got another error that would require another option. Since I don't know what readline or xlib does, I'd like to know so that I don't cripple my Postgresql installation. I don't know what apt-get does, but I'd like to find out.

---

### Post by windependence on 2009-02-09
[FONT=Arial]You're going to be better off installing from packages instead of compiling from source on Linux. If you build your own, you will have no package management and will eventually run into what we call "dependency hell". 

You can install the package by doing:

```
sudo apt-get install postgresql postgresql-client postgresql-contrib
```

Then if you want install the admin tool:

[/FONT]   [FONT=Arial]```
sudo apt-get install pgadmin3
```


[/FONT][FONT=Arial][SIZE=2]Once you get the packages installed, I can help you with the setup. Let me know how it goes.[/SIZE][/FONT][FONT=Arial]
[/FONT]
-Tim

---

### Post by mojohn on 2009-02-10
Hello Tim. I've just installed Postgresql per your instructions able, but when I try to create a database through pgAdminIII, I get the following error message:

[INDENT]Ident authentication failed

The server doesn't accept the current user: The server reports 
FATAL: Ident authentication failed for user "postgres" 

If this message appears, the pg_hba.conf entry found for your client / user / database combination is set to "ident" authentication. Some distributions, e.g. Debian, have this by default. To perform ident based authentication successfully, you need additional setup; see the PostgreSQL help for this. For a beginner, it might be more appropriate to use a different authentication method; MD5 encrypted passwords are a good choice, which can be configured by an entry in pg_hba.conf like this: 

[INDENT][/INDENT][COLOR="Blue"]host all all 192.168.0.0/24 md5 [/COLOR]

This example grants MD5 encrypted password access to all databases to all users on the private network 192.168.0.0/24. 

You can use the pg_hba.conf editor that is built into pgAdmin III to edit the pg_hba.conf configuration file. After changing pg_hba.conf, you need to trigger a server configuration reload using pg_ctl or by stopping and restarting the server process. 
[/INDENT]

The relevant lines from my pg_hba.conf file are as follows:

# Database administrative login by UNIX sockets
local   all         postgres                          ident sameuser

# TYPE  DATABASE    USER        CIDR-ADDRESS          METHOD

# "local" is for Unix domain socket connections only
local   all         all                               ident sameuser
# IPv4 local connections:
**host    all         all         127.0.0.1/32          md5**
# IPv6 local connections:
host    all         all         ::1/128               md5

It appears that the line in my error message is already contained in my conf file (bolded line), but still no new db. 

Any suggestions you have will be greatly appreciated!

Thanks, mojohn

---

### Post by EvanKroske on 2009-02-10
Okay, I've got the software installed, now how can manage it? When I typed in "pgadmin3" to try to start the admin program, I got this error:
```

Error: Unable to initialize gtk, is DISPLAY set properly?

```
So, how should I setup the software? I'm just looking for how to manage the databases and interact with the software itself; I don't need any info about SQL or how to use programming languages to interact with the database. That will come later, but, for now, I just need to know how to set it all up. Thanks!

---

### Post by windependence on 2009-02-11
Change the following line in your pg_hba.conf:

```
# Database administrative login by UNIX sockets
local   all         postgres                          ident sameuser

# TYPE  DATABASE    USER        CIDR-ADDRESS          METHOD

# "local" is for Unix domain socket connections only
**[COLOR=Red]local   all         all md5[/COLOR]**
# IPv4 local connections:
host    all         all         127.0.0.1/32          md5
# IPv6 local connections:
host    all         all         ::1/128               md5
```

Don't forget to restart postgresql

-Tim

---

### Post by EvanKroske on 2009-02-12
Sorry if I sound paranoid, but what does changing that line do? I know that it encodes the password as md5, but I also know that "md5" will replace "ident sameuser" for my config file. I'm not going to change anything until I know what it does; I don't want to have to keep pestering you for info every time I have a problem. XD

---


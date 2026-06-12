---
title: "Installaed U-Server 20.04 w/postgres, where is postgres? How to use it?"
date: 2020-09-07
forum: Server Platforms
---

### Post by Sceiron on 2020-09-07
Hi,
today I intstalled a fresh Ubuntu server 20.04 LTS. Here one could choose some options, and i chose "postgressql10" ( I even took a picture of it).,
Now that the server installation is compelte i cant locate the postgres-config files, no directory, cant log in to psql....

1. I thought i installed a server to host my databases and data, did I ?
2. Where are the files located?

I read that they would be in /etc if it was installed post Ubuntu server installation...

---

### Post by SeijiSensei on 2020-09-07
I just installed PostgreSQL 12 on 20.04 by running simply
```
sudo apt install postgresql
```

On Ubuntu, the installation lives in /var/lib/postgresql/[version]/main, so in your case it would be /var/lib/postgresql/10/main.  However the configuration files are in /etc/postgresql/[version]/main.

Do you have any experience with PostgreSQL? If not, the first problem you're likely to encounter is authentication. By default only the "postgres" user is authorized, and only on the local machine. (If you need network connectivity, you must edit both /etc/postgresql/10/main/postgresql.conf to change the "listen_addresses" parameter and /etc/postgresql/10/main/pg_hba.conf which governs the acceptable methods to connect.  That file is complicated; I'd read the documentation a couple of times before trying to change it.)

You should start by creating a database for yourself with these commands (in blue):
```

yourusername@host: $ [COLOR=blue]sudo su[/COLOR]
root@host: # [COLOR=blue]su postgres[/COLOR]
postgres@host: $ [COLOR=blue]createuser -s yourusername[/COLOR]
postgres@host: $ [COLOR=blue]exit[/COLOR]
root@host: # [COLOR=blue]exit[/COLOR]
yourusername@host: $ [COLOR=blue]createdb yourusername[/COLOR]

```
The "-s" switch makes yourusername a "superuser" that can create databases.

Now you have an empty database called "yourusername."  If you type "psql" at the prompt, you'll be connected to the server and using your database.  (If you create databases with other names, you'd use "psql databasename" to connect to them.) What you do after that depends on how your data is organized, whether you know SQL, etc.

---

### Post by Sceiron on 2020-09-07
Hey, and thanks!

I could not install the "defaukt package with *sudo apt install postgresql*
However, ubuntu told me to install the snap version (And that worked).
What is the snap version for postgres10 versus the non-snap version?

And why was i able to install this and not the other (stable or whatever it is) versioN?

And **no,** i have non experience with Postgres.

---

### Post by Sceiron on 2020-09-07
ok, so i reboote the server for the first time after installing ubuntu 20.04 server, and now i can run *sudo apt install postgresql*
I still wonder what the snap version is though. is it the current development relase? (Alfa beta something?)

---

### Post by SeijiSensei on 2020-09-07
[https://www.howtogeek.com/670084/what-you-need-to-know-about-snaps-on-ubuntu-20.04/](https://www.howtogeek.com/670084/what-you-need-to-know-about-snaps-on-ubuntu-20.04/)

I never use snaps.  I prefer to install entire packages with their dependencies as I always have.  

I don't know why you can't install the normal package with "sudo apt install postgresql". Maybe it has to do with differences between the server and desktop versions of Ubuntu? I installed PostgreSQL 12 on a Kubuntu 20.04 desktop machine.

If you haven't used PostgreSQL before, do you have any experience with SQL commands?  If not, you've got a steep learning curve ahead of you. One thing you can try is installing libreoffice-base which would give you a graphical front end that works with PostgreSQL.

For starters, try creating a table after connecting with psql using the CREATE TABLE command. That would look something like this:
```

CREATE TABLE mydata (name varchar, address1 varchar, address2 varchar, city varchar, state char(2), zip char(5));

```
(SQL commands are often capitalized in support documents, but the commands are actually case-insensitive.)  "Varchar" is a datatype that accepts text of varying length. The char(N) datatype requires text of N characters.

You can populate the table with data if the fields are separated by tabs with the command:
```

copy "mydata" (name,address1, address2, city, state, zip) from stdin;
Joe Blow[tab]Ten Happiness Lane[tab]Apartment 2[tab]Boston[tab]MA[tab]02112
etc.
\,

```
The "\." is an end-of-file delimiter.

You can then run a simple query like
```
SELECT * from mydata where state='MA';
```
which will return all records with MA as the state. Note that strings are enclosed in single quotes.

---

### Post by Sceiron on 2020-09-07
Thanks again :)
I know quite some SQL, but want to learn more about Postgre and dive into more administration aspects of databases.
Nice link for Snaps, thanks again !

---

### Post by Sceiron on 2020-09-08
By the way:
Do I not have to create the Database cluster with the *initdb* in addition to the commands you specified like this:
     ?
yourusername@host: $ sudo su
root@host: # su postgres
postgres@host: $ createuser -s yourusername
postgres@host: $ exit
root@host: # exit
yourusername@host: $ createdb yourusername

UPDATE: Nvm, it works now :)  Assuming that the *Database-Cluster* was created when installing postgres.

---

### Post by SeijiSensei on 2020-09-08
As you discovered, when you install the package the post-installation script runs initdb, starts the server, and tells systemd to run the server when the system is booted.

---


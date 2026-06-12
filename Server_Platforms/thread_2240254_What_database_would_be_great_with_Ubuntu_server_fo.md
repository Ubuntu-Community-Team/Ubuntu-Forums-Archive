---
title: "What database would be great with Ubuntu server for an office network?"
date: 2014-08-18
forum: Server Platforms
---

### Post by eakDev on 2014-08-18
Goo day guys,

I have been creating apps with python+pyside+sqlalchemy+sqlite. My problem now is that the data is getting bigger and it should be shared on a network. Basically what I want is to setup a server which can handle the data for a small office, say about 30 people.

This is my idea, please comment if its good or there would be better solutions.
1. Setup an ubuntu server
2. Install MySQL database which would store all data available for the network.
3. Configure the applications to connect to the database for storage and retreival of data. (Instead of using their own sqlite data)
4. Use another drive for backup.

Question: 
1. Would MySQL be good for a network database? I read PostgreSQL can easily be configured with Ubuntu Server, would that be good also?

---

### Post by nerdtron on 2014-08-19
If you are comfortable with the mysql syntax then it is a good choice. Lot's of documentation online an very reliable.

---

### Post by cj13579 on 2014-08-19
I would say that the back-end that you want to use will very much depend on what data types you are storing, the volume (number of transactions, size of tables, number of tables etc.) of data. For a detailed comparison of MySQL vs PostgreSQL have a look at [this]("https://www.digitalocean.com/community/tutorials/sqlite-vs-mysql-vs-postgresql-a-comparison-of-relational-database-management-systems") which may answer some/all of your questions for you.

However, what I would say is don't discount [the others out there]("http://en.wikipedia.org/wiki/List_of_relational_database_management_systems"). You may also want to look at Ingres or Apache Derby for example.

---

### Post by eakDev on 2014-08-19
Not yet an expert on mysql but I think I can learn it together with sqlalchemy. For Postgre i've used it for web before and it's really nice. What I'm troubled right now is more on the networking setup/layout I'm doing if it's good for the problem at hand.

---

### Post by nerdtron on 2014-08-19
MySQL is easy to setup for network access. On the server side, just edit the /etc/my.cf and set the bind address to listen to your IP block. On the client side, just set them to connect to the IP and port of the mysql server.

---

### Post by Sasha_Aderolop on 2014-08-21
I recommend you MySQL
As of Ubuntu 12.04, MySQL 5.5 is installed by default. Whilst this is 100% compatible with MySQL 5.1 should you need to install 5.1 (for example to be a slave to other MySQL 5.1 servers) you can install the mysql-server-5.1 package instead.

---

### Post by SeijiSensei on 2014-08-21
I'm more concerned about the application side myself.  What will they be written in?  If you use things like MS Access or Crystal Reports, you'll need to set up ODBC connectivity with the appropriate drivers on the client workstations.  Both [MySQL]("http://dev.mysql.com/downloads/connector/odbc/5.1.html") and [PostgreSQL]("http://www.postgresql.org/ftp/odbc/versions/") support ODBC.  I'm partial to the latter.  I only use MySQL when it's forced upon me by an application.  Otherwise I prefer the more standards-compliant PostgreSQL.  I also prefer a project that is not under the wing of Oracle.

Network configuration in Postgres takes place in the pg_hba.conf file located in the "data" subdirectory of the PG installation (usually /var/lib/pgsql/data).  I use a private network over OpenVPN to connect to my remote servers, so I just trust the entire private network subnet.  
```

# TYPE  DATABASE    USER        CIDR-ADDRESS          METHOD
host    all         all         10.1.1.0/24           trust
host    all         all         192.168.100.0/24      trust

```
However Postgres supports a wide variety of other network restrictions, and usernames/passwords of course.

If you write applications in LibreOffice Base, it has a native PostgreSQL driver which works well.

---

### Post by LHammonds on 2014-08-25
If you are creating web applications for about 30 users max, just about any database will work depending on any size limitations.  I have an ancient web application I wrote in 1998 (Active Server Pages...yeah, I know) that uses an MS Access database for the backend.  Even back then people said to stay away from MS Access for web applications because it is so connection-limited (20 max iirc).  However, because I wrote my application to only connect to the database when it needs to read/write and immediately close the connection, I never had a problem with it.  It started off as being used by just a handful of people but grew from 1 department use to just about every department at all locations across the US.  Granted, it was not an app people "sat in" all the time.  It was a submit-n-go ticket database.  I have companies that still actually use it to this day!

If I had to do it all over again today, I would use PHP + MySQL (or MariaDB or PostgreSQL).  To me, the database doesn't matter too much because I don't use db-specific features...I mainly use them like big spreadsheets for data entry (not literally).  So it does not really matter what backend I choose because I can make it work with any of them when talking about a web application communicating to the DB.

But like SeijiSensei said, if people plan on directly connecting to that database (e.g. ODBC) or using non-web apps like MS Access (connecting to MySQL via ODBC) or LibreOffice (connecting via ODBC), etc. you might need to adjust what DB you used because of it.

At my location, we have about 1 of every kind of major database out there mainly because the application demands it.  However, my generic database I used is MySQL for PHP web apps and MS Access (connecting to it via ODBC).  If I were to re-create this generic database again today, I would probably go with MariaDB (which is a fork of MySQL that remains open-source and community-driven...and it is designed to be a drop-in replacement for MySQL for compatibility with it)

LHammonds

---


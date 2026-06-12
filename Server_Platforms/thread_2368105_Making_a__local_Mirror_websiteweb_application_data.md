---
title: "Making a  local Mirror website/web application database"
date: 2017-08-07
forum: Server Platforms
---

### Post by webmiester on 2017-08-07
Hi guys,

I am not a real IT person.  I am a doctor.

Here's my scenario and question:  I am currently building a company system which will use an SQL database and a web-based application running on Apache.  So the web-based application will run locally on a server withinthe buidling and all the computers in my network will connect to it to run the application.  My dream is to setup a second computer which is a mirror for this server and it will have the same web-application and have its data updated at the same time as back-up in case the first computer goes down.  It is like RAID 1 except that it will work on 2 different computers instead of 2 different hard disks on 1 computer.  I think companies like google and facebook have these to spread the bandwidth needs accross multiple computers.  In case the first computer breaks down, the computers in the network will be redirected to the second computer which will have all the data and software there so that our system will work continuously.

What applications and steps do I need to achieve this?  Is this even possible?

Thanks

---

### Post by cariboo on 2017-08-07
This thread has nothing to do with 17.10 development, moved.

---

### Post by SeijiSensei on 2017-08-07
I'd start with the database side first.  Do you have a choice of SQL server software?  If so, I'd suggest PostgreSQL which is more enterprise-oriented than MySQL and has extensive "replication" procedures.  You can get a sense of the options available here:  [https://wiki.postgresql.org/wiki/Replication,_Clustering,_and_Connection_Pooling](https://wiki.postgresql.org/wiki/Replication,_Clustering,_and_Connection_Pooling)

If the application is written in PHP, you'll have no trouble using it to talk to a PostgreSQL server.  Or you can use the abstraction layer available [here](http://php.net/manual/en/intro.pdo.php).  PostgreSQL comes with an [ODBC driver]("https://odbc.postgresql.org/") if you need to access the data from Windows using something like Excel or Access.

---

### Post by webmiester on 2017-08-08
Thanks!  I wasnt sure what thread to post in.  Since I was working on Ubuntu Server, I thought of Ubuntu Server.

---

### Post by webmiester on 2017-08-08
My entire program is written on MySQL.  I think it will be too big a work to rewrite everything in PostgreSQL.  With your inputs, at least I know what features to look for to activate in MySQL if ever it does have those features.

Thanks so much.

---

### Post by SeijiSensei on 2017-08-10
You could set up some sort of non-real-time replication scheme.  In the PHP code, you could duplicate every write to the DB and put one copy on the main server and another copy on the replica.  

Another option would be to schedule a dump of the database using mysql_dump every fifteen minutes or sooner depending on your servers' performance.  Write a script to dump the contents of the DB to a file, then use that file to recreate the DB on the replica machine.  These are kludgy measures, of course, but they might be sufficient for your needs.

I would strongly recommend using a RAID array for the main database server, and routine backups, of course, if you don't go down the phony replication route.  I run a script from cron once per night that backs up all the PostgreSQL and MySQL databases on my cloud-based web server using pg_dump and mysql_dump, then copies those files to a disk drive in my home office.  I posted a sample MySQL backup script here: [https://ubuntuforums.org/showthread.php?t=2195496&p=12882235&viewfull=1#post12882235](https://ubuntuforums.org/showthread.php?t=2195496&p=12882235&viewfull=1#post12882235)

---

### Post by webmiester on 2017-08-13
Hi Seiji,

Thank you so much, I really appreciate your inputs.  With your reply last time, I found that MySQL also has the SQL Replication feature where it will copy everything to a slave server.  Everyone can write only to the master SQL and the system will automatically copy it to the slave.  However, everyone can read off both master and slave SQL so that network traffic to the master server is reduced.  I think it is a really cool idea.  I also like your idea of copying the SQL to a cloud via CRON.  Actually, this is what my programmer wants to do.  I think I can do both.

I have some other ideas about this SQL replication technique.  For one, our workstation's browsers are set to go to the IP address of the main server.  In my interpretation, this means that they will not be accessing the slave server anytime, even if the master server goes down (because they are pointed to the maseter's IP address, not the slave).  I was thinking of perhaps setting up a DNS server and give both the master and slave SQL servers the same local web address.  In this case, if the master is down, the DNS server will automatically direct to the slave.  Do you think this idea will work, or is there an easier way to do it?  Thank so much.

---

### Post by SeijiSensei on 2017-08-13
DNS allows you to specify multiple IP addresses for a single name.  
```

myserver      IN       A      10.10.10.10
                              10.10.10.11
                              10.10.10.12

```
Each client will get one of those addresses at random.  If you want to weight the distribution in favor of a specific server you can repeat that entry multiple times:
```

myserver      IN       A      10.10.10.10
                              10.10.10.10
                              10.10.10.10
                              10.10.10.11
                              10.10.10.12

```

What keeps this scheme from working well is caching of name-service records on the client workstations.  Windows is especially bad at this; oftentimes you either need to run "ipconfig /flushdns" in a cmd.exe terminal, or reboot, if the IP address is dead.  You could use extremely short time-to-live values in the DNS records as a workaround.

---

### Post by webmiester on 2017-08-19
Fantastic!  Thank you Seiji.  Your explanation of the DHCP is quite good.  It doesn't look like its what I would like to do though.  I recently found articles on upgrading the slave into the master SQL.  I also found one which describes a master-master setup instead of master-slave.  I will read on those more thoroughly.  Thank you for pointing me to this direction.

---

### Post by TheFu on 2017-08-21
DHCP is different from DNS. DNS is what SeijiSensei described.

There are many, many, other methods to accomplish your goal. Postgres data replication **is** more mature than the MySQL replication.  If (when) the replication gets out of sync, it is ugly, regardless of the underlying DBMS.
You could use a block-level replication method too. This is useful sometimes, especially if all the data isn't stored inside a DBMS.

The amount of data involved would matter greatly.

BTW, you don't need to use php.  Python, Perl, Ruby are viable options as well.  Whatever you choose will be with you, causing problems, for years, regardless.  All custom code has problems and needs to be maintained, since 3rd party libraries are constantly changing and old versions dropped from support.  It is an ongoing problem, forever.  Some of my code was running from 1989 - 2011.  That's a long time.

---


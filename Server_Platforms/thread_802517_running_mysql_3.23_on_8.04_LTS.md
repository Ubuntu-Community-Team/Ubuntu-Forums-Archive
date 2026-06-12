---
title: "running mysql 3.23 on 8.04 LTS"
date: 2008-05-21
forum: Server Platforms
---

### Post by pagingmrherman on 2008-05-21
Hi is there any way to run mysql 3.23 on Hardy Heron 64bit server Ed.?
I for the life of me cannot get sources to compile or find a binary distro that will start up.
The reason I have to use 3.23 is that I have an old dead-end proprietary application that used to run on debian 3.0 and it has tables with field names of 'from', 'to' and 'read'.  Apparently that is a no-no in mySQL 4 or 5.  The old debian server has no more drive space and ancient hardware.
The only other thing I can think of is to run it in a VM w/ an older distro????

Any help would be greatly appreciated......

PW

---

### Post by ikonia on 2008-05-21
your going to really struggle to get this to compile.

I've just looked at the dependencies for it, and pretty much every package it needs in the Hardy release is WAY too new, normally this would be a good thing that it's new, but there have been too many changes in core things (threading library as an easy example) to get this to work without a massive effort.

On a side note, I've just created some tables called "to" and "from" in 5 on a hardy release and it didn't complain, I'd try it in 8.04 - see what happens.

Failing that, a virtual host seems a good option as you already suggested.

Is there no possability of adding disk to the old server, either locally or over the network ?

---

### Post by pagingmrherman on 2008-05-22
That's weird - you're right it does seem to work on my PC which is gutsy.
On the server I do this:

shell> mysql -u root
create database ProdNum;
quit
shell> mysql -u root <test.sql
ERROR 1064 (42000) at line 15: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'FROM varchar(38) default NULL,

  TO varchar(38) default NULL,

  READ int(11) def' at line 6

And this is what test.sql looks like:

CREATE TABLE MESSAGES (

  ID int(11) default NULL,

  DOCID int(11) default NULL,

  SENT datetime default NULL,

  TYPE int(11) default NULL,

  FROM varchar(38) default NULL,

  TO varchar(38) default NULL,

  READ int(11) default NULL

) TYPE=MyISAM;


This was produced by mysqldump so what could be wrong with the syntax???

---

### Post by windependence on 2008-05-22
This is gonna send you into dpendency hell. 

My suggestion would be to run it in a VM but run it on FreeBSD. It's lighter than Debian even, and you could use an older version, plus you can load just the packages you need, nothing else. I would run it only as an SQL server and just have the application connect to it remotely. I'm afraid the code will have to be changed to get it up the a newer version though.

-Tim

---

### Post by pagingmrherman on 2008-05-22
Oh man I think I found the answer to my problem - I noticed when playing with the SQL admin, when it creates the field names it puts *backward quotes* around field names!!!  I tried puting backwards quotes around TYPE, FROM TO and READ fields and the test went through.  I will try this for the big mysqldump files....

---

### Post by ikonia on 2008-05-23
> **pagingmrherman said:**
> That's weird - you're right it does seem to work on my PC which is gutsy.
On the server I do this:

shell> mysql -u root
create database ProdNum;
quit
shell> mysql -u root <test.sql
ERROR 1064 (42000) at line 15: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'FROM varchar(38) default NULL,

  TO varchar(38) default NULL,

  READ int(11) def' at line 6

And this is what test.sql looks like:

CREATE TABLE MESSAGES (

  ID int(11) default NULL,

  DOCID int(11) default NULL,

  SENT datetime default NULL,

  TYPE int(11) default NULL,

  FROM varchar(38) default NULL,

  TO varchar(38) default NULL,

  READ int(11) default NULL

) TYPE=MyISAM;


This was produced by mysqldump so what could be wrong with the syntax???



Try executing that create table sql statement yourself on the test system to see if/which line it errors, sometimes errors can be in the script, or the way they are called.

---

### Post by pagingmrherman on 2008-05-23
Well for future reference, that worked!  I had to modify the 3.23 dump file so that all fields named:

TYPE
FROM
READ
TO

got changed to 

`TYPE`
`FROM`
`READ`
`TO`

Also anything that said 

TYPE=MyISAM

I changed to
 
ENGINE=MyISAM

Thanks for everyone's help!!

PW

---


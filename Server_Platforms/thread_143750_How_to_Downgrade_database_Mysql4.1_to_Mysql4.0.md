---
title: "How to Downgrade database Mysql4.1 to Mysql4.0?"
date: 2006-03-13
forum: Server Platforms
---

### Post by Elijah on 2006-03-13
Hello forums, 

The head development department wanted us to downgrade our 4.1 version databases to 4.0 ... is that possible? if so, how? :confused:

---

### Post by gmclachl on 2006-03-13
[QUOTE=Elijah]Hello forums, 

The head development department wanted us to downgrade our 4.1 version databases to 4.0 ... is that possible? if so, how? :confused:[/QUOTE]

I was going to ask why, but if he/she is anything like my boss I think I already know the answer ;-)

You {could|should} be able to just dump all your data out of the database and downgrade by installing an earlier version. 

 Another way of doing it would be to **

 cd /var/lib/;  sudo tar -cvf /tmp/mysql-data.tar mysql 

 Install an earlier version of MySQL
 
 cd /var/lib/;   sudo tar -xf /tmp/mysql-data.tar

 sudo chown -R mysql /var/lib/mysql/*

** This works on OSX I have never tried it on Ubuntu. In theory it will be the same, but alway back your DB's up first.

George

---

### Post by Elijah on 2006-03-15
Hmm... our main development server right now is using CentOS(something like redhat) with mysql4.1, maybe I could use my workstation with ubuntu breezy with mysql 4.0.24-10 , move the /var/lib/mysql/databasestuff here & back. 

question: is 4.0.24-10 actually plain 4.0? or is there a big difference? for some reason I could'nt successfully install a tar.gz'ed version of an exact '4.0'. Couldn't find any apt sources for those either ... only 4.0.24

---

### Post by Elijah on 2006-03-16
while still googling around I found this:
[http://dev.mysql.com/doc/refman/4.1/en/downgrading-to-4-0.html](http://dev.mysql.com/doc/refman/4.1/en/downgrading-to-4-0.html)

in mysqldump there's an option for compatability to mysql40 , problem solved, thanks for the reply :-)

---


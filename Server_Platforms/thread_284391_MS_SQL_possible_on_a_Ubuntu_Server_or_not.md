---
title: "MS SQL possible on a Ubuntu Server or not"
date: 2006-10-25
forum: Server Platforms
---

### Post by hairshirt on 2006-10-25
Hi All, is it at all possible to host/install a MSSQL database on an Ubuntu/other Linux host server?  A client runs a MSDE version of MSSQL and I sure as heck don't want to be lumbered with all the other crap that comes with runing a windiz 2003 server.  Any takers?

---

### Post by jimbren on 2006-10-25
I don't believe you can install MS SQL in a linux environment at all.

---

### Post by hairshirt on 2006-10-25
But, But, But there must be a way!  I suppose this is the place to find out...  Any more takers?

---

### Post by bswilson on 2006-10-25
> **hairshirt said:**
> Hi All, is it at all possible to host/install a MSSQL database on an Ubuntu/other Linux host server?  A client runs a MSDE version of MSSQL and I sure as heck don't want to be lumbered with all the other crap that comes with runing a windiz 2003 server.  Any takers?

Well, Windows 2000 or Windows 2003 are prerequisites for installing SQL Server (any flavor).  But you can install **MySQL** or **postgresql** to perform database functions...

---

### Post by hairshirt on 2006-10-25
Thanks bswilson, The problem I have is that the database is currently on a windiz server... a server I run.  The database has to remain as a MS SQL database... Which is a real pain in the rump.

The database runs an ASP website.  I know ASP can now be run on a *nix server.  Immpossible to have it running under Wine?

---

### Post by hairshirt on 2006-10-25
Anyone? I'm not fussy...anyone will do, really.

---

### Post by dabear on 2006-10-25
You shouldn't rely on any winified (new word, hurrah!) app running in a production environment. You could try to install it, but I doubt that you will have any success. The best thing would be to convert the database to postre/mysql and the asp code to asp.net (mono) or php.

---

### Post by Ride Jib on 2006-10-25
Hah. Install VMWare and Windows2k3 on it. 

That's about the only way to actually do it.

---

### Post by hairshirt on 2006-10-26
Thanks chaps...  It's a shame.  I hate M$/Windiz as much as any other right thinking human but what can you do?

---

### Post by homegrown on 2006-10-26
The vmware solution would be the most sensible. 
Why would you want to complicate things sooo much? What is the application that uses this db? Maybe we can help you to run the app against a Linux Hosted DB server - this would make things slightly more stable

---

### Post by foxylad on 2006-10-26
MySQL runs on: Linux, *BSD, Windows...
PostgreSQL runs on: Linux, *BSD, Windows...
Oracle runs on: Linux, *BSD...
MS SQL runs on: Windows

Your problem is fallout from the original decision to build a solution on MS SQL. The flexibility to choose a platform is one of the true benefits of open source software - this is a good lesson to those designing (or in a position to advise on) solutions.

---

### Post by hairshirt on 2006-10-27
I didn't design or build the database nor the website that uses it.  If I had then it would be MySQL and php.  I'm not interested running another poxy windiz server.  I'm not interested in converting the database to MySQL.  Just how feezable do you think it is to run this poxy thing on vmware, bearing in mind that it's also going to be a web server?

Cheers, you're pals.

---


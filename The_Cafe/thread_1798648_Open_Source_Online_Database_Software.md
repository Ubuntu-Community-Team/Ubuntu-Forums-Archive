---
title: "Open Source Online Database Software?"
date: 2011-07-06
forum: The Cafe
---

### Post by onthefence on 2011-07-06
So, I'm just wondering if there is essentially an online database software project in the open source community that has the basic functionality of a desktop database program (views, search, export, etc...) and that is compatible with MySQL.

I have a bunch of databases in Filemaker Pro or Excel that I would love to put online "in the cloud." But, my lack of web programming expertise is preventing me from creating my own interface, ie: to search through records, add records, display etc...

There are many places that offer database hosting, but they are ridiculously expensive and cannot be justified for my situation.

Any help is much appreciated. Thanks

UPDATE: I found this one but not sure if this is compatible with MySQL, says it uses ASP. [http://www.restfuldevelopment.net/1clickdb/](http://www.restfuldevelopment.net/1clickdb/)

---

### Post by jerenept on 2011-07-06
> **onthefence said:**
> So, I'm just wondering if there is essential an online database software project in the open source community that has the basic functionality of a desktop database program (views, search, export, etc...) and that is compatible with MySQL.

I have a bunch of databases in Filemaker Pro or Excel that I would love to put online "in the cloud." But, my lack of web programming expertise is preventing me from creating my own interface, ie: to search through records, add records, display etc...

There are many places that offer database hosting, but they are ridiculously expensive and cannot be justified for my situation.

Any help is much appreciated. Thanks

Get a website host and install PHPMyAdmin.

---

### Post by jhonan on 2011-07-06
Most hosting companies who offer linux hosts will offer mySQL - It's the most popular db option at the moment (for linux) - If you see ASP (as in .net) that means it's probably a ms sql server on a windows host.

The piece you need is the front-end piece - i.e. the web pages which let you display/search/update etc. the records. For this I'm sure you can find some template solution, or a method to automatically generate the web pages from your db structure.

But basically: web hosting co. running mysql on a linux host (i.e. most of them) and then a front-end solution based on PHP or similar.

---

### Post by onthefence on 2011-07-06
Yes, I already have a host with MySQL. That is not the problem. As jhonan said, I need the "front end" templates and queries that are pre-built or dynamically built based on my custom database. 

There are some resources I found here, but I'm still in the process of vetting them:
[http://www.shambles.net/pages/school/Dbases/](http://www.shambles.net/pages/school/Dbases/)

So far, [http://www.grubba.net/](http://www.grubba.net/) seems the most promising. 

But if any knows of anything out there please share. I'd love to solve this problem I've been thinking about for over a year now.

---

### Post by ugm6hr on 2011-07-06
I tried VFront
[http://www.vfront.org/](http://www.vfront.org/)
I have to say, it is probably OK for very simple databases, but struggles with anything complex.

---

### Post by timZZ on 2011-07-06
You need a client? Is this what you mean? MySQL Workbench is my choice although I use only command line now.

---

### Post by SeijiSensei on 2011-07-06
If you have a copy of Microsoft Access, you can use the [MySQL ODBC connector]("http://dev.mysql.com/downloads/connector/odbc/") to link from Access to tables in a remote MySQL database.  You can import your Excel tables into Access and create an Append Query to upload the data into MySQL.  [Filemaker](http://www.filemaker.com/support/technologies/odbc.html) has ODBC support as well.

---

### Post by jhonan on 2011-07-06
> **timZZ said:**
> You need a client? Is this what you mean? MySQL Workbench is my choice although I use only command line now.

No, he's going to put all his data into mySQL, but wants an easy way (without programming) to create a web front-end to allow him to add/delete/update records.

You know, the type of webpage you'd usually create using PHP or whatever to display records.

---

### Post by drdos2006 on 2011-07-06
Maybe this might help.

[http://dabodev.com/](http://dabodev.com/)

[http://c0129431.cdn.cloudfiles.rackspacecloud.com/dataenvironment1.html](http://c0129431.cdn.cloudfiles.rackspacecloud.com/dataenvironment1.html)

[http://c0129431.cdn.cloudfiles.rackspacecloud.com/dataenvironment2.html](http://c0129431.cdn.cloudfiles.rackspacecloud.com/dataenvironment2.html)

regards

---


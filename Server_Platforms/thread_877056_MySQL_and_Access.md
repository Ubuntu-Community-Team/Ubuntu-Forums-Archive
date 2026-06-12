---
title: "MySQL and Access"
date: 2008-08-01
forum: Server Platforms
---

### Post by nonaguy on 2008-08-01
Hello, the company I work for is a Microsoft shop primarily, and we are slowly switching over to Linux server-side. However, we have hit a snag, specifically with Microsoft Access. There are literally hundreds of Access databases stored on our network, some still in use, others not so much. We would like some way to phase out Access with MySQL. Has anyone had this problem before, and if so, do they have any ideas or experience with a mass migration like this? Basically, we need to build a front end that has similar functionality to Access (since that is what our users are used to); such as mimicking the datasheet view in Access that allows the users to view all the tables. Does anyone know of any tools that make conversion easy from Access to MySQL?

We have an idea of how we wish to proceed, which is to find a way to dump all the Access data into MySQL, and let the users log into an application that connects them to their specific database. Anyone have any thoughts on this?

---

### Post by opscure on 2008-08-01
This should help guide you:
[http://www.kitebird.com/articles/access-migrate.html](http://www.kitebird.com/articles/access-migrate.html)

---

### Post by mbeach on 2008-08-01
DbVisualizer comes to mind - not sure about its cost and or 'freeness' but a few years ago it was looking quite promising and a quick look to their website seems it may have the functionality you are looking for (may).
mb.

EDIT:
looked at this screenshot:
[http://www.minq.se/products/dbvis/features/images/screens/scaled/queryBuilder2.png](http://www.minq.se/products/dbvis/features/images/screens/scaled/queryBuilder2.png)

---

### Post by tinny on 2008-08-01
You REALLY want to have a look at [MySQL Migration Toolkit]("http://www.mysql.com/products/tools/migration-toolkit/"). Ive used it to migrate an Oracle database to MySQL before (it can migrate Access as well) and it worked really well!

---

### Post by windependence on 2008-08-01
Thanks Tinny, I didn't even know they had this. You learn something new everyt day.

-Tim

---

### Post by mbeach on 2008-08-02
yes, that is quite nifty - would love to find a similar tool for postgresql.  The mysql group seem to be doing a great job of polishing such utilities.

---

### Post by windependence on 2008-08-02
mbeach, I had the same problem with postgresql. It's a fabulous database but support for everything is on MySQL, and I wanted to migrate a forum. There are a few products out there, but most are paid. You could try this:

[http://www.lightbox.ca/pg2mysql.php](http://www.lightbox.ca/pg2mysql.php)

I have not tried doing it though.

-Tim

---

### Post by nonaguy on 2008-08-18
Speaking of postgre, we are now thinking of using that for Access instead of MySQL because we are thinking of using it with ldap authentication. Anyone know of any good tools or processes to convert Access to postgreSQL?

---


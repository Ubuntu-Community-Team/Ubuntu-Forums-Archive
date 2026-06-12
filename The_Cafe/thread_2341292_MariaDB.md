---
title: "MariaDB"
date: 2016-10-26
forum: The Cafe
---

### Post by 7-webmaster on 2016-10-26
I am puzzled that MariaDB is not "supported" by Ubuntu.  That is you can install it using the command line, but it is not available from any of the standard Ubuntu repositories and cannot be installed using the GUI software centre.

By contrast when I install other current repos it seems that most of them, for example CentOS7, have replaced MySQL with MariaDB.

I appreciate that this is mostly a political rather than a technical issue, which is why I decided to raise it as a discussion topic here in the Cafe.  On the technical side there are advantages and disadvantages to either side.  For example I find that MySQL 5.7 catches more subtle bugs in SQL statements, while MariaDB gives you more choice in DB engines.  But the main issue is political:  do you trust Oracle to continue investing in MySQL when MySQL is the most popular competitor to its commercial database product, or would you rather trust the same team that created MySQL in the first place.

I am really torn.  The production site that I currently support is running MySQL 5.6 on CentOS6.  When I created a testing clone of the site in VirtualBox I installed MariaDB on CentOS7, because that was the closest current package, and I would have had to manually install MySQL on CentOS7.  So before I deploy a change I have tested it both on MariaDB and MySQL 5.7.    In any event I thought it would be good experience to get ready for a migration to RHEL if my customer thought that worthwhile. On the other hand I do not want to lock my customer in to a particular technology.  When I took over the site I discovered that a lot of the code was MySQL specific, which meant that it ran fine on both MySQL and MariaDB but would need to be modified if the site was ported to MSSQL Server or Oracle.  So one of the features that I would expect from Oracle's ownership of MySQL would be simplification of the migration path, either through adding OracleDB compatibility on MySQL or MySQL compatibility in OracleDB.  The MariaDB team obviously has different priorities.

---

### Post by steeldriver on 2016-10-26
AFAIK it's in `universe` - do you not consider that to be a standard repository?

---

### Post by ventrical on 2016-10-27
> **7-webmaster said:**
> I am puzzled that MariaDB is not "supported" by Ubuntu.  That is you can install it using the command line, but it is not available from any of the standard Ubuntu repositories and cannot be installed using the GUI software centre.



Uh?

---


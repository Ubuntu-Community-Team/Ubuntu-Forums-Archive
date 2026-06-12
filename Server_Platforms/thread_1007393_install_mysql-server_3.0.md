---
title: "install mysql-server 3.0 ?"
date: 2008-12-10
forum: Server Platforms
---

### Post by usererror on 2008-12-10
How can I install an OLD version of MYSQL 3.0 from Aptitude?  

My problem is I have a mysql DB from a host that is on 3.0  I am having problems importing some tables into a new host with MySQL 5.0.51-community. 

I thought I'd install mysql 3.0 import the DB, then upgrade it to mysql 5.0.51-community.  Or is there a better way?

Thanks!

---

### Post by Fire_Chief on 2008-12-10
This link ([http://forge.mysql.com/wiki/UpgradingFAQ]("http://forge.mysql.com/wiki/UpgradingFAQ")) discusses the preferred method of upgrading. They suggest doing incremental upgrades through the 4 series to 5 instead of a direct upgrade.

The MySQL archives appear to have versions back to 4.1 but not 4.0. I'm not sure where the best place is to get the old .debs for MySQL.

Hope this helps!

---

### Post by usererror on 2008-12-10
> **Fire_Chief said:**
> This link ([http://forge.mysql.com/wiki/UpgradingFAQ]("http://forge.mysql.com/wiki/UpgradingFAQ")) discusses the preferred method of upgrading. They suggest doing incremental upgrades through the 4 series to 5 instead of a direct upgrade.

The MySQL archives appear to have versions back to 4.1 but not 4.0. I'm not sure where the best place is to get the old .debs for MySQL.

Hope this helps!

Thanks that does helps!  I have done a few google searches but I must be using the wrong keywords.  I also cannot find anything less than 4.1 of MySQL on the mysql website.

---


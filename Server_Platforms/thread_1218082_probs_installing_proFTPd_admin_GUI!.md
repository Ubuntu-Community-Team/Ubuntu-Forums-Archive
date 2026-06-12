---
title: "probs installing proFTPd admin GUI!"
date: 2009-07-20
forum: Server Platforms
---

### Post by uluru13 on 2009-07-20
[http://proftpd-adm.sourceforge.net/page_install.php#admin](http://proftpd-adm.sourceforge.net/page_install.php#admin)

"The next step will be copying the sample configuration file for proFTPd and setting up that file (first edit it, it's path is "misc/sample_config/proftpd.conf" - if you want support for quotas you probably want to use "misc/sample_config/proftpd_quota.conf" instead). There are three values in this file that you need to change, <database_name> (just set to "proftpd_admin"), <database_user> (just enter "proftpd") and <database_password>  (enter the same password you did when editing the file "db_structure.sql"). Now just copy the sample configuration into place: "

problem is, there's no such thing as database_admin or database_user in proftpd.conf

can someone correct it please?
i could only guess...

---


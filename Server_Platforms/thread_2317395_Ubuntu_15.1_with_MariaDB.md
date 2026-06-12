---
title: "Ubuntu 15.1 with MariaDB"
date: 2016-03-16
forum: Server Platforms
---

### Post by albert42 on 2016-03-16
Hi,

I have installed MariaDB 10 successfully and was looking to load up the tokudb plugin.  I could not find any where in the disk and aso searching the "apt-cache search tokudb" returns nothing.   From all the documentation online it does say the tokudb is packaged with MariaDB.   May I know how to get the tokudb plugin installed.   Thanks.

Cheers,
Albert

---

### Post by howefield on 2016-03-16
Thread moved to the "*Server Platforms*" forum, probably a better fit for your question.

---

### Post by wellsilva-email on 2016-03-16
Hello Albert42,

In [specific versions of mariadb it is a separate package]("https://mariadb.com/kb/en/mariadb/enabling-tokudb/#installing-tokudb-on-ubuntu-debian"), in the others it is already included. In Ubuntu 15.10, [it is the 10.0.10 and up ]("https://launchpad.net/ubuntu/wily/+package/mariadb-server") so, as it doesn't have a separate package, go [through the steps to enable it]("https://mariadb.com/kb/en/mariadb/enabling-tokudb/#enabling-tokudb").

Hope to have helped, let us know if it went well. 

Peace.

---


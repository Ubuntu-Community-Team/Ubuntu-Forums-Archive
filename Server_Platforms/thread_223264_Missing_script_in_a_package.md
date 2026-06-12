---
title: "Missing script in a package???"
date: 2006-07-26
forum: Server Platforms
---

### Post by Jeffrey SomeBody on 2006-07-26
I'm setting up a Ubuntu server and installed a package called Bacula, A network backup soultion for Xp and Linux boxes.

After installing the package I got it running and was following the Bacula manual, I ran a few test runs and tried to run a script that is called out in the manual, "drop_mysql_tables"

I've searched all over for this script and come up with nothing. Was this script somehow left out of the package by mistake?

Thanks.

---

### Post by Gabriel Sandberg on 2008-01-30
I also have problems with missing scripts. In [http://www.bacula.org/en/rel-manual/Installing_Configurin_MySQL.html#MySqlChapter]("http://www.bacula.org/en/rel-manual/Installing_Configurin_MySQL.html#MySqlChapter") they want you to run grant_mysql_privileges and create_mysql_database. They have not been installed or they have been renamed or integrated into something else. Perhaps into postinst-common?

---


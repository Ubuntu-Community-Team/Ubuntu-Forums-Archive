---
title: "MySQl Error (2) with freeradius and mysql"
date: 2012-08-06
forum: Server Platforms
---

### Post by Joshiiii on 2012-08-06
I am at wits end. Freeradius with mysql install on Ubunto 12.04 64 bit. All went well, but the error I get is  "[COLOR=Red]Error: rlm_sql_mysql: Couldn't connect socket to MySQL server  radius@127.0.0.1:radius[/COLOR]" The following checks were made. I can login to mysql with user radius (mysql -u radius -p) The mysqld.sock file is under /var/run/mysqld (So it cannot be a misplaced file). I start freeradius -X and it works fine, it does not complain with the same error mentioned above. The radcheck utility also works when testing a user in the sql database. The only thing I can still think of is a permission error as I am running sudo freeradius -X . Changing the sql.conf from localhost to loopback ip or eth0 ip does not work either. Starting freeradius /etc/init.d/freeradius produces a fail, but no log entries to suggest if it is related to the same problem.  Any suggestions will be appreciated

---

### Post by oke on 2012-10-24
Part of the problem and the symptoms you describe are very similar to those found in post [http://ubuntuforums.org/showthread.php?t=2060807&highlight=freeradius+starting+boot]("http://ubuntuforums.org/showthread.php?t=2060807&highlight=freeradius+starting+boot"), which unfortunately hasn't a solution yet.

The difference in your description is that when you start freeradius as a service in an already running system the service fails. You are very expicit to mention to test **sudo** freeradius -X, which gives no error(s). Just checking the obvious: did you start service freeradius as superuser since you mention no error loggings (in /var/log/freeradius/radius.log?)?

---


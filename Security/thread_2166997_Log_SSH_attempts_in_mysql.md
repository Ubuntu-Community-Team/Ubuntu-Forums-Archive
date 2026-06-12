---
title: "Log SSH attempts in mysql"
date: 2013-08-11
forum: Security
---

### Post by kr6511292 on 2013-08-11
Is there a way to log all SSH attempts into a mysql database?  Or is there a way to run a program when an SSH attempt has been made?  Because then I could write a small script to log that info.

---

### Post by SeijiSensei on 2013-08-12
You could do this by adding a rule to iptables to log the connections, then writing a parser in some language (I use PHP) that reads the log, parses the entries, then runs the command to insert the record into the database.  Here's a rough outline:

```
/sbin/iptables -A INPUT -p tcp --dport 3306 -j LOG --log-prefix MySQL
```

That writes a line to /var/log/kern.log for every connection and uses a custom "prefix" in the log so you can extract the relevant records easily like this:

```
grep 'MySQL' /var/log/kern.log > MySQL-connectins.log
```

Now you just need to write a script to read each line, split it into fields on the space character, and run an INSERT command with the entries you want to log.  You might want to add some derived fields.  I convert textual dates like "Aug 10 12:03:47" into a Unix datestamp which is much easier to handle in queries.

I have written a similar script that parses Squid's access log.  We run it nightly from cron against each day's log.

---

### Post by 1clue on 2013-08-12
[http://www.syslog.org/wiki/Main/DatabaseLogging](http://www.syslog.org/wiki/Main/DatabaseLogging)

---

### Post by kr6511292 on 2013-08-13
Thanks!!  I wrote a simple java program tonight that parses and logs the info I want and dumps it into a mysql db.  I appricate the help.  Once I've cleaned up the code a bit I'll post it for anyone who might be looking to do the same.

---


---
title: "Monitoring doubts with Database and Ubuntu"
date: 2014-02-14
forum: Server Platforms
---

### Post by joseluis2 on 2014-02-14
Good days, my company request to me the implementation of a tool for monitoring my network company, the same have two types of databases, Oracle and PostgreSQL database. I thought install Nagios or Hobbit/Symon tool in a Ubuntu system, but I have someone doubts. ¿what types of checks Hobbit provides to me for monitor these databases? and ¿there is documentation about how its checks is configured?. ¿why was better hobbit than nagios?, ¿Somebody can help me?A lot of Thanks

---

### Post by SeijiSensei on 2014-02-16
If by "monitoring" you mean simply asking whether the server is up, I just use "ps" for this task like this:

```
ps ax | grep postgres | grep -v grep
```

I wrote a little script that runs from cron every fifteen minutes and checks to see if any of a set of programs is not running, i.e., where the command above returns an empty string.  The script then tries to restart the program with the "service" command and sends an email notice to me if it fails.

Now if, by monitoring, you mean checking to see whether the server is functioning properly, perhaps the best test would be a script that ran some common queries against the databases and made sure they returned the correct answers.  For this you'd need to write a script to invoke the "psql" client (for PostgreSQL) with a set of test queries.

This sounds like the kind of goof-ball request from management who throw out a word like "monitoring" as if there is some well-defined method for this task.  Ask them what they mean specifically by monitoring before you invest much time in this.

---

### Post by hawkmage on 2014-02-18
Monitoring is a big topic.  It can be as simple as a script run by cron that sends an email when something is wrong or as a major implementation of a vendor product from HP, CA or BMC.  

A decent opens source monitoring/alerting app is Nagios.  It has a wide variety of modules for gathering information about many common services and send alerts based on criteria you set.

---

### Post by CharlesA on 2014-02-18
Zabbix is another one, but I've been using Nagios at work for a while now and it is quite effective.

---

### Post by nerdtron on 2014-02-19
+1 for nagios.
A bit hard to setup but you can configure to query the database every 5 minutes or so to make sure the database server is running.

---


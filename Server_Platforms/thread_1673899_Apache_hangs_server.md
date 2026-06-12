---
title: "Apache hangs server"
date: 2011-01-23
forum: Server Platforms
---

### Post by Danne79 on 2011-01-23
Hi all,

I was hoping anyone had some tips on how to solve a problem for me.

I'm running Ubuntu as a webserver (apache2, php, mysql) and apache keeps hanging/freezing causing the whole server to be unresponsive. It's not possible to connect to it by ssh, basicly it requires a reboot to come back online.

Description:    Ubuntu 10.04.1 LTS
Release:        10.04
Codename:       lucid

When the server restarts, and you logon it's filled up with errors like this.

INFO: task: apache2:xxxx blocked for more than 120 seconds.
"echo 0 > /proc/sys/kernel/hung_task_sys_timeout_secs" disables this message

So it's obvious that apache freezes, maybe due to the memory being used up or something, but is there any way to solve something like this other than stuffing the server with more memory? maybe some kind of autokill on tasks that blocks or become to memory hungry? or some kind of apache config tweak that I don't know about?

---

### Post by piroka on 2011-02-03
Whats your configuration? what else are you running on that box at the time of the crash?

---

### Post by kevinthecomputerguy on 2011-02-03
I have had the exact oppisite experience. Everything else in the world will eventually crash (after 5 or 6 years) but not apache.
 
If i truly thought apache was a problem, i would start over, format and re-install. Its the most reliable service i have ever come across.
 
Not much of an answer, but i hope this helps.

---

### Post by albinootje on 2011-02-03
> **Danne79 said:**
> 
I'm running Ubuntu as a webserver (apache2, php, mysql) and apache keeps hanging/freezing causing the whole server to be unresponsive. 

So it's obvious that apache freezes, maybe due to the memory being used up or something, but is there any way to solve something like this other than stuffing the server with more memory? 

It would be very useful to provide how much RAM your computer has and how much swapspace, and which CPU, and free diskspace.

You can already start with looking if you can turn off "innodb" in the MySQL settings. Afaik php applications quite often don't use the innodb format.

"To disable to InnoDB storage engine add this to my.cnf (the default MySQL configuration files) in /etc/mysql/"
```

skip-innodb

```
( [http://mediakey.dk/~cc/optimize-mysql-for-low-memory-use/](http://mediakey.dk/~cc/optimize-mysql-for-low-memory-use/) )

---

### Post by rudelgurke on 2011-02-04
> **albinootje said:**
> You can already start with looking if you can turn off "innodb" in the MySQL settings. Afaik php applications quite often don't use the innodb format.

But at least wih MySQL 5.5 InnoDB should be the primary table format if possible. And the only possible reason still using MyISAM might be a fulltext index for boards as example.

Still - the configuration of this Apache server would be nice to see if everything's ok :)

---

### Post by Danne79 on 2011-02-11
The server only runs apache and mysql, I seem to have locked it down to mySQL being the part that takes all memory.
The server runs at 500MG of ram, basicly what happens is that mySQL eats up all the memory due to heavy queries and "badly written" queries.

however, it seems to have improved a bit after I change some settings on the mySQL but it still happens if the traffic load gets high.

Is there some way to configure mySQL or Ubuntu to kill processes or queries that takes to much time and/or ram?

---


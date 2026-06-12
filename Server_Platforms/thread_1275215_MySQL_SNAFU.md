---
title: "MySQL SNAFU"
date: 2009-09-25
forum: Server Platforms
---

### Post by lenswipe on 2009-09-25
Hey guys


For some reason MySQL server has just totally gone fubar on me, if i try and access my Joomla portal i just get the message:

> DB function failed with error number 2006
MySQL server has gone away SQL=SELECT session_id FROM jos_session WHERE session_id = '72a6c7ba27ec829428f8dd003cc6fd37'
SQL =

SELECT session_id
 FROM jos_session
 WHERE session_id = '72a6c7ba27ec829428f8dd003cc6fd37'

just wondered if anyone had any ideas as to how to fix this?


The server is ubuntu hardy 8.04 (i think its 8.04 - not sure) and the problem started when i tried to install freeradius and freeradius-mysql from the ubuntu repos.

Someone in #ubuntu that what was happening was that MySQL server was crashing when that particular query was executed or something like that, not sure...


Anyone able to help?


Thanks


-Lenswipe

---

### Post by lenswipe on 2009-09-26
bump

---

### Post by yknivag on 2009-09-26
Is MySQL still running?
```
ps -e | grep mysqld
```
should provide some output if it is. If there is no output then it has stopped.

If it's stopped you can try starting it with the command:
```
sudo ./etc/init.d/mysql start
```

Hopefully that will fix it, but if it went down 'uncleanly' then you may need to repair tables etc.

---

### Post by lenswipe on 2009-09-27
> **yknivag said:**
> Is MySQL still running?
```
ps -e | grep mysqld
```
should provide some output if it is. If there is no output then it has stopped.

If it's stopped you can try starting it with the command:
```
sudo ./etc/init.d/mysql start
```

Hopefully that will fix it, but if it went down 'uncleanly' then you may need to repair tables etc.



Yeah its running heres the of the first command:

```
 5041 ?        00:00:00 mysqld_safe
 5083 ?        00:00:01 mysqld

```


Ive tried restarting it several times to no avail...

All this started when i installed the freeradius-mysql package from the repos which ive now removed, however mysql still aint working...

---

### Post by yknivag on 2009-09-27
Hmm, well it hasn't "gone away" very far then! :)

The MySQL forums seem to suggest that some people have cured this with "flushing tables".  I've no doubt you can do that from the command line (though I wouldn't know how).

Do you have phpmyadmin installed?  If so there are some useful pages in there that will tell you what is running against the database at any given time and also some useful diagnostics too.

---

### Post by lenswipe on 2009-09-29
hmmm well, i just restarted MySQL and restarted my server a few times and now it works again.


Weird....



-L

---


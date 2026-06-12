---
title: "bdb_equality_candidates: (entryUUID) not indexed"
date: 2008-12-27
forum: Server Platforms
---

### Post by logandzwon on 2008-12-27
I have two servers doing ldap, silver and black.  I see this same log entry over and over hundreds of times about things not being indexed.  How do I fix this?

black;
Dec 27 16:28:39 black slapd[23144]: <= bdb_equality_candidates: (entryUUID) not indexed 
Dec 27 16:28:39 black last message repeated 29 times
Dec 27 16:28:39 black slapd[23144]: connection_read(27): no connection! 
Dec 27 16:28:44 black slapd[23144]: <= bdb_equality_candidates: (entryUUID) not indexed 
Dec 27 16:29:19 black last message repeated 210 times
Dec 27 16:29:19 black last message repeated 29 times
Dec 27 16:29:19 black slapd[23144]: connection_read(27): no connection! 
Dec 27 16:29:24 black slapd[23144]: <= bdb_equality_candidates: (entryUUID) not indexed 
Dec 27 16:29:54 black last message repeated 209 times
Dec 27 16:29:59 black last message repeated 30 times
Dec 27 16:30:01 black /USR/SBIN/CRON[23404]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Dec 27 16:30:04 black slapd[23144]: <= bdb_equality_candidates: (entryUUID) not indexed 
Dec 27 16:30:24 black last message repeated 149 times
Dec 27 16:30:27 black slapd[23144]: <= bdb_equality_candidates: (uid) not indexed 
Dec 27 16:30:29 black slapd[23144]: <= bdb_equality_candidates: (entryUUID) not indexed 
Dec 27 16:30:59 black last message repeated 209 times
Dec 27 16:30:59 black slapd[23144]: connection_read(27): no connection! 
Dec 27 16:31:04 black slapd[23144]: <= bdb_equality_candidates: (entryUUID) not indexed 



silver;
Dec 27 16:29:44 silver slapd[6313]: <= bdb_equality_candidates: (entryUUID) not indexed 
Dec 27 16:29:54 silver last message repeated 119 times
Dec 27 16:30:01 silver /USR/SBIN/CRON[6749]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Dec 27 16:30:04 silver slapd[6313]: <= bdb_equality_candidates: (entryUUID) not indexed 
Dec 27 16:30:44 silver last message repeated 240 times

---

### Post by logandzwon on 2008-12-27
see thread;

[http://ubuntuforums.org/showthread.php?p=6446142](http://ubuntuforums.org/showthread.php?p=6446142)

---


---
title: "proftpd mod mysql configure"
date: 2010-04-01
forum: Server Platforms
---

### Post by pavel989 on 2010-04-01
hey all. bit of a weird set up that i can't get right.

i got an ubuntu desktop with a proftpd install, using a mysql db for its users. and i cannot figure if proftpd is even sending requests. im fairly confused.
the mysql logs dont show any requests but proftpd logs show incorrect logins.

mysql on the server machine is thruough a lampp install. 

i used the example file in /etc/proftpd/ that appeared when i installed the proftpd mod mysql package.

what can i be doing wrong

---

### Post by richardjh on 2010-04-06
Check for SQLLogFile in /etc/proftpd.conf

It should be defined, or otherwise set it to something like this

SQLLogFile /var/log/proftpd/sql.log

Then you can see what SQL queries are being sent from proftpd to mysql.

proftpd doesn't log very much by default, you can get it to be a bit more verbose by shutting down proftpd and starting manually using

proftpd -d 10 -n

Which will set debugging to maximum ( -d 10 ) and send output to console ( -n ). 
You can then try connecting with an ftp client and see exactly what is happening. 

If you still get problems, post the output here.

---


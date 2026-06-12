---
title: "Squid"
date: 2009-03-18
forum: Server Platforms
---

### Post by Kluttz on 2009-03-18
I was trying to setup some ACL and now my squid will not lauch
I am getting this error 

FATAL: Unable to open configuration file: /etc/squid/squid.conf: (13) Permission denied
Squid Cache (Version 2.7.STABLE3): Terminated abnormally.
CPU Usage: 0.020 seconds = 0.010 user + 0.010 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 0
Aborted


Any ideas why, and what I can do to fix it

thanks

---

### Post by Kluttz on 2009-03-19
Does anyone have any ideas regarding this error msg.

I have tried to re-install squid, but it still will not start up.

---

### Post by jagnikam on 2009-03-19
Please  check owner and group of conf files. 
You must be logged in by root user to make changes in squid.

---

### Post by HermanAB on 2009-03-19
'Permission denied' means exactly that.  It is an error coming from PAM which won't allow Squid to read the file.  So, you got to use chmod and chown to fix it.

Cheers,

Herman

---

### Post by Kluttz on 2009-03-19
thanks for all your help.

I got tit working.  I purged squid and re-installed it.

---


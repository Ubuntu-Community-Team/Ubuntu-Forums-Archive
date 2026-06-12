---
title: "ssh server just stops accepting requests"
date: 2007-01-18
forum: Server Platforms
---

### Post by endfx on 2007-01-18
On one of my servers, every month and a half or so, my ssh server completely stops accepting requests. People who ssh in via command line get this:

ssh_exchange_identification: Connection closed by remote host

So I have to log on to the server locally and restart the ssh server (/etc/init.d/ssh restart).

I've checked the log files, and I don't see anything regarding the ssh server stopping. The only thing I see is a "received signal 15" in one of the logs, which is me restarting the server.

Does anybody have any idea as to why this could be happening?
Is there any way I can bump up the "logging sensitivity" of the ssh server so maybe the logs will catch something?

Thanks.

---

### Post by jtc on 2007-01-18
> **endfx said:**
> On one of my servers, every month and a half or so, my ssh 
Is there any way I can bump up the "logging sensitivity" of the ssh server so maybe the logs will catch something?.

**man 5 sshd_config**
> 
*LogLevel*
Gives the verbosity level that is used when logging messages from sshd.  The possible values are: QUIET, FATAL, ERROR, INFO, VERBOSE, DEBUG, DEBUG1, DEBUG2 and DEBUG3.  The default is INFO.  DEBUG and DEBUG1 are equivalent.  DEBUG2 and DEBUG3 each specify higher levels of debugging output.  Logging with a DEBUG level violates the privacy of users and is not recommended.


---


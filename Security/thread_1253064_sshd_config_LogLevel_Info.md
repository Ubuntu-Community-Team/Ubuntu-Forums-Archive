---
title: "sshd_config LogLevel Info"
date: 2009-08-29
forum: Security
---

### Post by smc18 on 2009-08-29
Hey everyone,

I have questions about the sshd_config file.

Other than reading the man page; where can I find a good explaination of what the different values for LogLevel do? (And even other values within the config file?)

```
cat /etc/ssh/sshd_config

...
#Logging
SyslogFacility AUTH
LogLevel INFO
...
```

>  
...
LogLevel
             Gives the verbosity level that is used when logging messages from
             sshd(8).  The possible values are: [B]SILENT, QUIET, FATAL, ERROR,
             INFO, VERBOSE, DEBUG, DEBUG1, DEBUG2, and DEBUG3.[/B]  The default is
             INFO.  DEBUG and DEBUG1 are equivalent.  DEBUG2 and DEBUG3 each
             specify higher levels of debugging output.  Logging with a DEBUG
             level violates the privacy of users and is not recommended.
...


And where is the logging located at?  Is it just added to /var/log/auth.log?

---


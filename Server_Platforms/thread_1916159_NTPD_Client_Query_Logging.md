---
title: "NTPD Client Query Logging"
date: 2012-01-27
forum: Server Platforms
---

### Post by bdestephen on 2012-01-27
Hello,

 I need to be able to log when a client attempts to query the ntpd process for a time update.  Has anyone setup anything like this?  Ideally, I would like to see successful client queries logged, but even a failed attempt (i.e. restrict default ignore) would be acceptable for troubleshooting.  Log file size is not important for this setup.

I have successful logging to /var/log/ntp.log and am able to see when the server itself synchronizes or the service restarts, however I cannot see when a client attempts a synchronization.  This is a private, non Internet environment so the rest of the configuration is very basic.

contents of /etc/ntp.conf:

server 127.127.1.0
fudge server 127.1.0 stratum 5
logfile /var/log/ntp.log

Thanks for any suggestions!

---

### Post by ruffEdgz on 2012-01-27
I think this link would be useful for this:

[http://www.zytrax.com/books/dns/ch7/logging.html](http://www.zytrax.com/books/dns/ch7/logging.html)

I would look at the variables 'severity' and 'category' to see if either one will help.

Here is an example for logging in named.conf:
```

channel default_syslog {
        // Send most of the named messages to syslog. 
        syslog local2; 
        severity debug;
        };

        category default { default_syslog; };

```

---


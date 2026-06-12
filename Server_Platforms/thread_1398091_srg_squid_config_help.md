---
title: "srg squid config help"
date: 2010-02-04
forum: Server Platforms
---

### Post by dragos2 on 2010-02-04
I think I miss something here(Ubuntu 9.10 server 64bit):

 /etc/srg/srg.conf
```


##### SRG Example Configuration File #####

# Squid log file to process
#       Defaults to access.log in the srg directory.
# e.g. log_file "/usr/local/squid/logs/access.log"
log_file "/var/log/squid/access.log"


```because when I try to point it to squid logs

```

root@ubu:~# srg -Cv /etc/srg/srg.conf
WARNING: Configuration file not found!
No logfile lines found to process!

```Any ideas what I miss ?

---

### Post by koenn on 2010-02-04
obvious first guess:


/etc/srg/srg.conf doesn't exist or is not readable by srg (permissions ?)

/var/log/squid/access.log doesn't exist or is not readable by srg (permissions ?)

---


---
title: "Memcached stops working when using unix sockets."
date: 2015-07-23
forum: Server Platforms
---

### Post by gijs007 on 2015-07-23
I'm having issues where memcached is not functioning properly on Ubuntu 15.04 when using Unix sockets. It stops working after it has been running for a while(1-3 days) and then requires to be restarted to work properly again.


  The config is:


```
-d

# Log memcached's output to /var/log/memcached
logfile /var/log/memcached.log

# Be verbose
# -v

# Be even more verbose (print client commands as well)
# -vv

# Start with a cap of 64 megs of memory. It's reasonable, and the daemon default
# Note that the daemon will grow to this size, but does not start out holding this much
# memory
-m 4096

# Default connection port is 11211
#-p 11211

# Run the daemon as root. The start-memcached will default to running as root if no
# -u command is present in this config file
-u memcache

# Specify which IP address to listen on. The default is to listen on all IP addresses
# This parameter is one of the only security measures that memcached has, so make sure
# it's listening on a firewalled interface.
#-l 127.0.0.1

# Limit the number of simultaneous incoming connections. The daemon default is 1024
# -c 1024

# Lock down all paged memory. Consult with the README and homepage before you do this
# -k

# Return error when memory is exhausted (rather than removing items)
# -M

# Maximize core file limit
# -r

-s /tmp/memcached.sock
-a 666

-t 8
-R 200
```

Any idea what could be wrong?

I've also noticed the following in my syslog, I'm not sure if it's related
```
Jul 24 03:32:33 elitegameservers systemd[1]: Created slice user-1000.slice.
Jul 24 03:32:33 elitegameservers systemd[1]: Starting user-1000.slice.
Jul 24 03:32:33 elitegameservers systemd[1]: Starting User Manager for UID 1000...
Jul 24 03:32:33 elitegameservers systemd[1]: Started Session 30731 of user gijs.
Jul 24 03:32:33 elitegameservers systemd[1]: Starting Session 30731 of user gijs.
Jul 24 03:32:33 elitegameservers systemd[28762]: Reached target Paths.
Jul 24 03:32:33 elitegameservers systemd[28762]: Starting Paths.
Jul 24 03:32:33 elitegameservers systemd[28762]: Reached target Timers.
Jul 24 03:32:33 elitegameservers systemd[28762]: Starting Timers.
Jul 24 03:32:33 elitegameservers systemd[28762]: Reached target Sockets.
Jul 24 03:32:33 elitegameservers systemd[28762]: Starting Sockets.
Jul 24 03:32:33 elitegameservers systemd[28762]: Reached target Basic System.
Jul 24 03:32:33 elitegameservers systemd[28762]: Starting Basic System.
Jul 24 03:32:33 elitegameservers systemd[28762]: Reached target Default.
Jul 24 03:32:33 elitegameservers systemd[28762]: Startup finished in 20ms.
Jul 24 03:32:33 elitegameservers systemd[28762]: Starting Default.
Jul 24 03:32:33 elitegameservers systemd[1]: Started User Manager for UID 1000.
Jul 24 03:32:38 elitegameservers CRON[28615]: (CRON) info (No MTA installed, discar
```

---


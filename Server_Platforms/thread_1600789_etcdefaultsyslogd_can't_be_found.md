---
title: "/etc/default/syslogd can't be found"
date: 2010-10-19
forum: Server Platforms
---

### Post by satimis on 2010-10-19
Hi folks,

Ubuntu 10.04 server 64-bit

I was following;
The Perfect Server - Ubuntu Hardy Heron (Ubuntu 8.04 LTS Server) - Page 4
[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p4](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p4)

to set up the server on Ubuntu 10.04 and encountered problem on editing /etc/default/syslogd```

# Top configuration file for syslogd
# Full documentation of possible arguments are found in the manpage
# syslogd(8).
#
# For remote UDP logging use SYSLOGD="-r"
#
SYSLOGD="-a /var/lib/named/dev/log"

```

I couldn't find syslogd.

Please advise which file shall I edit?  TIA

B.R.
satimis

---

### Post by arrrghhh on 2010-10-19
Did you checkout ```
man syslogd
``` as it suggested...?

---

### Post by satimis on 2010-10-20
> **arrrghhh said:**
> Did you checkout ```
man syslogd
``` as it suggested...?

Hi,

$ man syslogd```

No manual entry for syslogd

```

I wonder whether the process has been changed on this version of Ubuntu OR the file has been re-named

I found;
$ ls -l /etc/default/ | grep syslog```

-rw-r--r-- 1 root root  321 2010-02-25 02:26 rsyslog

```

$ cat /etc/default/rsyslog ```

# Options for rsyslogd
# -m 0 disables 'MARK' messages (deprecated, only used in compat mode < 3)
# -r enables logging from remote machines (deprecated, only used in compat mode < 3)
# -x disables DNS lookups on messages received with -r
# -c compatibility mode
# See rsyslogd(8) for more details
RSYSLOGD_OPTIONS="-c4"

```


B.R.
satimis

---

### Post by arrrghhh on 2010-10-20
Hm, my apologies.  Do you need to do that step...?  It hardly seems necessary, but I'm not really sure how it applies to what you're trying to do.

---

### Post by satimis on 2010-10-20
> **arrrghhh said:**
> Hm, my apologies.  Do you need to do that step...?  It hardly seems necessary, but I'm not really sure how it applies to what you're trying to do.

Hi,

I don't know whether this step is necessary on Ubuntu 10.04.  I just followed that howto.  I'll skip this step and continue to see what will happen.  Thanks

B.R.
satimis

---


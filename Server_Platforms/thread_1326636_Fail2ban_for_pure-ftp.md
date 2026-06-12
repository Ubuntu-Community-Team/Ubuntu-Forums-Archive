---
title: "Fail2ban for pure-ftp"
date: 2009-11-14
forum: Server Platforms
---

### Post by wxman on 2009-11-14
I'm looking for anyone who has had luck getting fail2ban to work with pure-ftp. I keep getting log entries like:
```

Nov 14 15:39:05 web1 pure-ftpd: (?@60.217.229.228) [WARNING] Authentication failed for user [administrator]
Nov 14 15:39:18 web1 pure-ftpd: (?@60.217.229.228) [INFO] PAM_RHOST enabled. Getting the peer address
Nov 14 15:39:20 web1 pure-ftpd: (?@60.217.229.228) [WARNING] Authentication failed for user [administrator]
Nov 14 15:39:32 web1 pure-ftpd: (?@60.217.229.228) [INFO] PAM_RHOST enabled. Getting the peer address
Nov 14 15:39:34 web1 pure-ftpd: (?@60.217.229.228) [WARNING] Authentication failed for user [administrator]

```

my fail2ban failregex for pure-ftpd is now:
```

failregex = pure-ftpd(?:\[\d+\])?: (.+?@<HOST>\)) \[WARNING\] %(__errmsg)s \[.+\]$
failregex = pure-ftpd(?:\[\d+\])?: (.+?@<HOST>\)) \[INFO\] %(__errmsg)s \[.+\]$

```

So far I haven't blocked a single one.

---

### Post by speedy67 on 2009-12-20
> **wxman said:**
> 

my fail2ban failregex for pure-ftpd is now:
```

failregex = pure-ftpd(?:\[\d+\])?: (.+?@<HOST>\)) \[WARNING\] %(__errmsg)s \[.+\]$
failregex = pure-ftpd(?:\[\d+\])?: (.+?@<HOST>\)) \[INFO\] %(__errmsg)s \[.+\]$

```

So far I haven't blocked a single one.

I only use the top line (containing WARNING), and ip's are blocked regularly. This is my complete /etc/fail2ban/filter.d/pure-ftpd.conf :

```

# Fail2Ban configuration file
#
# Author: Cyril Jaquier
# Modified: Yaroslav Halchenko for pure-ftpd
#
# $Revision: 3$
#

[Definition]

# Error message specified in multiple languages
__errmsg = (?:Authentication failed for user|Erreur d'authentification pour l'utilisateur)

#
# Option: failregex
# Notes.: regex to match the password failures messages in the logfile. The
#         host must be matched by a group named "host". The tag "<HOST>" can
#         be used for standard IP/hostname matching and is only an alias for
#         (?:::f{4,6}:)?(?P<host>\S+)
# Values: TEXT
#
failregex = pure-ftpd(?:\[\d+\])?: (.+?@<HOST>\)) \[WARNING\] %(__errmsg)s \[.+\]$
#origineel: failregex = pure-ftpd (?:\[\d+\])?: (.+?@<HOST>) \[WARNING\] %(__errmsg)s \[.+\]$
# Option:  ignoreregex
# Notes.:  regex to ignore. If this regex matches, the line is ignored.
# Values:  TEXT
#
ignoreregex =

```

Be sure to add the following to /etc/fail2ban/jail.conf

```

[pure-ftpd]

enabled  = true
port     = ftp,ftp-data,ftps,ftps-data
filter   = pure-ftpd
logpath  = /var/log/messages
maxretry = 5

```

Greetings, Sander

---

### Post by wxman on 2009-12-21
Thanks for the reply. I'm now trying this pair:
```

# Error message specified in multiple languages
__errmsg = (?:Authentication failed for user|Erreur d'authentification pour l'utilisateur)

failregex = .*pure-ftpd: \(.*@<HOST>\) \[WARNING\] Authentication failed for user.*
failregex = .*pure-ftpd: \(.*@<HOST>\) \[INFO\] PAM_RHOST enabled. Getting the peer address.*

```
So far this has been doing okay, but I also noticed a new trick. I got nearly a day's worth of entries from one attacker that would make two tries, stop for 10 minutes, then do two more tries. Fail2ban, of course, didn't see it as an attack, so it ignored it. I'll try your suggestion next.

---

### Post by ingramproductions on 2011-10-12
I got it working by following this tutorial for Fail2ban on Ubuntu 10.04:

[http://itswapshop.com/content/how-install-and-configure-fail2ban-ubuntu-1004-ssh-and-pure-ftpd]("http://itswapshop.com/content/how-install-and-configure-fail2ban-ubuntu-1004-ssh-and-pure-ftpd")

---


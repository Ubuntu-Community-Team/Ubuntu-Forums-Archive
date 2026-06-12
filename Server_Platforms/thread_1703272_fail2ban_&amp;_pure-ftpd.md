---
title: "fail2ban &amp; pure-ftpd"
date: 2011-03-09
forum: Server Platforms
---

### Post by JeanCr on 2011-03-09
Edit: solved with sudo chmod a+rw /var/run/fail2ban/fail2ban.sock

Hello,
Fail2ban does not ban authentication failures from pure-ftpd. Anybody can help me?

I used this filter :
```

__errmsg = (?:Authentication failed for user|Erreur d'authentification pour l'utilisateur)

failregex = pure-ftpd: \(\?@<HOST>\) \[WARNING\] %(__errmsg)s \[.+\]$
ignoreregex = 

```

This is in jail.conf:

```

[pure-ftpd]

enabled  = true
port	 = ftp,ftp-data,ftps,ftps-data
filter   = pure-ftpd
logpath  = /var/log/messages
maxretry = 6

```

These are in /var/log/messages:

```

Mar  9 09:33:24 server pure-ftpd: (?@192.168.1.11) [WARNING] Authentication failed for user [anonymous]

```
Testing with 
```
fail2ban-regex /var/log/messages /etc/fail2ban/filter.d/pure-ftpd.conf
```
yields lots of hits.

'sudo fail2ban-client status' tells me it's running the jail.

Still no bans.

Thanks for help.

---

### Post by ingramproductions on 2011-10-12
I got it working by following this tutorial:

[http://itswapshop.com/content/how-install-and-configure-fail2ban-ubuntu-1004-ssh-and-pure-ftpd]("http://itswapshop.com/content/how-install-and-configure-fail2ban-ubuntu-1004-ssh-and-pure-ftpd")

---


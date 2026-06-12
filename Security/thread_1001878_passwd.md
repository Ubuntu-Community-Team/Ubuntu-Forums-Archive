---
title: "passwd"
date: 2008-12-04
forum: Security
---

### Post by iLLiCiTgr on 2008-12-04
Hi, i have a question.
Do you know, which of these SHOULD have /bin/bash or /bin/sh and which shouldn't have? (/bin/null or /bin/false)
```

root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
dhcp:x:100:101::/nonexistent:/bin/false
syslog:x:101:102::/home/syslog:/bin/false
klog:x:102:103::/home/klog:/bin/false
sshd:x:103:65534::/var/run/sshd:/usr/sbin/nologin
fetchmail:x:104:65534::/var/lib/fetchmail:/bin/sh
ntp:x:105:108::/home/ntp:/bin/false
bind:x:106:109::/var/cache/bind:/bin/false
postfix:x:108:111::/var/spool/postfix:/bin/false
teamspeak:x:1003:1003:teamspeak,,,:/home/teamspeak:/bin/false
ftp:x:109:65534::/home/ftp:/bin/false
proftpd:x:107:65534::/var/run/proftpd:/bin/false
mysql:x:1004:1004::/home/mysql:/bin/sh
clamav:x:110:113::/var/lib/clamav:/bin/false
amavis:x:111:114:AMaViS system user,,,:/var/lib/amavis:/bin/sh
dcc:x:112:115:DCC System User:/var/lib/dcc:/bin/false
vmail:x:1005:1005::/home/vmail/:/bin/false
dovecot:x:113:1005:Dovecot mail server,,,:/usr/lib/dovecot:/bin/false
postgrey:x:114:117::/var/lib/postgrey:/bin/false
ftpuser:x:2001:2001:proftpd user:/bin/null:/bin/false
uml-net:x:115:118::/home/uml-net:/bin/false
newsearch:x:1009:1009:,,,:/var/www/vhost/newsearch/:/dev/null
amavis-stats:x:116:4::/var/lib/amavis-stats:/bin/false

```

---

### Post by scorp123 on 2008-12-04
> **iLLiCiTgr said:**
> Do you know, which of these SHOULD have /bin/bash or /bin/sh and which shouldn't have? (/bin/null or /bin/false)  Why do you ask?

Most of those accounts are system accounts, e.g. owned by a program. So from time to time e.g. a program might need to do certain things and then it would become active, but instead of executing under "root" priviledges it would switch into one of those accounts and then execute whatever it needs to execute under that account. Also: most of those accounts are pretty much "standard". So by all means: don't remove them or touch them in any way unless you 100% know what you do, OK?

If "getting hacked" is what worries you:
Unless you installed **openssh-server** you're most likely not even reachable for any wannabe hackers, they have no obvious way into your system. And normally none of those accounts have passwords, so a remote login is not even possible with those accounts.

---

### Post by iLLiCiTgr on 2008-12-05
The above accounts are on a dedicated webserver(so sshd is installed, yes). Since a colleague of mine installed some services on this machine, i am interested to know if any of these services left any (standar) accounts with shell access.

But thanks for the info, i didn't know why most of the accounts described in this file needed shell access.

If anyone could then point me out to ANY of the above that do NOT need /bin/sh

Thanks again

---

### Post by scorp123 on 2008-12-05
> **iLLiCiTgr said:**
> i am interested to know if any of these services left any (standar) accounts with shell access. Not really relevant IMHO .... If they would not need shell access (at least from time to time) they would not have been installed the way they were I guess?

What you should keep an eye on is the /etc/shadow file IMHO:
```
sudo cat /etc/shadow
``` ... that's where hashes to the passwords get stored.

In theory none of those accounts should have a password attached to it. See this posting:

[http://ubuntuforums.org/showthread.php?p=5606071#post5606071](http://ubuntuforums.org/showthread.php?p=5606071#post5606071)

---


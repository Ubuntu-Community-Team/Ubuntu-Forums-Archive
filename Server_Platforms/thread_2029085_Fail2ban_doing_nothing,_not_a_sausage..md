---
title: "Fail2ban doing nothing, not a sausage."
date: 2012-07-19
forum: Server Platforms
---

### Post by VMOS on 2012-07-19
So I've installed fail2ban on ubuntu server 12.04, set it to ban folks and email me and it's doing bugger all

Here's what's in the log
```
2012-07-19 14:56:59,555 fail2ban.server : INFO   Changed logging target to /var/log/fail2ban.log for Fail2ban v0.8.6
2012-07-19 14:56:59,555 fail2ban.jail   : INFO   Creating new jail 'ssh'
2012-07-19 14:56:59,556 fail2ban.jail   : INFO   Jail 'ssh' uses Gamin
2012-07-19 14:56:59,566 fail2ban.filter : INFO   Added logfile = /var/log/auth.log
2012-07-19 14:56:59,567 fail2ban.filter : INFO   Set maxRetry = 6
2012-07-19 14:56:59,567 fail2ban.filter : INFO   Set findtime = 600
2012-07-19 14:56:59,568 fail2ban.actions: INFO   Set banTime = 600
2012-07-19 14:56:59,597 fail2ban.jail   : INFO   Creating new jail 'pure-ftpd'
2012-07-19 14:56:59,597 fail2ban.jail   : INFO   Jail 'pure-ftpd' uses Gamin
2012-07-19 14:56:59,598 fail2ban.filter : INFO   Added logfile = /var/log/syslog
2012-07-19 14:56:59,598 fail2ban.filter : INFO   Set maxRetry = 2
2012-07-19 14:56:59,599 fail2ban.filter : INFO   Set findtime = 600
2012-07-19 14:56:59,599 fail2ban.actions: INFO   Set banTime = 600
2012-07-19 14:56:59,607 fail2ban.jail   : INFO   Jail 'ssh' started
2012-07-19 14:56:59,609 fail2ban.jail   : INFO   Jail 'pure-ftpd' started
```

Then I try multiple ssh and ftp attempts, nothing gets added to the log

Here's what's in the jail.conf
```
[ssh]

enabled  = true
port     = ssh
filter   = sshd
logpath  = /var/log/auth.log
maxretry = 6

[pure-ftpd]

enabled  = true
port     = ftp,ftp-data,ftps,ftps-data
filter   = pure-ftpd
logpath  = /var/log/syslog
maxretry = 2


```


Here's what's in the syslog

```
Jul 19 14:17:58 ubuntu-template pure-ftpd: (?@my.hostaddress.com) [INFO] New connection from my.hostaddress.com
Jul 19 14:18:02 ubuntu-template pure-ftpd: (?@my.hostaddress.com) [WARNING] Authentication failed for user [test]

```

and the authlog


```
Jul 19 15:14:17 ubuntu-server sshd[5473]: Connection closed by my.ip.address [preauth]
Jul 19 15:14:17 ubuntu-server sshd[5473]: PAM 1 more authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=my.ip.address  user=myuser
Jul 19 15:14:19 ubuntu-server sshd[5475]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=my.ip.address  user=myuser
Jul 19 15:14:21 ubuntu-server sshd[5475]: Failed password for myuser from my.ip.address port 8250 ssh2
```

which matches what's in the filters

```
failregex = ^%(__prefix_line)s(?:error: PAM: )?Authentication failure for .* from <HOST>\s*$

failregex = .*pure-ftpd: \(.*@<HOST>\) \[WARNING\] Authentication failed for user.*
```


So it seems to me that fail2ban is just sitting there ignoring the logs. I feel I'm missing something obvious but I'm having trouble figuring out what.

Any ideas?

---

### Post by clay7 on 2012-07-19
> [ssh]

enabled  = true
port     = ssh
filter   = sshd
logpath  = /var/log/auth.log
maxretry = 6

I'd change the "maxretry = 6" to a lower number (maxretry = 3). That way it will trigger the jail after 3 bad attempts instead of 6.

Then,

> sudo service fail2ban restart

---

### Post by VMOS on 2012-07-20
yeah, tried setting that at one, didn't make a difference

---

### Post by spynappels on 2012-07-20
Does fail2ban run as a specific user, and does that user have read access to the logs?

---

### Post by VMOS on 2012-07-23
yeah, fail2ban is running as root

---

### Post by byronical on 2012-08-07
Maybe this bug is the cause of your problem

[https://bugs.launchpad.net/ubuntu/+source/fail2ban/+bug/954453](https://bugs.launchpad.net/ubuntu/+source/fail2ban/+bug/954453)

---

### Post by VMOS on 2012-08-09
I figured it out, it was the darndest thing. Instead of powering the machine off every time I finished with it, one time I happened to leave it running overnight. The next day fail2ban started working.

I'm not 100% sure why this is, but I think it's something to do with the logs rotating as nothing else was scheduled to run overnight.

---


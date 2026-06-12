---
title: "fail2ban 8.7 | python 2.7.3 | ubuntu 12.04 | dovecot &amp; sasl not working ssl error"
date: 2013-01-01
forum: Server Platforms
---

### Post by 08x on 2013-01-01
New server, New install of ubuntu 12.04

```
python -V
```Python 2.7.3

Fail2Ban v0.8.7
Installed via
```
sudo apt-get install fail2ban
```Problem:
IP not banned for failed dovecot logins, dovecot, sasl not working others may not be working too
Test:
Fail login passwords on mail client on different device
When testing via fail2ban-regex it finds lines
```
/usr/bin/fail2ban-regex /var/log/mail.info /etc/fail2ban/filter.d/dovecot.conf
``````

Running tests
=============

Use regex file : /etc/fail2ban/filter.d/dovecot.conf
Use log file   : /var/log/mail.info


Results
=======

Failregex: 1 total
|- #) [# of hits] regular expression
|  1) [1] .*(?:pop3-login|imap-login):.*(?:Authentication failure|Aborted login \(auth failed|Aborted login \(tried to use disabled|Disconnected \(auth failed).*rip=(?P<host>\S*),.*
`-

Ignoreregex: 0 total

Summary
=======

Addresses found:
[1]
    XX.XXX.XX.XXX (Tue Jan 01 21:52:40 2013)

Date template hits:
2450 hit(s): MONTH Day Hour:Minute:Second

Success, the total number of match is X

However, look at the above section 'Running tests' which could contain important
information.
```Whitelisted?
IP is not whitelisted, atemped with other ips also
Anything banning?
proftp,ssh are working fine
log messages:

/var/log/mail.info
```
Jan  1 21:52:40 server1 dovecot: pop3-login: Aborted login (auth failed, 17 attempts in 12 secs): user=<no@account.com>, method=PLAIN, rip=XX.XXX.XX.XXX, lip=XX.XXX.XX.XXX, TLS, session=<uhfKJHGHGLHhgljh>
Jan  1 21:53:36 server1 dovecot: pop3-login: Aborted login (auth failed, 17 attempts in 12 secs): user=<no@account.com>, method=PLAIN, rip=XX.XXX.XX.XXX, lip=XX.XXX.XX.XXX, TLS, session=<uhfKJHGHGLHhgljh>
Jan  1 21:54:41 server1 dovecot: pop3-login: Aborted login (auth failed, 17 attempts in 12 secs): user=<no@account.com>, method=PLAIN, rip=XX.XXX.XX.XXX, lip=XX.XXX.XX.XXX, TLS, session=<uhfKJHGHGLHhgljh>

```Now the ip gets banned under fail2ban-ssh under pam auth fail from /var/log/auth.log
```
Jan  1 21:52:28 server1 auth: pam_unix(dovecot:auth): authentication failure; logname= uid=0 euid=0 tty=dovecot ruser=no@account.com rhost=XX.XXX.XX.XXX  user=no@account.com
```but isnt banned under dovecot filter

all filters are default with fail2ban 8.7 install

```

[DEFAULT]
ignoreip = 127.0.0.1/8
bantime  = 600
maxretry = 3
backend = auto
usedns = warn
destemail = protect@localhost
banaction = iptables-multiport
mta = sendmail
protocol = tcp
chain = INPUT
action_ = %(banaction)s[name=%(__name__)s, port="%(port)s", protocol="%(protocol)s", chain="%(chain)s"]
action_mw = %(banaction)s[name=%(__name__)s, port="%(port)s", protocol="%(protocol)s", chain="%(chain)s"]
              %(mta)s-whois[name=%(__name__)s, dest="%(destemail)s", protocol="%(protocol)s", chain="%(chain)s"]
action_mwl = %(banaction)s[name=%(__name__)s, port="%(port)s", protocol="%(protocol)s", chain="%(chain)s"]
               %(mta)s-whois-lines[name=%(__name__)s, dest="%(destemail)s", logpath=%(logpath)s, chain="%(chain)s"]
action = %(action_mwl)s
[ssh]

enabled  = true
port     = ssh
filter   = sshd
logpath  = /var/log/auth.log
maxretry = 3

[ssh-ddos]

enabled  = true
port     = ssh
filter   = sshd-ddos
logpath  = /var/log/auth.log
maxretry = 3

[apache]

enabled  = true
port     = http,https
filter   = apache-auth
logpath  = /var/log/apache*/*error.log
maxretry = 6

[apache-virtualmin]

enabled  = true
port     = http,https
filter   = apache-auth
logpath  = /var/log/virtualmin/*error.log
maxretry = 6

[apache-noscript]

enabled  = true
port     = http,https
filter   = apache-noscript
logpath  = /var/log/apache*/*error.log
maxretry = 6

[apache-overflows]

enabled  = true
port     = http,https
filter   = apache-overflows
logpath  = /var/log/apache*/*error.log
maxretry = 2

[apache-w00tw00t]

enabled  = true
filter   = apache-w00tw00t
logpath  = /var/log/apache*/*error.log
action   = iptables-allports[name=w00tw00t]
maxretry = 1

[apache-w00tw00t-vm]
enabled  = true
filter   = apache-w00tw00t
logpath  = /var/log/virtualmin/*error.log
action   = iptables-allports[name=w00tw00t-vm]
maxretry = 1

[apache-badbots]
enabled  = true
filter   = apache-badbots
port     = http,https
logpath  = /var/log/apache*/*access.log
maxretry = 1

[apache-badbots-vm]
enabled  = true
filter   = apache-badbots
port     = http,https
logpath  = /var/log/virtualmin/*access.log
maxretry = 1

[proftpd]

enabled  = ture
port     = ftp,ftp-data,ftps,ftps-data
filter   = proftpd
logpath  = /var/log/proftpd/proftpd.log
maxretry = 6

[postfix]

enabled  = true
port     = smtp,ssmtp
filter   = postfix
logpath  = /var/log/mail.log
maxretry = 3

[sasl]

enabled  = true
port     = smtp,ssmtp,imap2,imap3,imaps,pop3,pop3s
filter   = sasl
logpath  = /var/log/mail.log
maxretry = 3

[dovecot]

enabled = true
port    = smtp,ssmtp,imap2,imap3,imaps,pop3,pop3s
filter  = dovecot-pop3imap
logpath = /var/log/mail.log
maxretry = 3

[recidive]

enabled  = false
filter   = recidive
logpath  = /var/log/fail2ban.log
action   = iptables-allports[name=recidive]
           sendmail-whois-lines[name=recidive, logpath=/var/log/fail2ban.log]
bantime  = 604800  ; 1 week
findtime = 86400   ; 1 day
maxretry = 5


```When starting/restarting no errors or fails
/var/log/fail2ban.log
```
2013-01-01 23:57:51,806 fail2ban.server : INFO   Changed logging target to /var/log/fail2ban.log for Fail2ban v0.8.7
2013-01-01 23:57:51,806 fail2ban.jail   : INFO   Creating new jail 'ssh'
2013-01-01 23:57:51,828 fail2ban.jail   : INFO   Jail 'ssh' uses pyinotify
2013-01-01 23:57:51,841 fail2ban.jail   : INFO   Initiated 'pyinotify' backend
2013-01-01 23:57:51,842 fail2ban.filter : INFO   Added logfile = /var/log/auth.log
2013-01-01 23:57:51,843 fail2ban.filter : INFO   Set maxRetry = 3
2013-01-01 23:57:51,843 fail2ban.filter : INFO   Set findtime = 600
2013-01-01 23:57:51,844 fail2ban.actions: INFO   Set banTime = 600
2013-01-01 23:57:51,857 fail2ban.jail   : INFO   Creating new jail 'ssh-ddos'
2013-01-01 23:57:51,858 fail2ban.jail   : INFO   Jail 'ssh-ddos' uses pyinotify
2013-01-01 23:57:51,862 fail2ban.jail   : INFO   Initiated 'pyinotify' backend
2013-01-01 23:57:51,863 fail2ban.filter : INFO   Added logfile = /var/log/auth.log
2013-01-01 23:57:51,864 fail2ban.filter : INFO   Set maxRetry = 3
2013-01-01 23:57:51,864 fail2ban.filter : INFO   Set findtime = 600
2013-01-01 23:57:51,864 fail2ban.actions: INFO   Set banTime = 600
2013-01-01 23:57:51,870 fail2ban.jail   : INFO   Creating new jail 'apache'
2013-01-01 23:57:51,870 fail2ban.jail   : INFO   Jail 'apache' uses pyinotify
2013-01-01 23:57:51,874 fail2ban.jail   : INFO   Initiated 'pyinotify' backend
2013-01-01 23:57:51,875 fail2ban.filter : INFO   Added logfile = /var/log/apache2/error.log
2013-01-01 23:57:51,876 fail2ban.filter : INFO   Set maxRetry = 6
2013-01-01 23:57:51,876 fail2ban.filter : INFO   Set findtime = 600
2013-01-01 23:57:51,876 fail2ban.actions: INFO   Set banTime = 600
2013-01-01 23:57:51,882 fail2ban.jail   : INFO   Creating new jail 'apache-noscript'
2013-01-01 23:57:51,883 fail2ban.jail   : INFO   Jail 'apache-noscript' uses pyinotify
2013-01-01 23:57:51,887 fail2ban.jail   : INFO   Initiated 'pyinotify' backend
2013-01-01 23:57:51,889 fail2ban.filter : INFO   Added logfile = /var/log/apache2/error.log
2013-01-01 23:57:51,889 fail2ban.filter : INFO   Set maxRetry = 6
2013-01-01 23:57:51,890 fail2ban.filter : INFO   Set findtime = 600
2013-01-01 23:57:51,890 fail2ban.actions: INFO   Set banTime = 600
2013-01-01 23:57:51,897 fail2ban.jail   : INFO   Creating new jail 'apache-overflows'
2013-01-01 23:57:51,897 fail2ban.jail   : INFO   Jail 'apache-overflows' uses pyinotify
2013-01-01 23:57:51,902 fail2ban.jail   : INFO   Initiated 'pyinotify' backend
2013-01-01 23:57:51,903 fail2ban.filter : INFO   Added logfile = /var/log/apache2/error.log
2013-01-01 23:57:51,904 fail2ban.filter : INFO   Set maxRetry = 2
2013-01-01 23:57:51,904 fail2ban.filter : INFO   Set findtime = 600
2013-01-01 23:57:51,904 fail2ban.actions: INFO   Set banTime = 600
2013-01-01 23:57:51,910 fail2ban.jail   : INFO   Creating new jail 'proftpd'
2013-01-01 23:57:51,910 fail2ban.jail   : INFO   Jail 'proftpd' uses pyinotify
2013-01-01 23:57:51,914 fail2ban.jail   : INFO   Initiated 'pyinotify' backend
2013-01-01 23:57:51,915 fail2ban.filter : INFO   Added logfile = /var/log/proftpd/proftpd.log
2013-01-01 23:57:51,915 fail2ban.filter : INFO   Set maxRetry = 6
2013-01-01 23:57:51,916 fail2ban.filter : INFO   Set findtime = 600
2013-01-01 23:57:51,916 fail2ban.actions: INFO   Set banTime = 600
2013-01-01 23:57:51,924 fail2ban.jail   : INFO   Creating new jail 'postfix'
2013-01-01 23:57:51,924 fail2ban.jail   : INFO   Jail 'postfix' uses pyinotify
2013-01-01 23:57:51,928 fail2ban.jail   : INFO   Initiated 'pyinotify' backend
2013-01-01 23:57:51,929 fail2ban.filter : INFO   Added logfile = /var/log/mail.log
2013-01-01 23:57:51,930 fail2ban.filter : INFO   Set maxRetry = 3
2013-01-01 23:57:51,930 fail2ban.filter : INFO   Set findtime = 600
2013-01-01 23:57:51,930 fail2ban.actions: INFO   Set banTime = 600
2013-01-01 23:57:51,936 fail2ban.jail   : INFO   Creating new jail 'sasl'
2013-01-01 23:57:51,936 fail2ban.jail   : INFO   Jail 'sasl' uses pyinotify
2013-01-01 23:57:51,940 fail2ban.jail   : INFO   Initiated 'pyinotify' backend
2013-01-01 23:57:51,941 fail2ban.filter : INFO   Added logfile = /var/log/mail.log
2013-01-01 23:57:51,942 fail2ban.filter : INFO   Set maxRetry = 3
2013-01-01 23:57:51,942 fail2ban.filter : INFO   Set findtime = 600
2013-01-01 23:57:51,942 fail2ban.actions: INFO   Set banTime = 600
2013-01-01 23:57:51,948 fail2ban.jail   : INFO   Creating new jail 'dovecot'
2013-01-01 23:57:51,948 fail2ban.jail   : INFO   Jail 'dovecot' uses pyinotify
2013-01-01 23:57:51,952 fail2ban.jail   : INFO   Initiated 'pyinotify' backend
2013-01-01 23:57:51,953 fail2ban.filter : INFO   Added logfile = /var/log/mail.log
2013-01-01 23:57:51,953 fail2ban.filter : INFO   Set maxRetry = 3
2013-01-01 23:57:51,954 fail2ban.filter : INFO   Set findtime = 600
2013-01-01 23:57:51,954 fail2ban.actions: INFO   Set banTime = 600
2013-01-01 23:57:51,960 fail2ban.jail   : INFO   Creating new jail 'apache-virtualmin'
2013-01-01 23:57:51,960 fail2ban.jail   : INFO   Jail 'apache-virtualmin' uses pyinotify
2013-01-01 23:57:51,964 fail2ban.jail   : INFO   Initiated 'pyinotify' backend
2013-01-01 23:57:51,965 fail2ban.filter : INFO   Set maxRetry = 6
2013-01-01 23:57:51,966 fail2ban.filter : INFO   Set findtime = 600
2013-01-01 23:57:51,966 fail2ban.actions: INFO   Set banTime = 600
2013-01-01 23:57:51,971 fail2ban.jail   : INFO   Creating new jail 'apache-w00tw00t'
2013-01-01 23:57:51,971 fail2ban.jail   : INFO   Jail 'apache-w00tw00t' uses pyinotify
2013-01-01 23:57:51,975 fail2ban.jail   : INFO   Initiated 'pyinotify' backend
2013-01-01 23:57:51,976 fail2ban.filter : INFO   Added logfile = /var/log/apache2/error.log
2013-01-01 23:57:51,977 fail2ban.filter : INFO   Set maxRetry = 1
2013-01-01 23:57:51,977 fail2ban.filter : INFO   Set findtime = 600
2013-01-01 23:57:51,977 fail2ban.actions: INFO   Set banTime = 600
2013-01-01 23:57:51,980 fail2ban.jail   : INFO   Creating new jail 'apache-w00tw00t-vm'
2013-01-01 23:57:51,980 fail2ban.jail   : INFO   Jail 'apache-w00tw00t-vm' uses pyinotify
2013-01-01 23:57:51,985 fail2ban.jail   : INFO   Initiated 'pyinotify' backend
2013-01-01 23:57:51,985 fail2ban.filter : INFO   Set maxRetry = 1
2013-01-01 23:57:51,986 fail2ban.filter : INFO   Set findtime = 600
2013-01-01 23:57:51,986 fail2ban.actions: INFO   Set banTime = 600
2013-01-01 23:57:51,988 fail2ban.jail   : INFO   Creating new jail 'apache-badbots'
2013-01-01 23:57:51,988 fail2ban.jail   : INFO   Jail 'apache-badbots' uses pyinotify
2013-01-01 23:57:51,993 fail2ban.jail   : INFO   Initiated 'pyinotify' backend
2013-01-01 23:57:51,994 fail2ban.filter : INFO   Added logfile = /var/log/apache2/access.log
2013-01-01 23:57:51,994 fail2ban.filter : INFO   Added logfile = /var/log/apache2/other_vhosts_access.log
2013-01-01 23:57:51,995 fail2ban.filter : INFO   Set maxRetry = 1
2013-01-01 23:57:51,995 fail2ban.filter : INFO   Set findtime = 600
2013-01-01 23:57:51,995 fail2ban.actions: INFO   Set banTime = 600
2013-01-01 23:57:52,008 fail2ban.jail   : INFO   Creating new jail 'apache-badbots-vm'
2013-01-01 23:57:52,008 fail2ban.jail   : INFO   Jail 'apache-badbots-vm' uses pyinotify
2013-01-01 23:57:52,013 fail2ban.jail   : INFO   Initiated 'pyinotify' backend
2013-01-01 23:57:52,014 fail2ban.filter : INFO   Set maxRetry = 1
2013-01-01 23:57:52,014 fail2ban.filter : INFO   Set findtime = 600
2013-01-01 23:57:52,014 fail2ban.actions: INFO   Set banTime = 600
2013-01-01 23:57:52,020 fail2ban.jail   : INFO   Jail 'ssh' started
2013-01-01 23:57:52,022 fail2ban.jail   : INFO   Jail 'ssh-ddos' started
2013-01-01 23:57:52,024 fail2ban.jail   : INFO   Jail 'apache' started
2013-01-01 23:57:52,024 fail2ban.jail   : INFO   Jail 'apache-noscript' started
2013-01-01 23:57:52,026 fail2ban.jail   : INFO   Jail 'apache-overflows' started
2013-01-01 23:57:52,028 fail2ban.jail   : INFO   Jail 'proftpd' started
2013-01-01 23:57:52,029 fail2ban.jail   : INFO   Jail 'postfix' started
2013-01-01 23:57:52,030 fail2ban.jail   : INFO   Jail 'sasl' started
2013-01-01 23:57:52,030 fail2ban.jail   : INFO   Jail 'dovecot' started
2013-01-01 23:57:52,032 fail2ban.jail   : INFO   Jail 'apache-virtualmin' started
2013-01-01 23:57:52,033 fail2ban.jail   : INFO   Jail 'apache-w00tw00t' started
2013-01-01 23:57:52,034 fail2ban.jail   : INFO   Jail 'apache-w00tw00t-vm' started
2013-01-01 23:57:52,036 fail2ban.jail   : INFO   Jail 'apache-badbots' started
2013-01-01 23:57:52,038 fail2ban.jail   : INFO   Jail 'apache-badbots-vm' started

```thanks in advance

08x

---

### Post by 08x on 2013-01-02
Solved, ```
/var/log/mail.log
``` was empty using ```
/var/log/mail.info
``` fixed this

---


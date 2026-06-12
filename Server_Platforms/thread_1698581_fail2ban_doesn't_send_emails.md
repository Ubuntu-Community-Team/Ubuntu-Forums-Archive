---
title: "fail2ban doesn't send emails"
date: 2011-03-02
forum: Server Platforms
---

### Post by LeonHeart on 2011-03-02
Hi there,
I'm running an Ubuntu 10.10 x64 webserver.
Every service has been setup using ISP Manager Lite.
I've successfully installed fail2ban0.8.4-SVN to protect sshd from brute force attacks. fail2ban works like charm and it has blocked some attacker. My problem is that it's doesn't send me emails.
I use sendmail/dovecot on the server and the email I'm using in jail.conf is root@localhost.

My jail.conf is this:
```

# Fail2Ban configuration file.
#
# This file was composed for Debian systems from the original one
#  provided now under /usr/share/doc/fail2ban/examples/jail.conf
#  for additional examples.
#
# To avoid merges during upgrades DO NOT MODIFY THIS FILE
# and rather provide your changes in /etc/fail2ban/jail.local
#
# Author: Yaroslav O. Halchenko <debian@onerussian.com>
#
# $Revision: 281 $
#

# The DEFAULT allows a global definition of the options. They can be override
# in each jail afterwards.

[DEFAULT]

# "ignoreip" can be an IP address, a CIDR mask or a DNS host
ignoreip = --REMOVED IPS--
findtime = 1800
bantime  = 172800
maxretry = 3

# "backend" specifies the backend used to get files modification. Available
# options are "gamin", "polling" and "auto".
# yoh: For some reason Debian shipped python-gamin didn't work as expected
#      This issue left ToDo, so polling is default backend for now
backend = polling

#
# Destination email address used solely for the interpolations in
# jail.{conf,local} configuration files.
destemail = root@localhost

#
# ACTIONS
#

# Default banning action (e.g. iptables, iptables-new,
# iptables-multiport, shorewall, etc) It is used to define
# action_* variables. Can be overriden globally or per
# section within jail.local file
banaction = iptables-multiport

# email action. Since 0.8.1 upstream fail2ban uses sendmail
# MTA for the mailing. Change mta configuration parameter to mail
# if you want to revert to conventional 'mail'.
mta = sendmail

# Default protocol
protocol = tcp

#
# Action shortcuts. To be used to define action parameter

# The simplest action to take: ban only
action_ = %(banaction)s[name=%(__name__)s, port="%(port)s", protocol="%(protocol)s]

# ban & send an e-mail with whois report to the destemail.
action_mw = %(banaction)s[name=%(__name__)s, port="%(port)s", protocol="%(protocol)s]
              %(mta)s-whois[name=%(__name__)s, dest="%(destemail)s", protocol="%(protocol)s]

# ban & send an e-mail with whois report and relevant log lines
# to the destemail.
action_mwl = %(banaction)s[name=%(__name__)s, port="%(port)s", protocol="%(protocol)s]
               %(mta)s-whois-lines[name=%(__name__)s, dest="%(destemail)s", logpath=%(logpath)s]

# Choose default action.  To change, just override value of 'action' with the
# interpolation to the chosen action shortcut (e.g.  action_mw, action_mwl, etc) in jail.local
# globally (section [DEFAULT]) or per specific section
action = %(action_)s

#
# JAILS
#

# Next jails corresponds to the standard configuration in Fail2ban 0.6 which
# was shipped in Debian. Enable any defined here jail by including
#
# [SECTION_NAME]
# enabled = true

#
#
# in /etc/fail2ban/jail.local.
#
# Optionally you may override any other parameter (e.g. banaction,
# action, port, logpath, etc) in that section within jail.local

[ssh]

enabled = true
port    = ssh
filter  = sshd
logpath  = /var/log/auth.log
maxretry = 3
```

Am I doing something wrong?

---

### Post by stlsaint on 2011-03-02
You are using root@localhost as a email account to have email sent too??#-o

Can you explain how you setup your mail server and what ocnfig you used to setup mail in fail2ban. Also ive read that installing mailx helps fix issues if you have a correctly setup mail server.

---

### Post by LeonHeart on 2011-03-02
> **stlsaint said:**
> You are using root@localhost as a email account to have email sent too??#-o

Can you explain how you setup your mail server and what ocnfig you used to setup mail in fail2ban. Also ive read that installing mailx helps fix issues if you have a correctly setup mail server.

On a Fedora 14 x64 machine using root@localhost works and sends the mail to the root account. I've tried using my Gmail address but I never get notified. As I told I use dovecot/sendmail. Both are working fine and they are handled by ISPManger so that I don't have to deal with the config files.

---

### Post by LeonHeart on 2011-03-02
If you'd like me to upload any specific configuration file please let me know.

---

### Post by LeonHeart on 2011-03-03
```
action = %(action_)s
```
That little line, I hate that line!!!

This line should be ```
action = %(action_mwl)s
``` or ```
action = %(action_mw)s
```
By default fail2ban is configured **not** to send any mails. I didn't notice that line until recently.
I feel stupid.

By the way, stlsaint, my destemail is set to root@localhost and I receive my mail notifications without any problems.

---

### Post by stlsaint on 2011-03-05
Good to know!

---


---
title: "Setting up fail2ban"
date: 2010-02-03
forum: Security
---

### Post by fisheater on 2010-02-03
Hi all,

I have set up my ubuntu 9.04 desktop as my Nx Nomachine server.

Then, on the advice of a forum post, have installed fail2ban and tweaked the jail.conf file (sudo gedit /etc/fail2ban/jail.conf) on one line:
WAS: bantime: 600, TO: bantime:600, and NOW: bantime: 21600.

I have had some people banned

```
2010-01-31 16:59:21,315 fail2ban.actions: WARNING [ssh] Ban 123.196.117.99
2010-01-31 17:17:59,515 fail2ban.actions: WARNING [ssh] Ban 69.8.113.104
2010-01-31 18:39:21,725 fail2ban.actions: WARNING [ssh] Unban 123.196.117.99
2010-01-31 18:57:59,960 fail2ban.actions: WARNING [ssh] Unban 69.8.113.104
2010-01-31 22:52:58,228 fail2ban.actions: WARNING [ssh] Ban 85.17.200.81
2010-01-31 23:35:05,958 fail2ban.actions: WARNING [ssh] Ban 61.152.217.77
2010-02-01 00:32:58,724 fail2ban.actions: WARNING [ssh] Unban 85.17.200.81
2010-02-01 01:15:06,403 fail2ban.actions: WARNING [ssh] Unban 61.152.217.77
2010-02-01 12:20:51,094 fail2ban.actions: WARNING [ssh] Ban 217.16.83.178
2010-02-01 12:47:53,883 fail2ban.actions: WARNING [ssh] Ban 59.46.39.204
2010-02-01 13:45:30,659 fail2ban.actions: WARNING [ssh] Ban 118.129.153.43
2010-02-01 14:00:51,666 fail2ban.actions: WARNING [ssh] Unban 217.16.83.178
2010-02-01 14:27:54,424 fail2ban.actions: WARNING [ssh] Unban 59.46.39.204
2010-02-01 15:25:31,200 fail2ban.actions: WARNING [ssh] Unban 118.129.153.43
2010-02-02 02:26:09,940 fail2ban.actions: WARNING [ssh] Ban 125.141.237.100
2010-02-02 04:06:10,363 fail2ban.actions: WARNING [ssh] Unban 125.141.237.100
2010-02-02 19:44:33,590 fail2ban.actions: WARNING [ssh] Ban 59.46.39.204
2010-02-02 21:24:34,095 fail2ban.actions: WARNING [ssh] Unban 59.46.39.204
2010-02-02 22:47:33,496 fail2ban.actions: WARNING [ssh] Ban 220.181.39.192
2010-02-03 00:27:33,990 fail2ban.actions: WARNING [ssh] Unban 220.181.39.192
2010-02-03 11:27:56,332 fail2ban.actions: WARNING [ssh] Ban 113.57.252.24
2010-02-03 13:07:57,038 fail2ban.actions: WARNING [ssh] Unban 113.57.252.24
2010-02-03 13:18:23,905 fail2ban.actions: WARNING [ssh] Ban 211.78.18.89
2010-02-03 14:58:24,459 fail2ban.actions: WARNING [ssh] Unban 211.78.18.89
2010-02-03 18:24:36,746 fail2ban.actions: WARNING [ssh] Ban 61.129.60.23
2010-02-03 20:04:37,190 fail2ban.actions: WARNING [ssh] Unban 61.129.60.23
```

but now this is the message i get in my fail2ban logs

```
2010-02-03 20:45:00,053 fail2ban.jail   : INFO   Jail 'ssh' stopped
2010-02-03 20:45:00,053 fail2ban.server : INFO   Exiting Fail2ban
2010-02-03 20:46:13,619 fail2ban.server : INFO   Changed logging target to /var/log/fail2ban.log for Fail2ban v0.8.3
2010-02-03 20:46:13,631 fail2ban.jail   : INFO   Creating new jail 'ssh'
2010-02-03 20:46:13,631 fail2ban.jail   : INFO   Jail 'ssh' uses poller
2010-02-03 20:46:13,734 fail2ban.server : ERROR  Unexpected communication error
2010-02-03 20:46:13,745 fail2ban.filter : INFO   Added logfile = /var/log/auth.log
2010-02-03 20:46:13,746 fail2ban.filter : INFO   Set maxRetry = 4
2010-02-03 20:46:13,747 fail2ban.filter : INFO   Set findtime = 600
2010-02-03 20:46:13,748 fail2ban.actions: INFO   Set banTime = 21600
2010-02-03 20:46:13,760 fail2ban.server : ERROR  Unexpected communication error
2010-02-03 20:46:13,765 fail2ban.server : ERROR  Unexpected communication error
2010-02-03 20:46:13,770 fail2ban.server : ERROR  Unexpected communication error
2010-02-03 20:46:13,775 fail2ban.server : ERROR  Unexpected communication error
2010-02-03 20:46:13,796 fail2ban.server : ERROR  Unexpected communication error
2010-02-03 20:46:13,804 fail2ban.server : ERROR  Unexpected communication error
2010-02-03 20:46:13,812 fail2ban.server : ERROR  Unexpected communication error
2010-02-03 20:46:13,820 fail2ban.server : ERROR  Unexpected communication error
2010-02-03 20:46:13,821 fail2ban.server : ERROR  Unexpected communication error
2010-02-03 20:46:13,822 fail2ban.server : ERROR  Unexpected communication error
2010-02-03 20:46:13,822 fail2ban.server : ERROR  Unexpected communication error
2010-02-03 20:46:13,823 fail2ban.server : ERROR  Unexpected communication error
2010-02-03 20:46:13,823 fail2ban.server : ERROR  Unexpected communication error
2010-02-03 20:46:13,840 fail2ban.server : ERROR  Unexpected communication error
2010-02-03 20:46:13,841 fail2ban.server : ERROR  Unexpected communication error
2010-02-03 20:46:13,842 fail2ban.server : ERROR  Unexpected communication error
2010-02-03 20:46:13,842 fail2ban.server : ERROR  Unexpected communication error
2010-02-03 20:46:13,903 fail2ban.jail   : INFO   Jail 'ssh' started
2010-02-03 20:46:13,927 fail2ban.server : ERROR  Unexpected communication error

```

I am very new at this type of dabbling with security, text editing, and the like. My question is: is my set up secure (enough) and have my changes to my fail2ban jail.conf improved my security (by having a longer ban time) or have I stuffed it up and made my system less secure!?

Just rereading the into to my jail file, i have already made an error...

```
# To avoid merges during upgrades DO NOT MODIFY THIS FILE
# and rather provide your changes in /etc/fail2ban/jail.local
```

I have been modifying the jail.conf rather than making or modifying jail.local. Oops. I will make the same changes to that file.

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
ignoreip = 127.0.0.1
# changed - 6hr ban
bantime  = 21600
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
# in /etc/fail2ban/jail.local.
#
# Optionally you may override any other parameter (e.g. banaction,
# action, port, logpath, etc) in that section within jail.local

[ssh]

enabled = true
port	= ssh
filter	= sshd
logpath  = /var/log/auth.log
maxretry = 4

# Generic filter for pam. Has to be used with action which bans all ports
# such as iptables-allports, shorewall
[pam-generic]

enabled = false
# pam-generic filter can be customized to monitor specific subset of 'tty's
filter	= pam-generic
# port actually must be irrelevant but lets leave it all for some possible uses
port = all
banaction = iptables-allports
port     = anyport
logpath  = /var/log/auth.log
maxretry = 4

[xinetd-fail]

enabled   = false
filter    = xinetd-fail
port      = all
banaction = iptables-multiport-log
logpath   = /var/log/daemon.log
maxretry  = 2


[ssh-ddos]

enabled = false
port    = ssh
filter  = sshd-ddos
logpath  = /var/log/auth.log
maxretry = 4

#
# HTTP servers
#

[apache]

enabled = false
port	= http,https
filter	= apache-auth
logpath = /var/log/apache*/*error.log
maxretry = 4

# default action is now multiport, so apache-multiport jail was left
# for compatibility with previous (<0.7.6-2) releases
[apache-multiport]

enabled   = false
port	  = http,https
filter	  = apache-auth
logpath   = /var/log/apache*/*error.log
maxretry  = 4

[apache-noscript]

enabled = false
port    = http,https
filter  = apache-noscript
logpath = /var/log/apache*/*error.log
maxretry = 6

[apache-overflows]

enabled = false
port    = http,https
filter  = apache-overflows
logpath = /var/log/apache*/*error.log
maxretry = 2

#
# FTP servers
#

[vsftpd]

enabled  = false
port	 = ftp,ftp-data,ftps,ftps-data
filter   = vsftpd
logpath  = /var/log/vsftpd.log
# or overwrite it in jails.local to be
# logpath = /var/log/auth.log
# if you want to rely on PAM failed login attempts
# vsftpd's failregex should match both of those formats
maxretry = 6


[proftpd]

enabled  = false
port	 = ftp,ftp-data,ftps,ftps-data
filter   = proftpd
logpath  = /var/log/proftpd/proftpd.log
maxretry = 6


[wuftpd]

enabled  = false
port	 = ftp,ftp-data,ftps,ftps-data
filter   = wuftpd
logpath  = /var/log/auth.log
maxretry = 6


#
# Mail servers
#

[postfix]

enabled  = false
port	 = smtp,ssmtp
filter   = postfix
logpath  = /var/log/mail.log


[couriersmtp]

enabled  = false
port	 = smtp,ssmtp
filter   = couriersmtp
logpath  = /var/log/mail.log


#
# Mail servers authenticators: might be used for smtp,ftp,imap servers, so
# all relevant ports get banned
#

[courierauth]

enabled  = false
port	 = smtp,ssmtp,imap2,imap3,imaps,pop3,pop3s
filter   = courierlogin
logpath  = /var/log/mail.log


[sasl]

enabled  = false
port	 = smtp,ssmtp,imap2,imap3,imaps,pop3,pop3s
filter   = sasl
logpath  = /var/log/mail.log


# DNS Servers


# These jails block attacks against named (bind9). By default, logging is off
# with bind9 installation. You will need something like this:
#
# logging {
#     channel security_file {
#         file "/var/log/named/security.log" versions 3 size 30m;
#         severity dynamic;
#         print-time yes;
#     };
#     category security {
#         security_file;
#     };
# }
#
# in your named.conf to provide proper logging

# Word of Caution:
# Given filter can lead to DoS attack against your DNS server
# since there is no way to assure that UDP packets come from the
# real source IP
[named-refused-udp]

enabled  = false
port     = domain,953
protocol = udp
filter   = named-refused
logpath  = /var/log/named/security.log

[named-refused-tcp]

enabled  = false
port     = domain,953
protocol = tcp
filter   = named-refused
logpath  = /var/log/named/security.log

```

Thanks for your input and keeping me out of trouble on the web.

FE

---

### Post by wolfgang.rumpf on 2011-02-06
Since it looks like you were trouble-shooting fail2ban I was hoping you could help me out - I think I have fail2ban installed properly, but the log file shows an error:

ERROR  iptables -D INPUT -p tcp -m multiport --dports ssh -j fail2ban-ssh
iptables -F fail2ban-ssh
iptables -X fail2ban-ssh returned 100

Does this mean fail2ban can't access iptables?

---

### Post by rudelgurke on 2011-02-06
> **fisheater said:**
> Thanks for your input and keeping me out of trouble on the web.

Hmm - if you want to be kept out of trouble, why not setup your SSH daemon first properly ? Then you'll notice Fail2ban is a waste of time and even increasing the risk for your server.

Speaking of:  [http://www.ossec.net/main/attacking-log-analysis-tools](http://www.ossec.net/main/attacking-log-analysis-tools)  as example.

Meanwhile this error has been fixed, yes, still this example shows that the more complex things are, the more errors there may be.  So, take care first of your SSH server by enabling publick key authentication, setting up the other options and then watch the bots trying to bruteforce failing. If it still gets annoying, change the port though this just keeps the logfiles more clean, it doesn't improve security.

---

### Post by b01 on 2011-10-23
> **rudelgurke said:**
> Hmm - if you want to be kept out of trouble, why not setup your SSH daemon first properly ? Then you'll notice Fail2ban is a waste of time and even increasing the risk for your server.

Your first point is true, PKs for brute-force SSH prevention. But your second is nonsense since PKs provide no protection against SSH DoS, or privilege elevation attacks. Various layers of well-configured intrusion-prevention and detection can really help protect a server. Fail2ban is a valid option, though not a miracle tool. Use it well and it will serve you well.

Also, do you do nothing about brute-force FTP or SMTP attacks on a shared hosting server?

---

### Post by nothingspecial on 2011-10-23
And we bid you goodnight, goodnight, goodnight.......

---


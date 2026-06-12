---
title: "Please check my fail2ban settings, I don't think it's blocking properly."
date: 2014-03-03
forum: Security
---

### Post by stchman on 2014-03-03
Hello all.  I have an ssh server running on my home network, and have fail2ban installed.

I am running Ubuntu 13.10.  It looks like that the 3 retries isn't working.

Here is my jail.local file:

```

# Fail2Ban configuration file.
#
# This file was composed for Debian systems from the original one
# provided now under /usr/share/doc/fail2ban/examples/jail.conf
# for additional examples.
#
# Comments: use '#' for comment lines and ';' for inline comments
#
# To avoid merges during upgrades DO NOT MODIFY THIS FILE
# and rather provide your changes in /etc/fail2ban/jail.local
#

# The DEFAULT allows a global definition of the options. They can be overridden
# in each jail afterwards.

[DEFAULT]

# "ignoreip" can be an IP address, a CIDR mask or a DNS host. Fail2ban will not
# ban a host which matches an address in this list. Several addresses can be
# defined using space separator.
ignoreip = 127.0.0.1/8 192.168.1.0/24

# "bantime" is the number of seconds that a host is banned.
#bantime  = 3600
bantime = 259200

# A host is banned if it has generated "maxretry" during the last "findtime"
# seconds.
findtime = 600
maxretry = 3

# "backend" specifies the backend used to get files modification.
# Available options are "pyinotify", "gamin", "polling" and "auto".
# This option can be overridden in each jail as well.
#
# pyinotify: requires pyinotify (a file alteration monitor) to be installed.
#            If pyinotify is not installed, Fail2ban will use auto.
# gamin:     requires Gamin (a file alteration monitor) to be installed.
#            If Gamin is not installed, Fail2ban will use auto.
# polling:   uses a polling algorithm which does not require external libraries.
# auto:      will try to use the following backends, in order:
#            pyinotify, gamin, polling.
backend = auto

# "usedns" specifies if jails should trust hostnames in logs,
#   warn when reverse DNS lookups are performed, or ignore all hostnames in logs
#
# yes:   if a hostname is encountered, a reverse DNS lookup will be performed.
# warn:  if a hostname is encountered, a reverse DNS lookup will be performed,
#        but it will be logged as a warning.
# no:    if a hostname is encountered, will not be used for banning,
#        but it will be logged as info.
usedns = warn

#
# Destination email address used solely for the interpolations in
# jail.{conf,local} configuration files.
destemail = root@localhost

#
# ACTIONS
#

# Default banning action (e.g. iptables, iptables-new,
# iptables-multiport, shorewall, etc) It is used to define
# action_* variables. Can be overridden globally or per
# section within jail.local file
banaction = iptables-multiport

# email action. Since 0.8.1 upstream fail2ban uses sendmail
# MTA for the mailing. Change mta configuration parameter to mail
# if you want to revert to conventional 'mail'.
mta = sendmail

# Default protocol
protocol = tcp

# Specify chain where jumps would need to be added in iptables-* actions
chain = INPUT

#
# Action shortcuts. To be used to define action parameter

# The simplest action to take: ban only
action_ = %(banaction)s[name=%(__name__)s, port="%(port)s", protocol="%(protocol)s", chain="%(chain)s"]

# ban & send an e-mail with whois report to the destemail.
action_mw = %(banaction)s[name=%(__name__)s, port="%(port)s", protocol="%(protocol)s", chain="%(chain)s"]
              %(mta)s-whois[name=%(__name__)s, dest="%(destemail)s", protocol="%(protocol)s", chain="%(chain)s"]

# ban & send an e-mail with whois report and relevant log lines
# to the destemail.
action_mwl = %(banaction)s[name=%(__name__)s, port="%(port)s", protocol="%(protocol)s", chain="%(chain)s"]
               %(mta)s-whois-lines[name=%(__name__)s, dest="%(destemail)s", logpath=%(logpath)s, chain="%(chain)s"]

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

enabled  = true
port     = ssh
filter   = sshd
logpath  = /var/log/auth.log
maxretry = 3

[dropbear]

enabled  = false
port     = ssh
filter   = sshd
logpath  = /var/log/dropbear
maxretry = 6

# Generic filter for pam. Has to be used with action which bans all ports
# such as iptables-allports, shorewall
[pam-generic]

enabled  = false
# pam-generic filter can be customized to monitor specific subset of 'tty's
filter   = pam-generic
# port actually must be irrelevant but lets leave it all for some possible uses
port     = all
banaction = iptables-allports
port     = anyport
logpath  = /var/log/auth.log
maxretry = 6

[xinetd-fail]

enabled   = false
filter    = xinetd-fail
port      = all
banaction = iptables-multiport-log
logpath   = /var/log/daemon.log
maxretry  = 2


[ssh-ddos]

enabled  = false
port     = ssh
filter   = sshd-ddos
logpath  = /var/log/auth.log
maxretry = 3


# Here we use blackhole routes for not requiring any additional kernel support
# to store large volumes of banned IPs

[ssh-route]

enabled = false
filter = sshd
action = route
logpath = /var/log/sshd.log
maxretry = 3

# Here we use a combination of Netfilter/Iptables and IPsets
# for storing large volumes of banned IPs
#
# IPset comes in two versions. See ipset -V for which one to use
# requires the ipset package and kernel support.
[ssh-iptables-ipset4]

enabled  = false
port     = ssh
filter   = sshd
banaction = iptables-ipset-proto4
logpath  = /var/log/sshd.log
maxretry = 3

[ssh-iptables-ipset6]

enabled  = false
port     = ssh
filter   = sshd
banaction = iptables-ipset-proto6
logpath  = /var/log/sshd.log
maxretry = 3


#
# HTTP servers
#

[apache]

enabled  = false
port     = http,https
filter   = apache-auth
logpath  = /var/log/apache*/*error.log
maxretry = 3

# default action is now multiport, so apache-multiport jail was left
# for compatibility with previous (<0.7.6-2) releases
[apache-multiport]

enabled   = false
port      = http,https
filter    = apache-auth
logpath   = /var/log/apache*/*error.log
maxretry  = 6

[apache-noscript]

enabled  = false
port     = http,https
filter   = apache-noscript
logpath  = /var/log/apache*/*error.log
maxretry = 6

[apache-overflows]

enabled  = false
port     = http,https
filter   = apache-overflows
logpath  = /var/log/apache*/*error.log
maxretry = 2

# Ban attackers that try to use PHP's URL-fopen() functionality
# through GET/POST variables. - Experimental, with more than a year
# of usage in production environments.

[php-url-fopen]

enabled = false
port    = http,https
filter  = php-url-fopen
logpath = /var/www/*/logs/access_log

# A simple PHP-fastcgi jail which works with lighttpd.
# If you run a lighttpd server, then you probably will
# find these kinds of messages in your error_log:
#   ALERT &#8211; tried to register forbidden variable &#8216;GLOBALS&#8217;
#   through GET variables (attacker '1.2.3.4', file '/var/www/default/htdocs/index.php')

[lighttpd-fastcgi]

enabled = false
port    = http,https
filter  = lighttpd-fastcgi
logpath = /var/log/lighttpd/error.log

# Same as above for mod_auth
# It catches wrong authentifications

[lighttpd-auth]

enabled = false
port    = http,https
filter  = lighttpd-auth
logpath = /var/log/lighttpd/error.log

# Monitor roundcube server

[roundcube-auth]

enabled  = false
filter   = roundcube-auth
port     = http,https
logpath  = /var/log/roundcube/userlogins


[sogo-auth]

enabled  = false
filter   = sogo-auth
port     = http, https
# without proxy this would be:
# port    = 20000
logpath  = /var/log/sogo/sogo.log


#
# FTP servers
#

[vsftpd]

enabled  = false
port     = ftp,ftp-data,ftps,ftps-data
filter   = vsftpd
logpath  = /var/log/vsftpd.log
# or overwrite it in jails.local to be
# logpath = /var/log/auth.log
# if you want to rely on PAM failed login attempts
# vsftpd's failregex should match both of those formats
maxretry = 6


[proftpd]

enabled  = false
port     = ftp,ftp-data,ftps,ftps-data
filter   = proftpd
logpath  = /var/log/proftpd/proftpd.log
maxretry = 3


[pure-ftpd]

enabled  = false
port     = ftp,ftp-data,ftps,ftps-data
filter   = pure-ftpd
logpath  = /var/log/syslog
maxretry = 3


[wuftpd]

enabled  = false
port     = ftp,ftp-data,ftps,ftps-data
filter   = wuftpd
logpath  = /var/log/syslog
maxretry = 3


#
# Mail servers
#

[postfix]

enabled  = false
port     = smtp,ssmtp,submission
filter   = postfix
logpath  = /var/log/mail.log


[couriersmtp]

enabled  = false
port     = smtp,ssmtp,submission
filter   = couriersmtp
logpath  = /var/log/mail.log


#
# Mail servers authenticators: might be used for smtp,ftp,imap servers, so
# all relevant ports get banned
#

[courierauth]

enabled  = false
port     = smtp,ssmtp,submission,imap2,imap3,imaps,pop3,pop3s
filter   = courierlogin
logpath  = /var/log/mail.log


[sasl]

enabled  = false
port     = smtp,ssmtp,submission,imap2,imap3,imaps,pop3,pop3s
filter   = sasl
# You might consider monitoring /var/log/mail.warn instead if you are
# running postfix since it would provide the same log lines at the
# "warn" level but overall at the smaller filesize.
logpath  = /var/log/mail.log

[dovecot]

enabled = false
port    = smtp,ssmtp,submission,imap2,imap3,imaps,pop3,pop3s
filter  = dovecot
logpath = /var/log/mail.log

# To log wrong MySQL access attempts add to /etc/my.cnf:
# log-error=/var/log/mysqld.log
# log-warning = 2
[mysqld-auth]

enabled  = false
filter   = mysqld-auth
port     = 3306
logpath  = /var/log/mysqld.log


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
# };
#
# in your named.conf to provide proper logging

# !!! WARNING !!!
#   Since UDP is connection-less protocol, spoofing of IP and imitation
#   of illegal actions is way too simple.  Thus enabling of this filter
#   might provide an easy way for implementing a DoS against a chosen
#   victim. See
#    http://nion.modprobe.de/blog/archives/690-fail2ban-+-dns-fail.html
#   Please DO NOT USE this jail unless you know what you are doing.
#[named-refused-udp]
#
#enabled  = false
#port     = domain,953
#protocol = udp
#filter   = named-refused
#logpath  = /var/log/named/security.log

[named-refused-tcp]

enabled  = false
port     = domain,953
protocol = tcp
filter   = named-refused
logpath  = /var/log/named/security.log


# Multiple jails, 1 per protocol, are necessary ATM:
# see https://github.com/fail2ban/fail2ban/issues/37
[asterisk-tcp]

enabled  = false
filter   = asterisk
port     = 5060,5061
protocol = tcp
logpath  = /var/log/asterisk/messages

[asterisk-udp]

enabled  = false
filter     = asterisk
port     = 5060,5061
protocol = udp
logpath  = /var/log/asterisk/messages


# Jail for more extended banning of persistent abusers
# !!! WARNING !!!
#   Make sure that your loglevel specified in fail2ban.conf/.local
#   is not at DEBUG level -- which might then cause fail2ban to fall into
#   an infinite loop constantly feeding itself with non-informative lines
[recidive]

enabled  = false
filter   = recidive
logpath  = /var/log/fail2ban.log
action   = iptables-allports[name=recidive]
           sendmail-whois-lines[name=recidive, logpath=/var/log/fail2ban.log]
bantime  = 604800  ; 1 week
findtime = 86400   ; 1 day
maxretry = 5

```

This is my latest auth.log file:

```

Mar  2 07:56:36 andoria sshd[13876]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=71.91.238.165  user=backup
Mar  2 07:56:38 andoria sshd[13876]: Failed password for backup from 71.91.238.165 port 51805 ssh2
Mar  2 07:56:38 andoria sshd[13876]: Connection closed by 71.91.238.165 [preauth]
Mar  2 08:17:01 andoria CRON[13884]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  2 08:17:01 andoria CRON[13884]: pam_unix(cron:session): session closed for user root
Mar  2 08:41:00 andoria sshd[13894]: Invalid user mysql from 71.91.238.165
Mar  2 08:41:00 andoria sshd[13894]: input_userauth_request: invalid user mysql [preauth]
Mar  2 08:41:00 andoria sshd[13894]: pam_unix(sshd:auth): check pass; user unknown
Mar  2 08:41:00 andoria sshd[13894]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=71.91.238.165 
Mar  2 08:41:02 andoria sshd[13894]: Failed password for invalid user mysql from 71.91.238.165 port 54583 ssh2
Mar  2 08:41:02 andoria sshd[13894]: Connection closed by 71.91.238.165 [preauth]
Mar  2 09:17:01 andoria CRON[13906]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  2 09:17:01 andoria CRON[13906]: pam_unix(cron:session): session closed for user root
Mar  2 09:25:34 andoria sshd[13912]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=71.91.238.165  user=nobody
Mar  2 09:25:36 andoria sshd[13912]: Failed password for nobody from 71.91.238.165 port 44439 ssh2
Mar  2 09:25:36 andoria sshd[13912]: Connection closed by 71.91.238.165 [preauth]
Mar  2 10:10:01 andoria sshd[13932]: Invalid user office from 71.91.238.165
Mar  2 10:10:01 andoria sshd[13932]: input_userauth_request: invalid user office [preauth]
Mar  2 10:10:01 andoria sshd[13932]: pam_unix(sshd:auth): check pass; user unknown
Mar  2 10:10:01 andoria sshd[13932]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=71.91.238.165 
Mar  2 10:10:03 andoria sshd[13932]: Failed password for invalid user office from 71.91.238.165 port 51326 ssh2
Mar  2 10:10:03 andoria sshd[13932]: Connection closed by 71.91.238.165 [preauth]
Mar  2 10:17:01 andoria CRON[13936]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  2 10:17:01 andoria CRON[13936]: pam_unix(cron:session): session closed for user root
Mar  2 10:54:50 andoria sshd[13949]: Invalid user oracle from 71.91.238.165
Mar  2 10:54:50 andoria sshd[13949]: input_userauth_request: invalid user oracle [preauth]
Mar  2 10:54:50 andoria sshd[13949]: pam_unix(sshd:auth): check pass; user unknown
Mar  2 10:54:50 andoria sshd[13949]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=71.91.238.165 
Mar  2 10:54:51 andoria sshd[13949]: Failed password for invalid user oracle from 71.91.238.165 port 46062 ssh2
Mar  2 10:54:51 andoria sshd[13949]: Connection closed by 71.91.238.165 [preauth]
Mar  2 11:17:01 andoria CRON[13958]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  2 11:17:01 andoria CRON[13958]: pam_unix(cron:session): session closed for user root
Mar  2 11:39:04 andoria sshd[13967]: Invalid user pentadbir from 71.91.238.165
Mar  2 11:39:04 andoria sshd[13967]: input_userauth_request: invalid user pentadbir [preauth]
Mar  2 11:39:04 andoria sshd[13967]: pam_unix(sshd:auth): check pass; user unknown
Mar  2 11:39:04 andoria sshd[13967]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=71.91.238.165 
Mar  2 11:39:06 andoria sshd[13967]: Failed password for invalid user pentadbir from 71.91.238.165 port 58296 ssh2
Mar  2 11:39:06 andoria sshd[13967]: Connection closed by 71.91.238.165 [preauth]
Mar  2 12:17:01 andoria CRON[13980]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  2 12:17:01 andoria CRON[13980]: pam_unix(cron:session): session closed for user root
Mar  2 12:24:42 andoria sshd[13985]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=71.91.238.165  user=root
Mar  2 12:24:44 andoria sshd[13985]: Failed password for root from 71.91.238.165 port 44085 ssh2
Mar  2 12:24:48  sshd[13985]: last message repeated 2 times
Mar  2 12:24:48 andoria sshd[13985]: Connection closed by 71.91.238.165 [preauth]
Mar  2 12:24:48 andoria sshd[13985]: PAM 2 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=71.91.238.165  user=root
Mar  2 13:09:52 andoria sshd[14023]: Invalid user sales from 71.91.238.165
Mar  2 13:09:52 andoria sshd[14023]: input_userauth_request: invalid user sales [preauth]
Mar  2 13:09:52 andoria sshd[14023]: pam_unix(sshd:auth): check pass; user unknown
Mar  2 13:09:52 andoria sshd[14023]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=71.91.238.165 
Mar  2 13:09:53 andoria sshd[14023]: Failed password for invalid user sales from 71.91.238.165 port 41536 ssh2
Mar  2 13:09:53 andoria sshd[14023]: Connection closed by 71.91.238.165 [preauth]
Mar  2 13:17:01 andoria CRON[14031]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  2 13:17:01 andoria CRON[14031]: pam_unix(cron:session): session closed for user root
Mar  2 13:54:19 andoria sshd[14050]: Invalid user skrbnik from 71.91.238.165
Mar  2 13:54:19 andoria sshd[14050]: input_userauth_request: invalid user skrbnik [preauth]
Mar  2 13:54:19 andoria sshd[14050]: pam_unix(sshd:auth): check pass; user unknown
Mar  2 13:54:19 andoria sshd[14050]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=71.91.238.165 
Mar  2 13:54:22 andoria sshd[14050]: Failed password for invalid user skrbnik from 71.91.238.165 port 60249 ssh2
Mar  2 13:54:22 andoria sshd[14050]: Connection closed by 71.91.238.165 [preauth]
Mar  2 14:17:01 andoria CRON[14069]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  2 14:17:01 andoria CRON[14069]: pam_unix(cron:session): session closed for user root
Mar  2 14:38:58 andoria sshd[14101]: Invalid user spravce from 71.91.238.165
Mar  2 14:38:58 andoria sshd[14101]: input_userauth_request: invalid user spravce [preauth]
Mar  2 14:38:58 andoria sshd[14101]: pam_unix(sshd:auth): check pass; user unknown
Mar  2 14:38:58 andoria sshd[14101]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=71.91.238.165 
Mar  2 14:39:00 andoria sshd[14101]: Failed password for invalid user spravce from 71.91.238.165 port 44247 ssh2
Mar  2 14:39:00 andoria sshd[14101]: Connection closed by 71.91.238.165 [preauth]
Mar  2 15:17:01 andoria CRON[14120]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  2 15:17:01 andoria CRON[14120]: pam_unix(cron:session): session closed for user root
Mar  2 15:23:34 andoria sshd[14124]: Invalid user sql from 71.91.238.165
Mar  2 15:23:34 andoria sshd[14124]: input_userauth_request: invalid user sql [preauth]
Mar  2 15:23:34 andoria sshd[14124]: pam_unix(sshd:auth): check pass; user unknown
Mar  2 15:23:34 andoria sshd[14124]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=71.91.238.165 
Mar  2 15:23:37 andoria sshd[14124]: Failed password for invalid user sql from 71.91.238.165 port 57407 ssh2
Mar  2 15:23:37 andoria sshd[14124]: Connection closed by 71.91.238.165 [preauth]
Mar  2 16:02:13 andoria sshd[14142]: Did not receive identification string from 114.80.203.161
Mar  2 16:08:18 andoria sshd[14150]: Invalid user support from 71.91.238.165
Mar  2 16:08:18 andoria sshd[14150]: input_userauth_request: invalid user support [preauth]
Mar  2 16:08:18 andoria sshd[14150]: pam_unix(sshd:auth): check pass; user unknown
Mar  2 16:08:18 andoria sshd[14150]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=71.91.238.165 
Mar  2 16:08:21 andoria sshd[14150]: Failed password for invalid user support from 71.91.238.165 port 42819 ssh2
Mar  2 16:08:21 andoria sshd[14150]: Connection closed by 71.91.238.165 [preauth]
Mar  2 16:17:01 andoria CRON[14154]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  2 16:17:01 andoria CRON[14154]: pam_unix(cron:session): session closed for user root
Mar  2 16:52:55 andoria sshd[14168]: Invalid user teamspeak from 71.91.238.165
Mar  2 16:52:55 andoria sshd[14168]: input_userauth_request: invalid user teamspeak [preauth]
Mar  2 16:52:55 andoria sshd[14168]: pam_unix(sshd:auth): check pass; user unknown
Mar  2 16:52:55 andoria sshd[14168]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=71.91.238.165 
Mar  2 16:52:58 andoria sshd[14168]: Failed password for invalid user teamspeak from 71.91.238.165 port 60090 ssh2
Mar  2 16:52:58 andoria sshd[14168]: Connection closed by 71.91.238.165 [preauth]
Mar  2 17:13:45 andoria sshd[14181]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.174.51.221  user=root
Mar  2 17:13:47 andoria sshd[14181]: Failed password for root from 61.174.51.221 port 1658 ssh2
Mar  2 17:13:57  sshd[14181]: last message repeated 5 times
Mar  2 17:13:57 andoria sshd[14181]: Disconnecting: Too many authentication failures for root [preauth]
Mar  2 17:13:57 andoria sshd[14181]: PAM 5 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.174.51.221  user=root
Mar  2 17:13:57 andoria sshd[14181]: PAM service(sshd) ignoring max retries; 6 > 3
Mar  2 17:17:01 andoria CRON[14184]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  2 17:17:01 andoria CRON[14184]: pam_unix(cron:session): session closed for user root
Mar  2 17:37:49 andoria sshd[14340]: Invalid user ts from 71.91.238.165
Mar  2 17:37:49 andoria sshd[14340]: input_userauth_request: invalid user ts [preauth]
Mar  2 17:37:49 andoria sshd[14340]: pam_unix(sshd:auth): check pass; user unknown
Mar  2 17:37:49 andoria sshd[14340]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=71.91.238.165 
Mar  2 17:37:52 andoria sshd[14340]: Failed password for invalid user ts from 71.91.238.165 port 47853 ssh2
Mar  2 17:37:52 andoria sshd[14340]: Connection closed by 71.91.238.165 [preauth]
Mar  2 17:41:03 andoria sshd[14246]: Received disconnect from 192.168.1.1: 11: disconnected by user
Mar  2 18:17:01 andoria CRON[14397]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  2 18:17:01 andoria CRON[14397]: pam_unix(cron:session): session closed for user root
Mar  2 18:22:25 andoria sshd[14402]: Invalid user user from 71.91.238.165
Mar  2 18:22:25 andoria sshd[14402]: input_userauth_request: invalid user user [preauth]
Mar  2 18:22:25 andoria sshd[14402]: pam_unix(sshd:auth): check pass; user unknown
Mar  2 18:22:25 andoria sshd[14402]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=71.91.238.165 
Mar  2 18:22:28 andoria sshd[14402]: Failed password for invalid user user from 71.91.238.165 port 45338 ssh2
Mar  2 18:22:28 andoria sshd[14402]: Connection closed by 71.91.238.165 [preauth]
Mar  2 18:48:14 andoria sshd[14415]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=222.186.62.9  user=root
Mar  2 18:48:16 andoria sshd[14415]: Failed password for root from 222.186.62.9 port 1033 ssh2
Mar  2 18:48:27  sshd[14415]: last message repeated 5 times
Mar  2 18:48:27 andoria sshd[14415]: Disconnecting: Too many authentication failures for root [preauth]
Mar  2 18:48:27 andoria sshd[14415]: PAM 5 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=222.186.62.9  user=root
Mar  2 18:48:27 andoria sshd[14415]: PAM service(sshd) ignoring max retries; 6 > 3
Mar  2 18:48:29 andoria sshd[14417]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=222.186.62.9  user=root
Mar  2 18:48:30 andoria sshd[14417]: Failed password for root from 222.186.62.9 port 3045 ssh2
Mar  2 18:48:41  sshd[14417]: last message repeated 5 times
Mar  2 18:48:41 andoria sshd[14417]: Disconnecting: Too many authentication failures for root [preauth]
Mar  2 18:48:41 andoria sshd[14417]: PAM 5 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=222.186.62.9  user=root
Mar  2 18:48:41 andoria sshd[14417]: PAM service(sshd) ignoring max retries; 6 > 3
Mar  2 18:48:43 andoria sshd[14419]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=222.186.62.9  user=root
Mar  2 18:48:45 andoria sshd[14419]: Failed password for root from 222.186.62.9 port 1155 ssh2
Mar  2 19:04:15 andoria sshd[14436]: Did not receive identification string from 219.142.99.51
Mar  2 19:06:14 andoria sshd[14437]: Invalid user a from 219.143.202.189
Mar  2 19:06:14 andoria sshd[14437]: input_userauth_request: invalid user a [preauth]
Mar  2 19:06:14 andoria sshd[14437]: pam_unix(sshd:auth): check pass; user unknown
Mar  2 19:06:14 andoria sshd[14437]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=219.143.202.189 
Mar  2 19:06:17 andoria sshd[14437]: Failed password for invalid user a from 219.143.202.189 port 48970 ssh2
Mar  2 19:06:17 andoria sshd[14439]: Invalid user verwalter from 71.91.238.165
Mar  2 19:06:17 andoria sshd[14439]: input_userauth_request: invalid user verwalter [preauth]
Mar  2 19:06:17 andoria sshd[14439]: pam_unix(sshd:auth): check pass; user unknown
Mar  2 19:06:17 andoria sshd[14439]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=71.91.238.165 
Mar  2 19:06:17 andoria sshd[14437]: Received disconnect from 219.143.202.189: 11: Bye Bye [preauth]
Mar  2 19:06:19 andoria sshd[14439]: Failed password for invalid user verwalter from 71.91.238.165 port 45183 ssh2
Mar  2 19:06:19 andoria sshd[14439]: Connection closed by 71.91.238.165 [preauth]
Mar  2 19:06:22 andoria sshd[14441]: Invalid user abc123 from 123.127.245.125
Mar  2 19:06:22 andoria sshd[14441]: input_userauth_request: invalid user abc123 [preauth]
Mar  2 19:06:22 andoria sshd[14441]: pam_unix(sshd:auth): check pass; user unknown
Mar  2 19:06:22 andoria sshd[14441]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=123.127.245.125 
Mar  2 19:06:25 andoria sshd[14441]: Failed password for invalid user abc123 from 123.127.245.125 port 49111 ssh2
Mar  2 19:06:25 andoria sshd[14441]: Received disconnect from 123.127.245.125: 11: Bye Bye [preauth]
Mar  2 19:06:30 andoria sshd[14443]: Invalid user abc from 123.127.246.61
Mar  2 19:06:30 andoria sshd[14443]: input_userauth_request: invalid user abc [preauth]
Mar  2 19:06:30 andoria sshd[14443]: pam_unix(sshd:auth): check pass; user unknown
Mar  2 19:06:30 andoria sshd[14443]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=123.127.246.61 
Mar  2 19:06:33 andoria sshd[14443]: Failed password for invalid user abc from 123.127.246.61 port 49332 ssh2
Mar  2 19:06:34 andoria sshd[14443]: Received disconnect from 123.127.246.61: 11: Bye Bye [preauth]
Mar  2 19:06:39 andoria sshd[14445]: Invalid user abcd from 123.127.246.61
Mar  2 19:06:39 andoria sshd[14445]: input_userauth_request: invalid user abcd [preauth]
Mar  2 19:06:39 andoria sshd[14445]: pam_unix(sshd:auth): check pass; user unknown
Mar  2 19:06:39 andoria sshd[14445]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=123.127.246.61 
Mar  2 19:06:41 andoria sshd[14445]: Failed password for invalid user abcd from 123.127.246.61 port 49526 ssh2
Mar  2 19:06:43 andoria sshd[14452]: Invalid user abcde from 219.142.99.51
Mar  2 19:06:43 andoria sshd[14452]: input_userauth_request: invalid user abcde [preauth]
Mar  2 19:06:43 andoria sshd[14452]: pam_unix(sshd:auth): check pass; user unknown
Mar  2 19:06:43 andoria sshd[14452]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=219.142.99.51 
Mar  2 19:06:45 andoria sshd[14452]: Failed password for invalid user abcde from 219.142.99.51 port 49702 ssh2
Mar  2 19:06:45 andoria sshd[14452]: Received disconnect from 219.142.99.51: 11: Bye Bye [preauth]
Mar  2 19:06:55 andoria sshd[14454]: Invalid user abcdef from 123.127.245.125
Mar  2 19:06:55 andoria sshd[14454]: input_userauth_request: invalid user abcdef [preauth]
Mar  2 19:06:55 andoria sshd[14454]: pam_unix(sshd:auth): check pass; user unknown
Mar  2 19:06:55 andoria sshd[14454]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=123.127.245.125 
Mar  2 19:06:57 andoria sshd[14454]: Failed password for invalid user abcdef from 123.127.245.125 port 49792 ssh2
Mar  2 19:06:57 andoria sshd[14454]: Connection closed by 123.127.245.125 [preauth]
Mar  2 19:08:21 andoria sshd[14462]: Did not receive identification string from 211.44.8.221
Mar  2 19:17:01 andoria CRON[14465]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  2 19:17:01 andoria CRON[14465]: pam_unix(cron:session): session closed for user root
Mar  2 19:49:56 andoria sshd[14478]: Invalid user webmaster from 71.91.238.165
Mar  2 19:49:56 andoria sshd[14478]: input_userauth_request: invalid user webmaster [preauth]
Mar  2 19:49:56 andoria sshd[14478]: pam_unix(sshd:auth): check pass; user unknown
Mar  2 19:49:56 andoria sshd[14478]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=71.91.238.165 
Mar  2 19:49:59 andoria sshd[14478]: Failed password for invalid user webmaster from 71.91.238.165 port 37299 ssh2
Mar  2 19:49:59 andoria sshd[14478]: Connection closed by 71.91.238.165 [preauth]
Mar  2 20:17:01 andoria CRON[14493]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  2 20:17:01 andoria CRON[14493]: pam_unix(cron:session): session closed for user root
Mar  2 20:33:32 andoria sshd[14500]: Invalid user yonetici from 71.91.238.165
Mar  2 20:33:32 andoria sshd[14500]: input_userauth_request: invalid user yonetici [preauth]
Mar  2 20:33:32 andoria sshd[14500]: pam_unix(sshd:auth): check pass; user unknown
Mar  2 20:33:32 andoria sshd[14500]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=71.91.238.165 
Mar  2 20:33:35 andoria sshd[14500]: Failed password for invalid user yonetici from 71.91.238.165 port 60376 ssh2
Mar  2 20:33:35 andoria sshd[14500]: Connection closed by 71.91.238.165 [preauth]
Mar  2 21:17:01 andoria CRON[14520]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  2 21:17:01 andoria CRON[14520]: pam_unix(cron:session): session closed for user root
Mar  2 22:17:01 andoria CRON[14546]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  2 22:17:01 andoria CRON[14546]: pam_unix(cron:session): session closed for user root
Mar  2 23:17:01 andoria CRON[14585]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  2 23:17:01 andoria CRON[14585]: pam_unix(cron:session): session closed for user root
Mar  3 00:17:01 andoria CRON[14651]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  3 00:17:01 andoria CRON[14651]: pam_unix(cron:session): session closed for user root
Mar  3 01:17:01 andoria CRON[14707]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  3 01:17:01 andoria CRON[14707]: pam_unix(cron:session): session closed for user root
Mar  3 02:17:01 andoria CRON[14750]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  3 02:17:01 andoria CRON[14750]: pam_unix(cron:session): session closed for user root
Mar  3 03:17:01 andoria CRON[14790]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  3 03:17:01 andoria CRON[14790]: pam_unix(cron:session): session closed for user root
Mar  3 04:17:01 andoria CRON[14816]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  3 04:17:01 andoria CRON[14816]: pam_unix(cron:session): session closed for user root
Mar  3 05:17:01 andoria CRON[14836]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  3 05:17:01 andoria CRON[14836]: pam_unix(cron:session): session closed for user root
Mar  3 06:17:01 andoria CRON[14856]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  3 06:17:02 andoria CRON[14856]: pam_unix(cron:session): session closed for user root
Mar  3 06:25:01 andoria CRON[14862]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  3 06:25:01 andoria CRON[14862]: pam_unix(cron:session): session closed for user root
Mar  3 07:05:49 andoria sshd[14879]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=5.39.223.8  user=root
Mar  3 07:05:51 andoria sshd[14879]: Failed password for root from 5.39.223.8 port 49160 ssh2
Mar  3 07:05:51 andoria sshd[14879]: Received disconnect from 5.39.223.8: 11: Bye Bye [preauth]
Mar  3 07:05:53 andoria sshd[14881]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=5.39.223.8  user=root
Mar  3 07:05:55 andoria sshd[14881]: Failed password for root from 5.39.223.8 port 51259 ssh2
Mar  3 07:05:56 andoria sshd[14881]: Received disconnect from 5.39.223.8: 11: Bye Bye [preauth]
Mar  3 07:05:58 andoria sshd[14883]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=5.39.223.8  user=root
Mar  3 07:06:00 andoria sshd[14883]: Failed password for root from 5.39.223.8 port 53752 ssh2
Mar  3 07:06:00 andoria sshd[14883]: Received disconnect from 5.39.223.8: 11: Bye Bye [preauth]
Mar  3 07:17:01 andoria CRON[14895]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  3 07:17:01 andoria CRON[14895]: pam_unix(cron:session): session closed for user root
Mar  3 07:30:01 andoria CRON[14903]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  3 07:30:01 andoria CRON[14903]: pam_unix(cron:session): session closed for user root
Mar  3 08:17:01 andoria CRON[15144]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  3 08:17:01 andoria CRON[15144]: pam_unix(cron:session): session closed for user root
Mar  3 08:18:54 andoria sshd[15147]: Did not receive identification string from 188.64.170.221
Mar  3 09:17:01 andoria CRON[15166]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  3 09:17:01 andoria CRON[15166]: pam_unix(cron:session): session closed for user root
Mar  3 10:17:01 andoria CRON[15185]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  3 10:17:01 andoria CRON[15185]: pam_unix(cron:session): session closed for user root
Mar  3 10:30:32 andoria sshd[15193]: Did not receive identification string from 222.186.62.71
Mar  3 11:17:01 andoria CRON[15207]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  3 11:17:01 andoria CRON[15207]: pam_unix(cron:session): session closed for user root
Mar  3 12:17:01 andoria CRON[15233]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  3 12:17:01 andoria CRON[15233]: pam_unix(cron:session): session closed for user root
Mar  3 12:36:05 andoria sshd[15240]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=222.190.114.98  user=root
Mar  3 12:36:07 andoria sshd[15240]: Failed password for root from 222.190.114.98 port 42462 ssh2
Mar  3 12:36:08 andoria sshd[15240]: Received disconnect from 222.190.114.98: 11: Bye Bye [preauth]
Mar  3 12:36:09 andoria sshd[15242]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=222.190.114.98  user=root
Mar  3 12:36:12 andoria sshd[15242]: Failed password for root from 222.190.114.98 port 43477 ssh2
Mar  3 12:36:12 andoria sshd[15242]: Received disconnect from 222.190.114.98: 11: Bye Bye [preauth]
Mar  3 12:36:13 andoria sshd[15244]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=222.190.114.98  user=root
Mar  3 12:36:16 andoria sshd[15244]: Failed password for root from 222.190.114.98 port 44528 ssh2
Mar  3 12:36:16 andoria sshd[15244]: Received disconnect from 222.190.114.98: 11: Bye Bye [preauth]
Mar  3 12:49:59 andoria sshd[15258]: Did not receive identification string from 124.207.17.12
Mar  3 13:17:01 andoria CRON[15266]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  3 13:17:01 andoria CRON[15266]: pam_unix(cron:session): session closed for user root
Mar  3 14:17:01 andoria CRON[15318]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  3 14:17:01 andoria CRON[15318]: pam_unix(cron:session): session closed for user root
Mar  3 15:17:01 andoria CRON[15425]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  3 15:17:01 andoria CRON[15425]: pam_unix(cron:session): session closed for user root
Mar  3 16:17:01 andoria CRON[15547]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  3 16:17:01 andoria CRON[15547]: pam_unix(cron:session): session closed for user root
Mar  3 16:20:50 andoria sshd[15555]: Did not receive identification string from 182.72.174.82
Mar  3 17:17:01 andoria CRON[15784]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  3 17:17:01 andoria CRON[15784]: pam_unix(cron:session): session closed for user root
Mar  3 18:17:01 andoria CRON[15813]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  3 18:17:01 andoria CRON[15813]: pam_unix(cron:session): session closed for user root
Mar  3 19:02:10 andoria sshd[15837]: Invalid user guest from 219.138.60.51
Mar  3 19:02:10 andoria sshd[15837]: input_userauth_request: invalid user guest [preauth]
Mar  3 19:02:10 andoria sshd[15837]: pam_unix(sshd:auth): check pass; user unknown
Mar  3 19:02:10 andoria sshd[15837]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=219.138.60.51 
Mar  3 19:02:12 andoria sshd[15837]: Failed password for invalid user guest from 219.138.60.51 port 45741 ssh2
Mar  3 19:02:12 andoria sshd[15837]: Received disconnect from 219.138.60.51: 11: Bye Bye [preauth]
Mar  3 19:17:01 andoria CRON[15844]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  3 19:17:01 andoria CRON[15844]: pam_unix(cron:session): session closed for user root
Mar  3 20:17:01 andoria CRON[15872]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  3 20:17:01 andoria CRON[15872]: pam_unix(cron:session): session closed for user root
Mar  3 21:17:01 andoria CRON[15903]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  3 21:17:01 andoria CRON[15903]: pam_unix(cron:session): session closed for user root
Mar  3 22:17:01 andoria CRON[15948]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar  3 22:17:01 andoria CRON[15948]: pam_unix(cron:session): session closed for user root

```

And finally my fail2ban.log file:

```

2014-03-02 07:55:56,561 fail2ban.server : INFO   Changed logging target to /var/log/fail2ban.log for Fail2ban v0.8.10
2014-03-02 10:05:09,905 fail2ban.actions: WARNING [ssh] Unban 222.186.62.55
2014-03-02 15:40:58,736 fail2ban.actions: WARNING [ssh] Unban 222.178.179.158
2014-03-02 18:48:45,950 fail2ban.actions: WARNING [ssh] Ban 222.186.62.9
2014-03-02 19:06:40,128 fail2ban.actions: WARNING [ssh] Ban 123.127.246.61
2014-03-02 19:06:56,157 fail2ban.actions: WARNING [ssh] Ban 123.127.245.125
2014-03-03 07:06:01,122 fail2ban.actions: WARNING [ssh] Ban 5.39.223.8
2014-03-03 11:50:14,684 fail2ban.actions: WARNING [ssh] Unban 5.135.183.21
2014-03-03 12:36:16,697 fail2ban.actions: WARNING [ssh] Ban 222.190.114.98
2014-03-03 21:54:52,250 fail2ban.actions: WARNING [ssh] Unban 222.186.62.74

```

---

### Post by stchman on 2014-03-04
I set the findtime parameter in the jail.local to 14400(4 hours) as it appears that some try to stagger their tries to beat the 10 minute time limit.

After a bit more digging, some other folks have given it a try.

---

### Post by Habitual on 2014-03-04
if findtime is 600 (the default) and maxretry is 3 then the 4th hit in 600 seconds causes it to be banned.

My f2b 0.8.4 fail2ban.log shows suspect_ips being unbanned, but it doesn't actually do so. But then I have custom actions (for [permanence]("https://www.linuxquestions.org/questions/blog/habitual-558710/fail2ban-and-persistence-35932/")). It may not be the approved method, but it working for me.

My findtime is 60 and my maxretry = 1
You get **no** 2nd chance on my host. :)

Is 222.186.62.74 listed in ```
iptables -L -n | grep 222.186.62.74
```?

---

### Post by stchman on 2014-03-04
> **Habitual said:**
> if findtime is 600 (the default) and maxretry is 3 then the 4th hit in 600 seconds causes it to be banned.

My f2b 0.8.4 fail2ban.log shows suspect_ips being unbanned, but it doesn't actually do so. But then I have custom actions (for [permanence]("https://www.linuxquestions.org/questions/blog/habitual-558710/fail2ban-and-persistence-35932/")). It may not be the approved method, but it working for me.

My findtime is 60 and my maxretry = 1
You get **no** 2nd chance on my host. :)

Is 222.186.62.74 listed in ```
iptables -L -n | grep 222.186.62.74
```?

That IP address is not listed.

So with your setup, if you get the password wrong on the first try, you're banned?

Hopefully you don't fat finger your own password.

---

### Post by Habitual on 2014-03-04
> **stchman said:**
> That IP address is not listed.

So with your setup, if you get the password wrong on the first try, you're banned?

Hopefully you don't fat finger your own password.

Yes, 1 "try" and you're out!
passwords for ssh are **not** secure.
I use [ssh keys]("http://www.cyberciti.biz/tips/ssh-public-key-based-authentication-how-to.html").

and [COLOR=#ff0000]**all**[/COLOR] passwords are disabled via /etc/ssh/sshd_config
```
PasswordAuthentication no
```
Setting this requires sshd restart but ***do*** open another shell and test it BEFORE disconnecting from the session you used to make the edit.
and copy your ssh key.pub contents to the appropriate authorized_keys[2] file before you restart and/or disconnect. Else you won't get back in.
I can't emphasize this enough.
If the 2nd session doesn't work, revert your change in /etc/ssh/sshd_config, or better yet, make a backup before editing.

With "PasswordAuthentication no" they can bang on it all day and night and Never get in.

Recipe:
Create an sshkey on your localhost
copy sshkey.**[COLOR=#ff0000]pub[/COLOR]** contents to authorized_keys2 on remote host.
If you connect as root as some do ( I do) then the contents of sshkey.pub go in /root/.ssh/authorized_keys2 (this may not exist but you can make one and it should be "read" by the system when sshd is restarted)
If you connect as "ryan" then copy contents of sshkey.pub to /home/ryan/.ssh/authorized_keys or authorized_keys2 in same directory on the remote host.
Whichever <user>@domain.com you use to connect is who gets the contents of sshkey.pub in <user>/.ssh/authorized_keys2
make a copy of /etc/ssh/sshd_config using ```
cp /etc/ssh/sshd_config /etc/ssh/sshd_config.back
```

Test the ssh key using ssh -i /path/to/sshkey [EMAIL="user@remote_host.com"]user@remote_host.com[/EMAIL] in a **new terminal** from your localhost.
if that works, then edit /etc/ssh/sshd_config and set PasswordAuthentication to no
Restart ssh and [B]stay connected.
[/B]
testing password **dis**ability using another terminal with
ssh [EMAIL="user@remote_host.com"]user@remote_host.com[/EMAIL] with a known working password, it should fail.

Test again for good measure and if satisfied, you can disconnect all sessions.

Subscribed with interest....

---


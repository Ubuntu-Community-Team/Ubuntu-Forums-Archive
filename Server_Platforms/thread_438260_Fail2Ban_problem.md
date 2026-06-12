---
title: "Fail2Ban problem"
date: 2007-05-09
forum: Server Platforms
---

### Post by laytek on 2007-05-09
I am running an FTP server (VSFTPD 2.0.5) in a DMZ zone (Shorewall is the firewall running on the gateway computer). I am interested in blocking the script kiddies and dictionary attacks, so I installed Fail2Ban (0.7.6) on the FTP server (Feisty Kubuntu). It doesn't seem to be working though.

My fail2ban.conf looks like this:

```
# Fail2Ban configuration file
#
# Author: Cyril Jaquier
#
# $Revision: 494 $
#

[Definition]

# Option:  loglevel
# Notes.:  Set the log level output.
#          1 = ERROR
#          2 = WARN
#          3 = INFO
#          4 = DEBUG
# Values:  NUM  Default:  3
#
loglevel = 3

# Option:  logtarget
# Notes.:  Set the log target. This could be a file, SYSLOG, STDERR or STDOUT.
#          Only one log target can be specified.
# Values:  STDOUT STDERR SYSLOG file  Default:  /var/log/fail2ban.log
#
logtarget = /var/log/fail2ban.log

# Option: socket
# Notes.: Set the socket file. This is used to communicate with the daemon. Do
#         not remove this file when Fail2ban runs. It will not be possible to
#         communicate with the server afterwards.
# Values: FILE  Default:  /tmp/fail2ban.sock
#
socket = /tmp/fail2ban.sock
```

Nothing special here, so this is my jail.conf:

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
bantime  = 600
maxretry = 3
findtime = 600

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


#
# Action shortcuts. To be used to define action parameter

# The simplest action to take: ban only
action_ = %(banaction)s[name=%(__name__)s, port="%(port)s"]

# ban & send an e-mail with whois report to the destemail.
action_mw = %(banaction)s[name=%(__name__)s, port="%(port)s"]
              mail-whois[name=%(__name__)s, dest="%(destemail)s"]

# ban & send an e-mail with whois report and relevant log lines
# to the destemail.
action_mwl = %(banaction)s[name=%(__name__)s, port="%(port)s"]
               mail-whois-lines[name=%(__name__)s, dest="%(destemail)s", logpath=%(logpath)s]
 
# Choose default action.  To change, just override value of 'action' with the
# interpolation to the chosen action shortcut (e.g.  action_mw, action_mwl, etc) in jail.local
# globally (section [DEFAULT]) or per specific section 
action = %(action_)s

#
# JAILS
#

# Next jails corresponds to the standard configuration in Fail2ban 0.6 which
# was shipped in Debian. Please enable any defined here jail by including
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
port    = ssh,sftp
filter  = sshd
logpath  = /var/log/auth.log
maxretry = 6


[ssh-ddos]

enabled = false
port    = ssh,sftp
filter  = sshd-ddos
logpath  = /var/log/auth.log
maxretry = 6

#
# HTTP servers
#

[apache]

enabled = false
port    = http,https
filter  = apache-auth
logpath = /var/log/apache*/*access.log
maxretry = 6

# default action is now multiport, so apache-multiport jail was left
# for compatibility with previous (<0.7.6-2) releases
[apache-multiport]

enabled   = false
port      = http,https
filter    = apache-auth
logpath   = /var/log/apache*/*access.log
maxretry  = 6

[apache-noscript]

enabled = false
port    = http,https
filter  = apache-noscript
logpath = /var/log/apache*/*error.log
maxretry = 6

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
maxretry = 6


[wuftpd]

enabled  = false
port     = ftp,ftp-data,ftps,ftps-data
filter   = wuftpd
logpath  = /var/log/auth.log
maxretry = 6


#
# Mail servers
#

[postfix]

enabled  = false
port     = smtp,ssmtp
filter   = postfix
logpath  = /var/log/mail.log


[couriersmtp]

enabled  = false
port     = smtp,ssmtp
filter   = couriersmtp
logpath  = /var/log/mail.log


#
# Mail servers authenticators: might be used for smtp,ftp,imap servers, so
# all relevant ports get banned
#

[courierauth]

enabled  = false
port     = smtp,ssmtp,imap2,imap3,imaps,pop3,pop3s
filter   = courierlogin
logpath  = /var/log/mail.log


[sasl]

enabled  = false
port     = smtp,ssmtp,imap2,imap3,imaps,pop3,pop3s
filter   = sasl
logpath  = /var/log/mail.log
```

I added "findtime = 600" to this file to get rid of a warning during startup.
My jail.local:

```
# Fail2Ban local configuration file.
#
# This file was composed for Debian systems from the original one
#  provided now under /usr/share/doc/fail2ban/examples/jail.conf
#  for additional examples.
#
# To avoid merges during upgrades DO NOT MODIFY THIS FILE
# and rather provide your changes in /etc/fail2ban/jail.local
#

[DEFAULT]

# "ignoreip" can be an IP address, a CIDR mask or a DNS host
#ignoreip = 127.0.0.1
#bantime  = 600
#maxretry = 3

#
# JAILS
#

# Next jails corresponds to the standard configuration in Fail2ban 0.6 which
# was shipped in Debian. Please enable any defined here jail by including
#
# [SECTION_NAME] 
# enabled = true
#
# in /etc/fail2ban/jail.local.
#
# Optionally you may override any other parameter (e.g. banaction,
# action, port, logpath, etc) in that section within jail.local

[vsftpd]

enabled  = true
findtime = 600
port     = ftp,ftp-data,ftps,ftps-data
filter   = vsftpd
logpath  = /var/log/vsftpd.log
# or overwrite it in jails.local to be
#logpath = /var/log/auth.log
# if you want to rely on PAM failed login attempts
# vsftpd's failregex should match both of those formats
maxretry = 5
```

In this file, I enable vsftpd detection/protection.
I then start Fail2Ban, which appears to start normally.

```
xxxx@compaq:/etc/fail2ban$ sudo fail2ban-client status
Status
|- Number of jail:      2
`- Jail list:           vsftpd, ssh
```

As best I can tell, though Fail2Ban is not properly parsing/ detecting the vsftpd.log. Using a loglevel = 4, Fail2Ban reports that the vsftpd.log (and auth.log for ssh) file changes, but it is not picking up on a FAIL LOGIN. Therefore the counters never increment and it never bans an IP.

```
2007-05-09 15:27:41,451 fail2ban.filter : DEBUG  /var/log/auth.log has been modified
2007-05-09 15:27:41,452 fail2ban.filter : DEBUG  Opened /var/log/auth.log
2007-05-09 15:27:41,453 fail2ban.filter : DEBUG  Setting file position to 344033L for /var/log/auth.log
2007-05-09 15:27:41,454 fail2ban.filter.datedetector: DEBUG  Sorting the template list
2007-05-09 15:28:56,450 fail2ban.filter : DEBUG  /var/log/auth.log has been modified
2007-05-09 15:28:56,451 fail2ban.filter : DEBUG  Opened /var/log/auth.log
2007-05-09 15:28:56,452 fail2ban.filter : DEBUG  Setting file position to 344148L for /var/log/auth.log
2007-05-09 15:28:56,453 fail2ban.filter.datedetector: DEBUG  Sorting the template list
2007-05-09 15:29:46,114 fail2ban.filter : DEBUG  /var/log/vsftpd.log has been modified
2007-05-09 15:29:46,115 fail2ban.filter : DEBUG  Opened /var/log/vsftpd.log
2007-05-09 15:29:46,116 fail2ban.filter : DEBUG  Setting file position to 621924L for /var/log/vsftpd.log
2007-05-09 15:29:46,116 fail2ban.filter.datedetector: DEBUG  Sorting the template list
2007-05-09 15:31:59,449 fail2ban.filter : DEBUG  /var/log/auth.log has been modified
2007-05-09 15:31:59,450 fail2ban.filter : DEBUG  Opened /var/log/auth.log
2007-05-09 15:31:59,451 fail2ban.filter : DEBUG  Setting file position to 344259L for /var/log/auth.log
2007-05-09 15:31:59,452 fail2ban.filter.datedetector: DEBUG  Sorting the template list
```

Help!

LayTek:confused:

---

### Post by dannyboy79 on 2007-05-11
here is something that I believe will help.

I found the below info here ([http://www.the-art-of-web.com/system/fail2ban/](http://www.the-art-of-web.com/system/fail2ban/))

The most complicated part of the configuration file is the regular expression that is applied to auth.log to determine what to count as an access failure.

failregex = : (?:(?:Authentication failure|Failed [-/\w+]+) for(?: illegal user)?|Illegal user|Did not receive identification) .* from (?P<host>\S*) 
Note: the regular expression used here has been optimised for the auth.log in Debian Linux (Sarge) and may need to be modified slightly for other platforms.

In short, this matches any/all of the following auth.log entries and triggers a fwban event with the ip address or domain (host) that's been captured by the regular expression:

Authentication failure for username from <host>
Failed password for illegal user username from <host>
Failed password for username from <host>
Failed keyboard-interactive/pam for username from <host>
Illegal user username from <host>
Did not receive identification string from <host> 
For anyone trying to reverse-engineer the regular expression:

(?:.*) is a non-grouping version of regular parentheses; and 
(?P<name>.*) is similar to regular parentheses, but the substring matched by the group is accessible via the symbolic group name name. 
The single matched variable <host> will be added to the fail2ban-ssh chain if maxfailures or more matches occur within findtime. It's that simple.

You will see a lot of different (and usually simpler) failregex patterns that don't contain the <host> capture. The reason for having the named capture in the regexp is to counter a bug that allows malicious users to trick your server into blocking non-hostile addresses:

"fail2ban's approach to identifying an IP address in a login failure line is to scan the line for all IP addresses.

Since it is possible to generate false logins from accounts such as 10.2.28.2, it is possible to force fail2ban to block access to addresses which are not attempting to connect to the system. For each IP address available to the attacker, a desired ip address may be blocked."

---

### Post by laytek on 2007-05-12
Hi Dannyboy79

Thanks for the reply. Yes, I began to realize that Fail2Ban was not properly reading the logs. I have mine set to read the vsftpd.log. Using fail2ban-regex, I tested both regex filters from vsftpd.conf against vsftpd.log and auth.log. The test produced only a "Sorry, no match". Both logs were full with a thousand or more FAIL LOGIN attempts. With no match, their can be no banned IP.

I wrote to debianATonerussion.com about the problem. I believe he is the debian package maintainer. After supplying him with the requested info, he confirmed that there is a problem with versions 0.7.6 and 0.7.7. However, 0.7.8 works just fine. So I upgrade my Fail2Ban to the Gutsy version 0.8. I am a happy camper now. :) 

Thanks for your time. I hope this reply helps.

LayTek

---

### Post by dannyboy79 on 2007-05-14
how is vsftpd? I have used proftpd and thought it was hard to set up and I always had a issue getting ssl to work with fireftp or filezilla client thru my router. that's cool you got it working. I would appreciate any tips you could provide about setting up fail2ban and vsftpd as I just installed a brand new feisty install. I have only been on linux since March of 2006 and not to toot my own horn but I feel that I have picked it up rather fast. But since my first install was DApper back in March of 2006 I kind of had some garbage laying around, mis-compiled programs etc etc so I thought I'd do a fresh install and use my new found knowledge of linux to admin my server/desktop box correctly. Do you use a different port on your vsftpd server? Cause right now I have my windows box running filezilla server on the main ftp port. Anyway, again, thatnk you if you can provide any tips or gotchas. I would like to set it up so people are jailed in a certain directorey only, I don't want anonymous access login and possible ssl. 

You stated you're running the gutsy gibbon version of fail2ban, have you tried gutsy out yet?

---

### Post by laytek on 2007-05-17
Dannyboy79,

I am very much a Linux noob, so please take everything with a grain of salt. I am running an HP Pent IV (512Mb RAM, 200GB hard drive) as my desktop/gateway computer. It has been updated to Feisty Ubuntu. The kids love it, and my wife is not computer savvy. I am using Shorewall Firewall to protect us from the internet (a DSL 4.5 Mb/sec connection). I set up a local net zone for the other computers in the house, and a DMZ for my experimental web/vsftpd/ssh server. The DMZ is running Feisty Kubuntu with boa and vsftpd. To prevent the sometimes continuous script attacks on the FTP server I went with Fail2Ban.

I found vsftpd to be very, very easy to setup and understand. I use it mostly to distribute family pictures and the such. No anonymous and SSL. I would like to see more in-depth documentation, as digging certain facts out are hard. For instance, vsftpd 2.0.4 has a new feature that kills the current connection (session) if the user fails to login correctly in a user defined number of tries. Very important because shorewall and fail2ban only work on new connections. The changelog doesn't even mention vsftpd 2.0.5.

I use port 20 per standard. When the desktop/gateway was upgraded to Feisty, FTP quit working. Ugh! After some searching, I found that Netfilter changed many of the loadable module names. Shorewall uses a number of these, one in particular being ip_conntrack_ftp. Active and Passive modes of FTP cause firewalls fits, and a connection tracking module is required to open the correct ports. With the name change, the modules weren't loading. Tom Eastep has created a new modules list and all is well now!

I am very pleased with the little network I have built, and am patting myself on the back. But I know that I am nowhere the level that you are. Fortunately, I put meals on the table with a very different job.

Hope that helps.

Laytek

---

### Post by dannyboy79 on 2007-05-18
thank you very very much for taking the time to inform me about this. I wouldn't say that you don't have the knowledge that I do regarding linux, you sound like you were able to figure somehting out that a normal newbie would've just went back to winbloz on. I thanks again for your comments. do you feel that shorewall is any better than iptables or is just that it's gui driven which of course would make it easier if you don't understand iptables. is shorewall in the repo's or is shorewall a distro that you have setup on a computer which has 2 networks cards, one leading to the internet and the other leading to your internal network? i have read the using dmz is very dangerous, are you saying that your dmz server is on a different subnet or different internal network than youfamily boxes? or is it before your shorewall firewall?

---


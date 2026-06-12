---
title: "Fail2ban and it's hatred for Proftp"
date: 2008-07-24
forum: Security
---

### Post by ChumleyEX on 2008-07-24
Ok folks, I've been beating my head against this one for quite some time now. 

fail2ban will ban ssh all day long with unwaivering support, however fail2ban just hates proftp. 

I have the newest ubuntu (Hardy I think is the name) and the newest fail2ban package that it offers. I've made the change in the filter.d folder for proftpd.conf and still no love. 

Help me ubuntuforums, you're my only hope. 

ok jail.conf 

> # Fail2Ban configuration file.
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
bantime  = 666
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
maxretry = 6

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
maxretry = 6

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
maxretry = 6

#
# HTTP servers
#

[apache]

enabled = false
port	= http,https
filter	= apache-auth
logpath = /var/log/apache*/*error.log
maxretry = 6

# default action is now multiport, so apache-multiport jail was left
# for compatibility with previous (<0.7.6-2) releases
[apache-multiport]

enabled   = false
port	  = http,https
filter	  = apache-auth
logpath   = /var/log/apache*/*error.log
maxretry  = 6

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

enabled  = true
port	 = ftp,ftp-data,ftps,ftps-data,proftpd,proftp
filter   = proftpd
logpath  = /var/log/secure
maxretry = 3


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




/etc/fail2ban/filter.d/proftpd.conf

> # Fail2Ban configuration file
#
# Author: Yaroslav Halchenko
#
# $Revision: 665 $
#

[Definition]

# Option: failregex
# Notes.: regex to match the password failures messages in the logfile. The
#          host must be matched by a group named "host". The tag "<HOST>" can
#          be used for standard IP/hostname matching and is only an alias for
#          (?:::f{4,6}:)?(?P<host>\S+)
# Values: TEXT
#
failregex = \(\S+\[<HOST>\]\)[: -]+ USER \S+: no such user found from \S+ \[[0-9.]+\] to \S+:\S+$
            \(\S*\[<HOST>\]\): USER \S+ \(Login failed\): Incorrect password.$
            \(\S+\[<HOST>\]\)[: -]+ SECURITY VIOLATION: \S+ login attempted\.$
            \(\S+\[<HOST>\]\)[: -]+ Maximum login attempts \(\d+\) exceeded$

# Option:  ignoreregex
# Notes.:  regex to ignore. If this regex matches, the line is ignored.
# Values:  TEXT
#
ignoreregex = 



/var/log/fail2ban.log   (here is a part of it)

> 2008-07-24 10:12:34,449 fail2ban.jail   : INFO   Using poller
2008-07-24 10:12:34,458 fail2ban.filter : INFO   Created Filter
2008-07-24 10:12:34,458 fail2ban.filter : INFO   Created FilterPoll
2008-07-24 10:12:34,459 fail2ban.filter : INFO   Added logfile = /var/log/auth.log
2008-07-24 10:12:34,465 fail2ban.filter : INFO   Set maxRetry = 6
2008-07-24 10:12:34,466 fail2ban.filter : INFO   Set findtime = 600
2008-07-24 10:12:34,467 fail2ban.actions: INFO   Set banTime = 666
2008-07-24 10:12:34,523 fail2ban.actions.action: INFO   Set actionBan = iptables -I fail2ban-<name> 1 -s <ip> -j DROP
2008-07-24 10:12:34,524 fail2ban.actions.action: INFO   Set actionStop = iptables -D INPUT -p <protocol> -m multiport --dports <port> -j fail2ban-<name>
iptables -F fail2ban-<name>
iptables -X fail2ban-<name>
2008-07-24 10:12:34,525 fail2ban.actions.action: INFO   Set actionStart = iptables -N fail2ban-<name>
iptables -A fail2ban-<name> -j RETURN
iptables -I INPUT -p <protocol> -m multiport --dports <port> -j fail2ban-<name>
2008-07-24 10:12:34,526 fail2ban.actions.action: INFO   Set actionUnban = iptables -D fail2ban-<name> -s <ip> -j DROP
2008-07-24 10:12:34,527 fail2ban.actions.action: INFO   Set actionCheck = iptables -n -L INPUT | grep -q fail2ban-<name>
2008-07-24 10:12:34,530 fail2ban.jail   : INFO   Using poller
2008-07-24 10:12:34,530 fail2ban.filter : INFO   Created Filter
2008-07-24 10:12:34,530 fail2ban.filter : INFO   Created FilterPoll
2008-07-24 10:12:34,531 fail2ban.filter : INFO   Added logfile = /var/log/secure
2008-07-24 10:12:34,533 fail2ban.filter : INFO   Set maxRetry = 3
2008-07-24 10:12:34,534 fail2ban.filter : INFO   Set findtime = 600
2008-07-24 10:12:34,535 fail2ban.actions: INFO   Set banTime = 666
2008-07-24 10:12:34,545 fail2ban.actions.action: INFO   Set actionBan = iptables -I fail2ban-<name> 1 -s <ip> -j DROP
2008-07-24 10:12:34,546 fail2ban.actions.action: INFO   Set actionStop = iptables -D INPUT -p <protocol> -m multiport --dports <port> -j fail2ban-<name>
iptables -F fail2ban-<name>
iptables -X fail2ban-<name>
2008-07-24 10:12:34,547 fail2ban.actions.action: INFO   Set actionStart = iptables -N fail2ban-<name>
iptables -A fail2ban-<name> -j RETURN
iptables -I INPUT -p <protocol> -m multiport --dports <port> -j fail2ban-<name>
2008-07-24 10:12:34,548 fail2ban.actions.action: INFO   Set actionUnban = iptables -D fail2ban-<name> -s <ip> -j DROP
2008-07-24 10:12:34,549 fail2ban.actions.action: INFO   Set actionCheck = iptables -n -L INPUT | grep -q fail2ban-<name>
2008-07-24 10:12:34,693 fail2ban.actions.action: ERROR  iptables -N fail2ban-proftpd
iptables -A fail2ban-proftpd -j RETURN
iptables -I INPUT -p tcp -m multiport --dports ftp,ftp-data,ftps,ftps-data,proftpd,proftp -j fail2ban-proftpd returned 200




Part of /var/log/secure         (this is me trying to get banned)

> Jul 24 10:14:30 sage proftpd[21237] sage (::ffff:165.221.220.2[::ffff:165.221.220.2]): FTP session opened.
Jul 24 10:14:32 sage proftpd[21237] sage (::ffff:165.221.220.2[::ffff:165.221.220.2]): no such user 'poop'
Jul 24 10:14:32 sage proftpd[21237] sage (::ffff:165.221.220.2[::ffff:165.221.220.2]): USER poop: no such user found from ::ffff:165.221.220.2 [::ffff:165.221.220.2] to ::ffff:192.168.1.8:21
Jul 24 10:14:33 sage proftpd[21237] sage (::ffff:165.221.220.2[::ffff:165.221.220.2]): FTP session closed.
Jul 24 10:15:27 sage proftpd[21272] sage (::ffff:165.221.220.2[::ffff:165.221.220.2]): FTP session opened.
Jul 24 10:15:29 sage proftpd[21272] sage (::ffff:165.221.220.2[::ffff:165.221.220.2]): no such user 'poop'
Jul 24 10:15:29 sage proftpd[21272] sage (::ffff:165.221.220.2[::ffff:165.221.220.2]): USER poop: no such user found from ::ffff:165.221.220.2 [::ffff:165.221.220.2] to ::ffff:192.168.1.8:21
Jul 24 10:15:29 sage proftpd[21272] sage (::ffff:165.221.220.2[::ffff:165.221.220.2]): FTP session closed.
Jul 24 10:15:42 sage proftpd[21274] sage (::ffff:165.221.220.2[::ffff:165.221.220.2]): FTP session opened.
Jul 24 10:15:45 sage proftpd[21274] sage (::ffff:165.221.220.2[::ffff:165.221.220.2]): no such user 'poop'
Jul 24 10:15:45 sage proftpd[21274] sage (::ffff:165.221.220.2[::ffff:165.221.220.2]): USER poop: no such user found from ::ffff:165.221.220.2 [::ffff:165.221.220.2] to ::ffff:192.168.1.8:21
Jul 24 10:15:45 sage proftpd[21274] sage (::ffff:165.221.220.2[::ffff:165.221.220.2]): FTP session closed.
Jul 24 10:15:58 sage proftpd[21276] sage (::ffff:165.221.220.2[::ffff:165.221.220.2]): FTP session opened.
Jul 24 10:16:01 sage proftpd[21276] sage (::ffff:165.221.220.2[::ffff:165.221.220.2]): no such user 'poop'
Jul 24 10:16:01 sage proftpd[21276] sage (::ffff:165.221.220.2[::ffff:165.221.220.2]): USER poop: no such user found from ::ffff:165.221.220.2 [::ffff:165.221.220.2] to ::ffff:192.168.1.8:21




What can I do?

---

### Post by HermanAB on 2008-07-24
Uhmmm, the solution is actually very simple.  Instead of using fail2ban, rather put a rate limit statement in iptables.  

Add the following two lines to the bottom of /etc/rc.d/rc.local, to limit new login attempts to once per minute:

```
iptables -A INPUT -p tcp -m state --syn --state NEW --dport ssh -m limit --limit 1/minute --limit-burst 1 -j ACCEPT
iptables -A INPUT -p tcp -m state --syn --state NEW --dport ssh -j DROP
```

That will defeat even the most patient hacker...

---

### Post by kevdog on 2008-07-24
I agree with herman, most of these extra tools -- fail2ban, denyhosts -- can be forgotten if you just configure the iptables manually -- which is actually very easy.

I found this off another website however this may be exactly what you want -- just change some of the ports, names around etc:

Simple iptables rules for blocking brute-force login attacks, such as the automated SSH attacks that infest the Internet. These will continue to wander and annoy long after the sociopaths who launched them are dead and forgotten. All you need are two rules per service, like this:

iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m
recent --set --name SSH
iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m
recent --update --seconds 60 --hitcount 8 --rttl --name SSH -j DROP

This limits all incoming connections to port 22 to 8 per minute. To prevent
locking yourself out, you can create a whitelist:

iptables -N ssh-whitelist
iptables -A ssh-whitelist -s [your-ip-address] -m recent --remove --name
SSH -j ACCEPT

Then modify your limiting rules like this:

iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m
recent --set --name SSH
iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -j
ssh-whitelist
iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m
recent --update --seconds 60 --hitcount 8 --rttl --name SSH -j DROP


You can easily adapt this for any service. The --set --name option creates an arbitrary name, so you can call it anything you want. Just make sure it matches the --name in your DROP rule.

---

### Post by ChumleyEX on 2008-07-25
So far it didn't work. The file was /etc/rc.local  I don't have just a rc.d folder I have lots of rc.1d 2d etc. 

> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
exit 0
iptables -A INPUT -p tcp -m state --syn --state NEW --dport proftpd -m limit --$
iptables -A INPUT -p tcp -m state --syn --state NEW --dport proftpd -j DROP


I tried it as ftp, proftp, and proftpd, along with moving exit 0 to the bottom. I was able to attempt (and purposely fail) login back to back.

---

### Post by cariboo on 2008-07-25
You have to use the port number not the name of the server for ftp it would be port 21. If you have your ftp server running on a different port use that.

Jim

---

### Post by kevdog on 2008-07-25
exit 0 goes at the bottom of the script.

As stated above you need to use the specific port number, or define  proftpd at the top of the script such as

proftpd=22

and then reference with $proftpd


iptables -A INPUT -p tcp -m state --syn --state NEW --dport proftpd -m limit --$
iptables -A INPUT -p tcp -m state --syn --state NEW --dport proftpd -j DROP

What are those statements above anyway?? The first is incomplete, and the second drops the connection?  What are your trying to write?

With any ftp connection you need to do connection tracking since it requires two ports == one for data and the other for commands.

---

### Post by HermanAB on 2008-07-26
Service names and port numbers are defined in /etc/services.  The variables ssh and ftp are both defined in there, so you can use them in iptables scripts without further ado.

Cheers,

Herman

---

### Post by kevdog on 2008-07-26
> **HermanAB said:**
> Service names and port numbers are defined in /etc/services.  The variables ssh and ftp are both defined in there, so you can use them in iptables scripts without further ado.

Cheers,

Herman

Assuming you haven't deviated from the normal ports -- like many with ssh do :)

---

### Post by ChumleyEX on 2008-07-27
all the port numbers are normal. ftp is 21 ssh 22.

---

### Post by kevdog on 2008-07-27
I'm reposting this info here directly taken from another post that I wrote -- the other user told me specifically it worked for him:

Its because ftp involves both a command and data channel, not just one ftp port 21:

Connection tracking and ftp

Firstly, you need to load the ip_conntrack_ftp module.

*** Ok this can be done one of two ways depending on how you are setting up your firewall.
1. If you are using firestarter or some GUI, you likely need to load the kernel module (either on the command line, in the rc.local file, in /etc/modules, in /etc/network/interfaces). If loading at the command line do the following:
sudo modprobe ip_conntrack_ftp

2. If you are using a script to load the iptables such as explained here:
[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

You would add this to this near the top of the script:
MODPROBE=/sbin/modprobe
$MODPROBE ip_conntrack_ftp


Assuming you have a single-homed box, a simple ruleset to allow an ftp connection would be:

iptables -A INPUT -p tcp --sport 21 -m state --state ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p tcp --dport 21 -m state --state NEW,ESTABLISHED -j ACCEPT

(Please note, I am assuming here you have a separate ruleset to allow any icmp RELATED to the conection.)

This is not the whole story. An ftp connection also needs a data-channel, which can be provided in one of two ways:

1) Active ftp

The ftp client sends a port number over the ftp channel via a PORT command to the ftp server. The ftp server then connects from port 20 to this port to send data, such as a file, or the output from an ls command. The ftp-data connection is in the opposite sense from the original ftp connection.

To allow active ftp without knowing the port number that has been passed we need a general rule which allows connections from port 20 on remote ftp servers to high ports (port numbers > 1023) on ftp clients. This is simply too general to ever be secure.

Enter the ip_conntrack_ftp module. This module is able to recognize the PORT command and pick-out the port number. As such, the ftp-data connection can be classified as RELATED to the original outgoing connection to port 21 so we don't need NEW as a state match for the connection in the INPUT chain. The following rules will serve our purposes grandly:

iptables -A INPUT -p tcp --sport 20 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -p tcp --dport 20 -m state --state ESTABLISHED -j ACCEPT

2) Passive ftp

A PORT command is again issued, but this time it is from the server to the client. The client connects to the server for data transfer. Since the connection is in the same sense as the original ftp connection, passive ftp is inherently more secure than active ftp, but note that this time we know even less about the port numbers. Now we have a connection between almost arbitrary port numbers.

Enter the ip_conntrack_ftp module once more. Again, this module is able to recognize the PORT command and pick-out the port number. Instead of NEW in the state match for the OUTPUT chain, we can use RELATED. The following rules will suffice:

iptables -A INPUT -p tcp --sport 1024: --dport 1024: -m state --state ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p tcp --sport 1024: --dport 1024: -m state --state ESTABLISHED,RELATED -j ACCEPT

---

### Post by ChumleyEX on 2008-07-28
omg massive headache from total noobness on my part. It hurts. I will look this over and try to digest it all. 

No pain no gain.

---

### Post by HermanAB on 2008-07-28
For FTP, you only need to protect the login port 21.  Don't worry about the random high ports.

Go to "Rusty Russel's amazingly inaccurate web site" and read up on Iptables and Netfilter.

Cheers,

Herman

---


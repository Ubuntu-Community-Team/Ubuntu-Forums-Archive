---
title: "Fail2ban not actually banning IPs"
date: 2014-11-06
forum: Security
---

### Post by nicole9 on 2014-11-06
I have been messing around with fail2ban for days now to stop brute force attempts to get into my server. 

IPs are still able to brute force my server somehow, despite the fact that my fail2ban settings appear to be successfully dropping them. 

What's odd is that the output of iptables -L has tons of DROP entries for the same IP addresses:

```

DROP       all  --  123.157.150.50       anywhere
DROP       all  --  123.157.150.50       anywhere
DROP       all  --  123.157.150.50       anywhere
DROP       all  --  123.157.150.50       anywhere
DROP       all  --  123.157.150.50       anywhere
DROP       all  --  123.157.150.50       anywhere
DROP       all  --  123.157.150.50       anywhere
DROP       all  --  123.157.150.50       anywhere
DROP       all  --  123.157.150.50       anywhere
DROP       all  --  123.157.150.50       anywhere
DROP       all  --  123.157.150.50       anywhere
DROP       all  --  123.157.150.50       anywhere

```

In fail2ban.log I have tons of these:

```

fail2ban.log:2014-11-05 14:51:03,778 fail2ban.actions: WARNING [ssh] Unban 123.157.150.50
fail2ban.log:2014-11-05 14:51:28,823 fail2ban.actions: WARNING [ssh] Ban 123.157.150.50
fail2ban.log:2014-11-05 15:01:29,614 fail2ban.actions: WARNING [ssh] Unban 123.157.150.50
fail2ban.log:2014-11-05 15:01:45,649 fail2ban.actions: WARNING [ssh] Ban 123.157.150.50
fail2ban.log:2014-11-05 15:11:46,430 fail2ban.actions: WARNING [ssh] Unban 123.157.150.50
fail2ban.log:2014-11-05 15:13:42,585 fail2ban.actions: WARNING [ssh] Ban 123.157.150.50
fail2ban.log:2014-11-05 15:23:43,359 fail2ban.actions: WARNING [ssh] Unban 123.157.150.50
fail2ban.log:2014-11-05 15:24:01,397 fail2ban.actions: WARNING [ssh] Ban 123.157.150.50
fail2ban.log:2014-11-05 15:34:02,158 fail2ban.actions: WARNING [ssh] Unban 123.157.150.50
fail2ban.log:2014-11-05 15:34:20,194 fail2ban.actions: WARNING [ssh] Ban 123.157.150.50
fail2ban.log:2014-11-05 15:44:20,958 fail2ban.actions: WARNING [ssh] Unban 123.157.150.50

```

In auth.log I have tons of these:
```

auth.log:Nov  5 15:23:55 seitan sshd[20427]: User root from 123.157.150.50 not allowed because not listed in AllowUsers
auth.log:Nov  5 15:23:58 seitan sshd[20429]: User root from 123.157.150.50 not allowed because not listed in AllowUsers
auth.log:Nov  5 15:24:00 seitan sshd[20431]: User root from 123.157.150.50 not allowed because not listed in AllowUsers
auth.log:Nov  5 15:34:06 seitan sshd[21349]: User root from 123.157.150.50 not allowed because not listed in AllowUsers
auth.log:Nov  5 15:34:08 seitan sshd[21351]: User root from 123.157.150.50 not allowed because not listed in AllowUsers
auth.log:Nov  5 15:34:11 seitan sshd[21354]: User root from 123.157.150.50 not allowed because not listed in AllowUsers
auth.log:Nov  5 15:34:13 seitan sshd[21362]: User root from 123.157.150.50 not allowed because not listed in AllowUsers
auth.log:Nov  5 15:34:16 seitan sshd[21368]: User root from 123.157.150.50 not allowed because not listed in AllowUsers
auth.log:Nov  5 15:34:19 seitan sshd[21370]: User root from 123.157.150.50 not allowed because not listed in AllowUsers

```

Here's my iptables-multiport.conf:

```

# Fail2Ban configuration file
#
# Author: Cyril Jaquier
# Modified by Yaroslav Halchenko for multiport banning
# $Revision$
#

[Definition]

# Option:  actionstart
# Notes.:  command executed once at the start of Fail2Ban.
# Values:  CMD
#
actionstart = iptables -N fail2ban-<name>
              iptables -A fail2ban-<name> -j RETURN
              iptables -I INPUT -p <protocol> -m multiport --dports <port> -j fail2ban-<name>
cat /etc/fail2ban/ip.blacklist | while read IP; do iptables -I fail2ban-<name> 1 -s $IP -j DROP; done

# Option:  actionstop
# Notes.:  command executed once at the end of Fail2Ban
# Values:  CMD
#
actionstop = iptables -D <chain> -p <protocol> -m multiport --dports <port> -j fail2ban-<name>
             iptables -F fail2ban-<name>
             iptables -X fail2ban-<name>

# Option:  actioncheck
# Notes.:  command executed once before each actionban command
# Values:  CMD
#
actioncheck = iptables -n -L <chain> | grep -q fail2ban-<name>

# Option:  actionban
# Notes.:  command executed when banning an IP. Take care that the
#          command is executed with Fail2Ban user rights.
# Tags:    <ip>  IP address
#          <failures>  number of failures
#          <time>  unix timestamp of the ban time
# Values:  CMD
#
actionban = iptables -I fail2ban-<name> 1 -s <ip> -j DROP
            echo <ip> >> /etc/fail2ban/ip.blacklist

# Option:  actionunban
# Notes.:  command executed when unbanning an IP. Take care that the
#          command is executed with Fail2Ban user rights.
# Tags:    <ip>  IP address
#          <failures>  number of failures
#          <time>  unix timestamp of the ban time
# Values:  CMD
#
actionunban = iptables -D fail2ban-<name> -s <ip> -j DROP

[Init]

# Defaut name of the chain
#
name = default

# Option:  port
# Notes.:  specifies port to monitor
# Values:  [ NUM | STRING ]  Default:
#
port = ssh

# Option:  protocol
# Notes.:  internally used by config reader for interpolations.
# Values:  [ tcp | udp | icmp | all ] Default: tcp
#
protocol = tcp

# Option:  chain
# Notes    specifies the iptables chain to which the fail2ban rules should be
#          added
# Values:  STRING  Default: INPUT
chain = INPUT

```

Does anyone have any idea why this is happening? I can't seem to find any correct answers online.

---

### Post by nicole9 on 2014-11-06
One this I have noticed in the output of iptables -L is that the IPs autodropped by fail2ban are entered under

Chain fail2ban-ssh (1 references)

but if I manually drop an IP from the command line using iptables, the IP tends to actaully be blocked, and it's entered under

Chain INPUT (policy ACCEPT)

I have no idea why this is happening???

---

### Post by Habitual on 2014-11-06
show us the relevant entry in jail.conf or jail.local for the ssh jail please.

and the "/etc/fail2ban/ip.blacklist" code looks strangely familiar. I've used the same mechanism in the past, but not any longer.

---

### Post by nicole9 on 2014-11-06
Thank you so much for responding! Can you tell me what you use now?

Here is my entire jail.local file:

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
# $Revision$
#

# The DEFAULT allows a global definition of the options. They can be overridden
# in each jail afterwards.

[DEFAULT]

# "ignoreip" can be an IP address, a CIDR mask or a DNS host
ignoreip = 127.0.0.1/8 xx.xx.xx.xxx
bantime  = 600
maxretry = 3

# "backend" specifies the backend used to get files modification. Available
# options are "gamin", "polling" and "auto".
# yoh: For some reason Debian shipped python-gamin didn't work as expected
#      This issue left ToDo, so polling is default backend for now
backend = auto

#
# Destination email address used solely for the interpolations in
# jail.{conf,local} configuration files.
destemail = M

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
maxretry = 6

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
maxretry = 6

#
# HTTP servers
#

[apache]

enabled  = false
port     = http,https
filter   = apache-auth
logpath  = /var/log/apache*/*error.log
maxretry = 6

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


[pure-ftpd]

enabled  = false
port     = ftp,ftp-data,ftps,ftps-data
filter   = pure-ftpd
logpath  = /var/log/auth.log
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
# You might consider monitoring /var/log/mail.warn instead if you are
# running postfix since it would provide the same log lines at the
# "warn" level but overall at the smaller filesize.
logpath  = /var/log/mail.log

[dovecot]

enabled = false
port    = smtp,ssmtp,imap2,imap3,imaps,pop3,pop3s
filter  = dovecot
logpath = /var/log/mail.log

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

```

---

### Post by Doug S on 2014-11-06
I have been noticing increased SSH brute force stuff from China recently (several months). The attacks are also very sophisticated and methodical, merely switching to another IP address on the same sub-net or a different sub-net entirely once they are blocked. At this point I am now permanently blocking several large blocks of IP addresses from China. I have also increased my dynamic block time from 1.5 hours to greater than one day. However, I do not use Fail2Ban, I use this, which has served me very well for many years now (mentioned many times before):```
# Secure Shell on port 22.
#
# Dynamic Badguy List. Detect and DROP Bad IPs that do password attacks on SSH.
# Once they are on the BADGUY list then DROP all packets from them.
#$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 5400 --name BADGUY_SSH -j LOG --log-prefix "SSH BAD:" --log-level info
#$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 5400 --name BADGUY_SSH -j DROP
# Sometimes make the lock time very long. Typically to try to get rid of coordinated attacks from China.
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 90000 --name BADGUY_SSH -j LOG --log-prefix "SSH BAD:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 90000 --name BADGUY_SSH -j DROP
$IPTABLES -A INPUT -i $EXTIF -p tcp -m tcp --dport 22 -m recent --set --name BADGUY_SSH -j ACCEPT
```And yes, I have left SSH access on port 22 on purpose. Why? Because I study this stuff. I also log everything, but you don't have to.

Edit: I forgot to mention, in sshd_config I also do this:```
#Limit the number of bad passwords per connection to 2. Default is 6.
#Then the iptables connection counter will kick in sooner to drop
#password attack hackers.
MaxAuthTries 2
```

---

### Post by HermanAB on 2014-11-07
Just use an iptables rate limiting rule and be done with it.

---

### Post by mastablasta on 2014-11-07
it's doing what jail.local tells it to do and that is:

```
[DEFAULT]

# "ignoreip" can be an IP address, a CIDR mask or a DNS host
ignoreip = 127.0.0.1/8 xx.xx.xx.xxx
bantime  = 600
maxretry = 3
```

so that's 600 seconds= 10 minutes. it's banning the IP for 10 mins then unbanning it. increase bantime to something big or I think -1 should be forever.

for example:
```
[FONT="Times New Roman"][COLOR=#000000]#
"ignoreip" can be an IP address, a CIDR mask or a DNS host

ignoreip = [/COLOR][[COLOR=#0000ff]127.0.0.1/8[/COLOR]]("http://127.0.0.1/8")[COLOR=#000000] xx.xx.xx.xxx[/COLOR][COLOR=#000000]
bantime  = 2592000
maxretry = 3[/COLOR][/FONT]
```

this should ban them for 30 days.

---

### Post by mastablasta on 2014-11-07
> **Doug S said:**
> I have been noticing increased SSH brute force stuff from China recently (several months). The attacks are also very sophisticated and methodical, merely switching to another IP address on the same sub-net or a different sub-net entirely once they are blocked. At this point I am now permanently blocking several large blocks of IP addresses from China. I have also increased my dynamic block time from 1.5 hours to greater than one day. However, I do not use Fail2Ban, I use this, which has served me very well for many years now (mentioned many times before):

where do you write these ruies? to iptables? or in some file?

---

### Post by Doug S on 2014-11-07
> **mastablasta said:**
> where do you write these rules? to iptables? or in some file?What I posted was an excerpt from a script that implements my iptables rule set, among a couple of other things. Here is the same area again (method 1):```
doug@doug-64:~$ [COLOR=#ff0000]sudo iptables -v -x -n -L[/COLOR]
Chain INPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
    5018   385986 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0
   24000   768072 DROP       all  --  *      *       0.0.0.0/0            224.0.0.1
       0        0 LOG        tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0            state INVALID LOG flags 0 level 6 prefix "IINVALID:"
      15     6202 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcpflags:! 0x17/0x02 state NEW LOG flags 0 level 6 prefix "NEW TCP no SYN:"
      15     6202 REJECT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcpflags:! 0x17/0x02 state NEW reject-with icmp-port-unreachable
  380526 46859680 ACCEPT     all  --  eth0   *       192.168.111.0/24     0.0.0.0/0
... deleted some stuff...
  192679 55982124 ACCEPT     all  --  eth1   *       0.0.0.0/0            173.180.45.4         state RELATED,ESTABLISHED
   11682   337070 DROP       all  --  eth1   *       0.0.0.0/0            0.0.0.0/0            u32 "0x6&0xff=0x1&&0x0>>0x16&0x3c@0x0>>0x18=0x8&&0x0&0xff00=0x0"
      40     4873 ACCEPT     icmp --  eth1   *       0.0.0.0/0            173.180.45.4
... deleted some direct DROP stuff, including several large sub-nets from China ...
     195    64108 ACCEPT     udp  --  eth0   *       0.0.0.0/0            0.0.0.0/0            udp spt:68 dpt:67
[COLOR=#ff0000]     755    41328 LOG        all  --  eth1   *       0.0.0.0/0            0.0.0.0/0            recent: UPDATE seconds: 90000 hit_count: 3 name: BADGUY_SSH side: source LOG flags 0 level 6 prefix "SSH BAD:"
     755    41328 DROP       all  --  eth1   *       0.0.0.0/0            0.0.0.0/0            recent: UPDATE seconds: 90000 hit_count: 3 name: BADGUY_SSH side: source
     249    12796 ACCEPT     tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22 recent: SET name: BADGUY_SSH side: source
[/COLOR]    3691   208872 http-new-in  tcp  --  eth1   *       0.0.0.0/0            173.180.45.4         state NEW tcp dpt:80
     163     8044 ACCEPT     tcp  --  eth1   *       0.0.0.0/0            173.180.45.4         state NEW limit: avg 5/min burst 3 tcp dpt:25
    1241    64041 LOG        tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0            multiport sports 80,443 LOG flags 0 level 6 prefix "BAD80:"
    1241    64041 REJECT     tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0            multiport sports 80,443 reject-with icmp-port-unreachable
    5911   478047 log-n-drop  all  --  *      *       0.0.0.0/0            0.0.0.0/0
... deleted the rest ...
```Here is the same area again (method 2):```
doug@doug-64:~$ [COLOR=#ff0000]sudo iptables-save -c[/COLOR]
# Generated by iptables-save v1.4.12 on Fri Nov  7 08:04:46 2014
*nat
:PREROUTING ACCEPT [229726:37235104]
:INPUT ACCEPT [56101:4009889]
:OUTPUT ACCEPT [68631:5642978]
:POSTROUTING ACCEPT [6618:831606]
[124872:8512914] -A POSTROUTING -o eth1 -j SNAT --to-source 173.180.45.4
COMMIT
# Completed on Fri Nov  7 08:04:46 2014
# Generated by iptables-save v1.4.12 on Fri Nov  7 08:04:46 2014
*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT DROP [0:0]
:http-new-in - [0:0]
:http-new-in2 - [0:0]
:http-new-in3 - [0:0]
:http-new-in4 - [0:0]
:log-n-drop - [0:0]
[5034:387464] -A INPUT -i lo -j ACCEPT
[24047:769576] -A INPUT -d 224.0.0.1/32 -j DROP
[0:0] -A INPUT -i eth0 -p tcp -m state --state INVALID -j LOG --log-prefix "IINVALID:" --log-level 6
[15:6202] -A INPUT -p tcp -m tcp ! --tcp-flags FIN,SYN,RST,ACK SYN -m state --state NEW -j LOG --log-prefix "NEW TCP no SYN:" --log-level 6
[15:6202] -A INPUT -p tcp -m tcp ! --tcp-flags FIN,SYN,RST,ACK SYN -m state --state NEW -j REJECT --reject-with icmp-port-unreachable
[380871:46882660] -A INPUT -s 192.168.111.0/24 -i eth0 -j ACCEPT
... deleted some stuff ...
[192747:55993198] -A INPUT -d 173.180.45.4/32 -i eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT
[11682:337070] -A INPUT -i eth1 -m u32 --u32 "0x6&0xff=0x1&&0x0>>0x16&0x3c@0x0>>0x18=0x8&&0x0&0xff00=0x0" -j DROP
[40:4873] -A INPUT -d 173.180.45.4/32 -i eth1 -p icmp -j ACCEPT
... deleted some direct DROP stuff, including several large sub-nets from China ...
[195:64108] -A INPUT -i eth0 -p udp -m udp --sport 68 --dport 67 -j ACCEPT
[COLOR=#ff0000][755:41328] -A INPUT -i eth1 -m recent --update --seconds 90000 --hitcount 3 --name BADGUY_SSH --rsource -j LOG --log-prefix "SSH BAD:" --log-level 6
[755:41328] -A INPUT -i eth1 -m recent --update --seconds 90000 --hitcount 3 --name BADGUY_SSH --rsource -j DROP
[249:12796] -A INPUT -i eth1 -p tcp -m tcp --dport 22 -m recent --set --name BADGUY_SSH --rsource -j ACCEPT[/COLOR]
[3692:208924] -A INPUT -d 173.180.45.4/32 -i eth1 -p tcp -m state --state NEW -m tcp --dport 80 -j http-new-in
[166:8196] -A INPUT -d 173.180.45.4/32 -i eth1 -p tcp -m state --state NEW -m limit --limit 5/min --limit-burst 3 -m tcp --dport 25 -j ACCEPT
[1243:64125] -A INPUT -i eth1 -p tcp -m multiport --sports 80,443 -j LOG --log-prefix "BAD80:" --log-level 6
[1243:64125] -A INPUT -i eth1 -p tcp -m multiport --sports 80,443 -j REJECT --reject-with icmp-port-unreachable
[5923:479162] -A INPUT -j log-n-drop
... deleted the rest...
```

---


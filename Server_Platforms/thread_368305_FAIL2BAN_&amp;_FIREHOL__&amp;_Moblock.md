---
title: "FAIL2BAN &amp; FIREHOL  &amp; Moblock"
date: 2007-02-23
forum: Server Platforms
---

### Post by shookone on 2007-02-23
FAIL2BAN: bans failed attempts on a service (FTP SSH ETC.)
FIREHOL: iptables firewall
MOBLOCK: blocks ip address from a list of ip addresses (like peerguardian)

Will there be any conflicts if i run fail2ban with my current firehol/moblock settings?

Do fail2ban defaults over ride firehol settings.. All my inbound traffic goes to moblock, ip blocking program.

I believe that the fwstart section of fail2ban will cause some problems. Anyone with any ideas let me know please.

firehol.conf:

```
version 5

#iface
lan_iface="eth1"
net_iface="eth0"

# ip zone variables
lan_ips_zone="192.168.1.0/24"

#Custom Service
server_kaid_ports="tcp/8080 tcp/37500 udp/37500 tcp/34525 udp/34525 tcp/34523 udp/34523 tcp/37501 udp/37501 tcp/34522 udp/34522 tcp/30000 udp/30000"
client_kaid_ports="default"
server_lw_ports="tcp/18548"
client_lw_ports="default"
server_dc_ports="tcp/3117 udp/2290"
client_dc_ports="default"
server_mule_ports="tcp/4662 udp/4672"
client_mule_ports="default"

# service sets
# NOTE: the internal LAN is unprotected against other internal machines by the
#       firewall, as all services are allowed to pass through
lan_services="all"
net_services="mule vnc ftp ssh kaid dc lw"
http_services="http https" #ignores moblock

# moblock settings
iptables --new MOBLOCK
iptables -A MOBLOCK -j NFQUEUE

# IP White Listing 
# (Examples)
# iptables -I OUTPUT -d a.b.c.d -j ACCEPT   | Single IP
# iptables -I OUTPUT -d a.b.c.0/24 -j ACCEPT| Net with Netmask
# iptables -I INPUT -s a.b.c.d -j ACCEPT
# iptables -I INPUT -s a.c.c.0/24 -j ACCEPT

iptables -I OUTPUT -d 66.135.32.175 -j ACCEPT
iptables -I OUTPUT -d 64.34.165.84 -j ACCEPT
iptables -I INPUT -s 66.135.32.175 -j ACCEPT
iptables -I INPUT -s 64.34.165.84 -j ACCEPT
iptables -I OUTPUT -d 72.21.211.32 -j ACCEPT
iptables -I INPUT -s 72.21.211.32 -j ACCEPT
iptables -I OUTPUT -d 66.230.129.242 -j ACCEPT
iptables -I INPUT -s 66.230.129.242 -j ACCEPT
iptables -I OUTPUT -d 65.207.183.49 -j ACCEPT
iptables -I INPUT -s 65.207.183.49 -j ACCEPT
iptables -I INPUT -d 218.55.89.101 -j DROP
iptables -I INPUT -s 218.55.89.101 -j DROP
iptables -I INPUT -d 65.207.183.49 -j DROP
iptables -I INPUT -s 65.207.183.49 -j DROP

## interfaces
interface "${lan_iface}" lan src "${lan_ips_zone}"
        server "${lan_services}" accept
        server "ident" reject with tcp-reset

        client all accept

interface "${net_iface}" net src not "${lan_ips_zone} ${UNROUTABLE_IPS}"
        protection strong 10/sec 10


        server "${net_services}" accept
        server "ident" reject with tcp-reset
        client "${http_services}" accept
        #client all accept
        client all moblock


# routers

# route lan <-> net
router lan2net inface "${lan_iface}" outface "${net_iface}"
        masquerade
        route all accept
router net2lan inface "${net_iface}" outface "${lan_iface}"
        route all accept

FIREHOL_LOG_MODE="ULOG"

```

fail2ban.conf:
```

# Fail2Ban configuration file
#
# $Revision: 1.9 $
#
# 2005.06.21  modified for readability  Iain Lea  iain@bricbrac.de

[DEFAULT]
# Option:  background
# Notes.:  start fail2ban as a daemon. Output is redirect to logfile.
# Values:  [true | false]  Default:  false
#
background = true

# Option:  verbose
# Notes.:  verbosity of the output.
#           0 - regular level
#           1 - INFO level
#           2 - DEBUG level (but commands get executed as opposed to
#                debug option)
# Values:  NUM  Default:  0
#
verbose = 1

# Option:  debug
# Notes.:  enable debug mode. No real commands gets executed but only
#          reported, more verbose output, bypass root user test.
# Values:  [true | false]  Default:  false
#
debug = false

# Option:  logtargets
# Notes.:  log targets. Space separated list of logging targets.
# Values:  STDERR SYSLOG file  Default:  /var/log/fail2ban.log
#
logtargets = /var/log/fail2ban.log

# Option:  syslog-target
# Notes.:  where to find syslog facility if logtarget SYSLOG.
# Values:  SOCKET HOST HOST:PORT  Default: /dev/log
#
syslog-target = /dev/log

# Option:  syslog-facility
# Notes.:  which syslog facility to use if logtarget SYSLOG.
# Values:  NUM  Default: 1
#
syslog-facility = 1

# Option:  pidlock
# Notes.:  path of the PID lock file (must be able to write to file).
# Values:  FILE  Default:  /var/run/fail2ban.pid
#
pidlock = /var/run/fail2ban.pid

# Option:  maxfailures
# Notes.:  number of failures before IP gets banned.
# Values:  NUM  Default:  5
#
maxfailures = 5

# Option:  bantime
# Notes.:  number of seconds an IP will be banned. If set to a negative
#          value, IP will never be unbanned (permanent banning).
# Values:  NUM  Default:  600
#
bantime = 600

# Option:  findtime
# Notes.:  lifetime in seconds of a "failed" log entry.
# Values:  NUM  Default:  600
#
findtime = 600

# Option:  ignoreip
# Notes.:  space separated list of IP's to be ignored by fail2ban.
#          You can use CIDR mask in order to specify a range.
#          Example:  ignoreip = 192.168.0.1/24 123.45.235.65
# Values:  IP  Default:  
#
ignoreip = 

# Option:  cmdstart
# Notes.:  command executed once at the start of Fail2Ban
# Values:  CMD  Default:
#
cmdstart = 

# Option:  cmdend
# Notes.:  command executed once at the end of Fail2Ban.
# Values:  CMD  Default:
#
cmdend = 

# Option:  polltime
# Notes.:  number of seconds fail2ban sleeps between iterations.
# Values:  NUM  Default:  1
#
polltime = 1

# Option:  reinittime
# Notes.:  minimal number of seconds between the re-initialization of
#          firewalls due to external changes in their rules (see fwcheck)
# Values:  NUM  Default:  100
#
reinittime = 10

# Option:  maxreinits
# Notes.:  maximal number of re-initialization of firewalls due to external
#          changes. -1 stays for infinite, so only reinittime is of importance
# Values:  NUM  Default:  -1
#
maxreinits = 1000

# NOTE: Interpolations
#
# fwstart, as well as fwend, fwcheck, fwban, fwunban, use interpolations
# so %(__name__)s  will be substituted by a name of each section
# (unless the option is overriden in a section).
# If you are going to use interpolations in your setup, please make
# sure that you specified options port and protocol (which also has
# an option in DEFAULT).
#

# Option:  protocol
# Notes.:  internally used by config reader for interpolations.
# Values:  [ tcp | udp | icmp | all ] Default: tcp
#
protocol = tcp

# Option:  fwchain
# Notes.:  chain from which to jump into fail2ban chains
# Values:  TEXT  Default: INPUT
#
fwchain = INPUT

# Option:  fwstart
# Notes.:  command executed once at the start of Fail2Ban.
# Values:  CMD  Default:
#
fwstart = iptables -N fail2ban-%(__name__)s
          iptables -A fail2ban-%(__name__)s -j RETURN
          iptables -I %(fwchain)s -p %(protocol)s --dport %(port)s -j fail2ban-%(__name__)s

# Option:  fwend
# Notes.:  command executed once at the end of Fail2Ban
# Values:  CMD  Default:
#
fwend = iptables -D %(fwchain)s -p %(protocol)s --dport %(port)s -j fail2ban-%(__name__)s
        iptables -F fail2ban-%(__name__)s
        iptables -X fail2ban-%(__name__)s

# Option:  fwcheck
# Notes.:  command executed once before each fwban command
# Values:  CMD  Default:
#
fwcheck = iptables -L %(fwchain)s | grep -q fail2ban-%(__name__)s

# Option:  fwban
# Notes.:  command executed when banning an IP. Take care that the
#          command is executed with Fail2Ban user rights.
# Tags:    <ip>  IP address
#          <failures>  number of failures
#          <failtime>  unix timestamp of the last failure
#          <bantime>  unix timestamp of the ban time
# Values:  CMD
# Default: iptables -I INPUT 1 -s <ip> -j DROP
#
fwban = iptables -I fail2ban-%(__name__)s 1 -s <ip> -j DROP

# Option:  fwunban
# Notes.:  command executed when unbanning an IP. Take care that the
#          command is executed with Fail2Ban user rights.
# Tags:    <ip>  IP address
#          <bantime>  unix timestamp of the ban time
#          <unbantime>  unix timestamp of the unban time
# Values:  CMD
# Default: iptables -D INPUT -s <ip> -j DROP
#
fwunban = iptables -D fail2ban-%(__name__)s -s <ip> -j DROP

[MAIL]
# Option:  enabled
# Notes.:  enable mail notification when banning an IP address.
# Values:  [true | false]  Default:  false
#
enabled = false

# Option:  host
# Notes.:  host running the mail server.
# Values:  STR  Default:  localhost
#
host = localhost

# Option:  port
# Notes.:  port of the mail server.
# Values:  INT  Default:  25
#
port = 25

# Option:  user
# Notes.:  the username for smtp-server if authentification is required.
#          if user is empty, no authentification is done.
# Values:  STR  Default:  
#
user = 

# Option:  password
# Notes.:  the smtp-user's password if authentification is required.
# Values:  STR  Default:  
#
password = 

# Option:  from
# Notes.:  e-mail address of the sender.
# Values:  MAIL  Default:  fail2ban
#
from = fail2ban@localhost

# Option:  to
# Notes.:  e-mail addresses of the receiver. Addresses are space
#          separated.
# Values:  MAIL  Default:  root
#
to = root@localhost

# Option:  localtime
# Notes.:  report local time (including timezone) or GMT
# Values:  [true | false]  Default:  false
#
localtime = true

# Option:  subject
# Notes.:  subject of the e-mail.
# Tags:    <section> active section (eg ssh, apache, etc)
#          <ip>  IP address
#          <failures>  number of failures
#          <failtime>  unix timestamp of the last failure
# Values:  TEXT  Default:  [Fail2Ban] <section>: Banned <ip>
#
subject = [Fail2Ban] <section>: Banned <ip>

# Option:  message
# Notes.:  message of the e-mail.
# Tags:    <section> active section (eg ssh, apache, etc)
#          <ip>  IP address
#          <failures>  number of failures
#          <failtime>  unix timestamp of the last failure
#          <br>  new line
# Values:  TEXT  Default:
#
message = Hi,<br>
          The IP <ip> has just been banned by Fail2Ban after
          <failures> attempts against <section>.<br>
          Regards,<br>
          Fail2Ban

# You can define a new section for each log file to check for
# password failure. Each section has to define the following
# options: logfile, fwban, fwunban, timeregex, timepattern,
# failregex.


[SASL]
# Option:  enabled
# Notes.:  enable monitoring for this section.
# Values:  [true | false]  Default:  true
#
enabled = false

# Option:  port
# Notes.:  specifies port to monitor
# Values:  [ NUM | STRING ]  Default:
#
port = smtp

# Option:  logfile
# Notes.:  logfile to monitor.
# Values:  FILE  Default:  /var/log/auth.log
#
logfile = /var/log/mail.log

# Option:  timeregex
# Notes.:  regex to match timestamp
# Values:  [Mar  7 17:53:28]
# Default: \S{3}\s{1,2}\d{1,2} \d{2}:\d{2}:\d{2}
#
timeregex = \S{3}\s{1,2}\d{1,2} \d{2}:\d{2}:\d{2}

# Option:  timepattern
# Notes.:  format used in "timeregex" fields definition. Note that '%' must be
#          escaped with '%' (see http://rgruet.free.fr/PQR2.3.html#timeModule)
# Values:  TEXT  Default:  %%b %%d %%H:%%M:%%S
#
timepattern = %%b %%d %%H:%%M:%%S

# Option:  failregex
# Notes.:  regex to match the password failures messages in the logfile.
# Values:  TEXT  Default:
#
failregex = : warning: [-._\w]+\[(?P<host>[.\d]+)\]: SASL (?:LOGIN|PLAIN|(?:CRAM|DIGEST)-MD5) authentication failed$


[Apache]
# Option:  enabled
# Notes.:  enable monitoring for this section.
# Values:  [true | false]  Default:  false
#
enabled = false

# Option:  logfile
# Notes.:  logfile to monitor.
# Values:  FILE  Default:  /var/log/apache/error.log
# Other.: /var/log/apache2/error.log
#
logfile = /var/log/apache/error.log

# Option:  port
# Notes.:  specifies port to monitor
# Values:  [ NUM | STRING ]  Default:
#
port = http

# Option:  timeregex
# Notes.:  regex to match timestamp in Apache logfile. For TAI64N format,
#          use timeregex = @[0-9a-f]{24}
# Values:  [Wed Jan 05 15:08:01 2005]
# Default: \S{3} \S{3} \d{2} \d{2}:\d{2}:\d{2} \d{4}
#
timeregex = \S{3} \S{3} \d{2} \d{2}:\d{2}:\d{2} \d{4}

# Option:  timepattern
# Notes.:  format used in "timeregex" fields definition. Note that '%' must be
#          escaped with '%' (see http://rgruet.free.fr/PQR2.3.html#timeModule).
#          For TAI64N format, use timepattern = tai64n
# Values:  TEXT  Default:  %%a %%b %%d %%H:%%M:%%S %%Y
#
timepattern = %%a %%b %%d %%H:%%M:%%S %%Y

# Option:  failregex
# Notes.:  regex to match the password failure messages in the logfile.
# Values:  TEXT  Default:  [[]client (?P<host>\S*)[]] user .*(?:: authentication failure|not found)
#
failregex = [[]client (?P<host>\S*)[]] user .*(?:: authentication failure|not found)

[ApacheAttacks]
# Option:  enabled
# Notes.:  enable monitoring for this section.
# Values:  [true | false]  Default:  false
#
enabled = false

# Option:  logfile
# Notes.:  logfile to monitor.
# Values:  FILE  Default:  /var/log/apache/access.log
#
logfile = /var/log/apache/access.log

# Option:  port
# Notes.:  specifies port to monitor
# Values:  [ NUM | STRING ]  Default:
#
port = http

# Option:  maxfailures
# Notes.:  number of failures before IP gets banned.
# Values:  NUM  Default:  5
#
maxfailures = 2

# Option:  timeregex
# Notes.:  regex to match timestamp in Apache access logfile.
# Values:  [19/Feb/2006:08:38:18]
# Default: \d{2}/\S{3}/\d{4}:\d{2}:\d{2}:\d{2}
#
timeregex = \d{2}/\S{3}/\d{4}:\d{2}:\d{2}:\d{2}

# Option:  timepattern
# Notes.:  format used in "timeregex" fields definition. Note that '%' must be
#          escaped with '%' (see http://rgruet.free.fr/PQR2.3.html#timeModule)
# Values:  TEXT  Default: %%d/%%b/%%Y:%%H:%%M:%%S
#
timepattern = %%d/%%b/%%Y:%%H:%%M:%%S

# Option:  failregex
# Notes.:  regex to match the password failure messages in the logfile.
# Values:  TEXT  Default:  [[]client (?P<host>\S*)[]] user .*(?:: authentication failure|not found)
#
failregex = ^(?P<host>\S*) -.*"GET .*(?:awstats\.pl\?configdir=|index2\.php\?_REQUEST\[option\].*)\|echo.*

[VSFTPD]
# Option: enabled
# Notes.: enable monitoring for this section.
# Values: [true | false] Default: false
#
enabled = false

# Option: logfile
# Notes.: logfile to monitor.
# Values: FILE Default: /var/log/secure
#
logfile = /var/log/vsftpd.log

# Option:  port
# Notes.:  specifies port to monitor
# Values:  [ NUM | STRING ]  Default:
#
port = ftp

# Option: timeregex
# Notes.: regex to match timestamp in VSFTPD logfile.
# Values: [Mar 7 17:53:28]
# Default: \S{3}\s{1,2}\d{1,2} \d{2}:\d{2}:\d{2}
#
timeregex = \S{3}\s{1,2}\d{1,2} \d{2}:\d{2}:\d{2}

# Option: timepattern
# Notes.: format used in "timeregex" fields definition. Note that '%' must be
# escaped with '%' (see http://rgruet.free.fr/PQR2.3.html#timeModule)
# Values: TEXT Default: %%b %%d %%H:%%M:%%S
#
timepattern = %%b %%d %%H:%%M:%%S

# Option: failregex
# Notes.: regex to match the password failures messages in the logfile.
# Values: TEXT Default: Authentication failure|Failed password|Invalid user
#
failregex = \[.+\] FAIL LOGIN: Client "(?P<host>\S+)"$


[PROFTPD]
# Option: enabled
# Notes.: enable monitoring for this section.
# Values: [true | false] Default: false
#
enabled = true

# Option: logfile
# Notes.: logfile to monitor.
# Values: FILE Default: /var/log/proftpd/proftpd.log
# Other.: /var/log/auth.log
#
logfile = /var/log/proftpd/proftpd.log

# Option:  port
# Notes.:  specifies port to monitor
# Values:  [ NUM | STRING ]  Default: ftp
#
port = ftp

# Option: timeregex
# Notes.: regex to match timestamp in VSFTPD logfile.
# Values: [Mar 7 17:53:28]
# Default: \S{3}\s{1,2}\d{1,2} \d{2}:\d{2}:\d{2}
#
timeregex = \S{3}\s{1,2}\d{1,2} \d{2}:\d{2}:\d{2}

# Option: timepattern
# Notes.: format used in "timeregex" fields definition. Note that '%' must be
# escaped with '%' (see http://rgruet.free.fr/PQR2.3.html#timeModule)
# Values: TEXT Default: %%b %%d %%H:%%M:%%S
#
timepattern = %%b %%d %%H:%%M:%%S

# Option: failregex
# Notes.: regex to match the password failures messages in the logfile.
# Values: TEXT Default:
#
failregex = USER \S+: no such user found from \S* ?\[(?P<host>\S+)\] to \S+\s*$


[SSH]
# Option:  enabled
# Notes.:  enable monitoring for this section.
# Values:  [true | false]  Default:  true
#
enabled = true

# Option:  logfile
# Notes.:  logfile to monitor.
# Values:  FILE  Default:  /var/log/auth.log
#
logfile = /var/log/auth.log

# Option:  port
# Notes.:  specifies port to monitor
# Values:  [ NUM | STRING ]  Default:
#
port = ssh

# Option:  timeregex
# Notes.:  regex to match timestamp in SSH logfile. For TAI64N format,
#          use timeregex = @[0-9a-f]{24}
# Values:  [Mar  7 17:53:28]
# Default: \S{3}\s{1,2}\d{1,2} \d{2}:\d{2}:\d{2}
#
timeregex = \S{3}\s{1,2}\d{1,2} \d{2}:\d{2}:\d{2}

# Option:  timepattern
# Notes.:  format used in "timeregex" fields definition. Note that '%' must be
#          escaped with '%' (see http://rgruet.free.fr/PQR2.3.html#timeModule).
#          For TAI64N format, use timepattern = tai64n
# Values:  TEXT  Default:  %%b %%d %%H:%%M:%%S
#
timepattern = %%b %%d %%H:%%M:%%S

# Option:  failregex
# Notes.:  regex to match the password failures messages in the logfile.
# Values:  TEXT  Default:  (?:Authentication failure|Failed (?:keyboard-interactive/pam|password)) for(?: illegal user)? .* from (?:::f{4,6}:)?(?P<host>\S*)
#
failregex = : (?:(?:Authentication failure|Failed [-/\w+]+) for(?: [iI](?:llegal|nvalid) user)?|[Ii](?:llegal|nvalid) user|ROOT LOGIN REFUSED) .*(?: from|FROM) (?:::f{4,6}:)?(?P<host>\S*)

```

---

### Post by MJN on 2007-02-23
Fail2ban will create (and delete) its own rules (as the name 'fail2ban') hence will operate quite happily alongside Firehol (and your IP blacklist) without conflict.
 
Mathew

---

### Post by shookone on 2007-02-23
Thanks for the input! I'll continue monitoring and see if there are any changes.

---

### Post by shookone on 2007-02-23
2007-02-23 05:30:50,992 WARNING: Verbose level is 1
2007-02-23 05:30:50,995 INFO: Fail2Ban v0.6.1 is running
2007-02-23 05:30:51,004 INFO: Enabled sections: ['PROFTPD', 'SSH']
2007-02-23 05:30:51,005 WARNING:  is not a valid IP address


Whats not a valid ip?

---

### Post by MJN on 2007-02-23
Safe to ignore that - it's just a quirk of Fail2Ban.
 
Mathew

---

### Post by shookone on 2007-02-24
sweet. Thanks guys.

---

### Post by Johan! on 2007-02-24
> 2007-02-23 05:30:50,992 WARNING: Verbose level is 1
2007-02-23 05:30:50,995 INFO: Fail2Ban v0.6.1 is running
2007-02-23 05:30:51,004 INFO: Enabled sections: ['PROFTPD', 'SSH']
2007-02-23 05:30:51,005 WARNING: is not a valid IP address


Whats not a valid ip?

```

# Option:  ignoreip
# Notes.:  space separated list of IP's to be ignored by fail2ban.
#          You can use CIDR mask in order to specify a range.
#          Example:  ignoreip = 192.168.0.1/24 123.45.235.65
# Values:  IP  Default:  
#
ignoreip = 
```

Enter an IP address after **ignoreip = ** and the warning is gone :)

---

### Post by yellowtip on 2007-04-13
Hopefully you guys can help me out with Fail2ban ...I've been trying to get it to work on several servers, but somehow doesn't seem to work.

All seems to be running fine... I used apt-get install fail2ban to install, and all goes fine. In the fail2ban logfile, I also don't see any major problems.

2007-04-14 05:55:01,454 WARNING: Verbose level is 1
2007-04-14 05:55:01,459 INFO: Fail2Ban v0.6.0 is running
2007-04-14 05:55:01,464 INFO: Enabled sections: ['SSH']
2007-04-14 05:57:18,682 INFO: SSH: xxx.xxx.xxx.xxx has 5 login failure(s). Banned
.
2007-04-14 05:57:18,686 WARNING: SSH: Ban xxx.xxx.xxx.xxx

( Note: In the log above, I replaced the real IP address with xxx.xxx.xxx.xxx )

However, it's not blocking the hosts that fail to authenticate! 

I also have ipkungfu installed as my firewall. Could that be conflicting with fail2ban?

Any help is highly appreciated! Thanks in advance!

---

### Post by MJN on 2007-04-13
Fail2ban uses the firewall as it's means to block login attempts. IPTables is the default hence the question is therefore, did you configure Fail2Ban to control IPKungFu?

Mathew

---

### Post by yellowtip on 2007-04-13
> **MJN said:**
> Fail2ban uses the firewall as it's means to block login attempts. IPTables is the default hence the question is therefore, did you configure Fail2Ban to control IPKungFu?

Mathew

Thanks for the quick response Mathew.

As I know...ipkungu is merely a frontend to IPTables.. so essentially, I'm running IpTables.

...or am I missing someting?

---

### Post by MJN on 2007-04-13
Ah, no, it was me. I've never heard of ipkungfu so when you said you were using it for your firewall I assumed you therefore meant you weren't using iptables.

In that case, what's the output of **sudo iptables -L -n** There should be fail2ban chains listed (regardless whether anything's currently banned). Try then tripping fail2ban and checking to see if an extra rule is added for the offending IP (remember it potentially only lasts a short period - 10 mins by default?).

Mathew

---

### Post by yellowtip on 2007-04-13
> **MJN said:**
> Ah, no, it was me. I've never heard of ipkungfu so when you said you were using it for your firewall I assumed you therefore meant you weren't using iptables.

In that case, what's the output of **sudo iptables -L -n** There should be fail2ban chains listed (regardless whether anything's currently banned). Try then tripping fail2ban and checking to see if an extra rule is added for the offending IP (remember it potentially only lasts a short period - 10 mins by default?).

Mathew

It does seem to add an extra rule:

Chain fail2ban-SSH (1 references)
target     prot opt source               destination
DROP       all  --  xxx.xxx.xxx.xxx         0.0.0.0/0
RETURN     all  --  0.0.0.0/0            0.0.0.0/0

but...still nothing is blocked...

---

### Post by yellowtip on 2007-04-14
I went ahead and removed fail2ban as I don't want to run the risk of fail2ban conflicting with iptables.

However, I'd love to hear from anybody who has both fail2ban and ipkungfu running together successfully.

Anybody?

---


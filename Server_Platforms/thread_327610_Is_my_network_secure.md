---
title: "Is my network secure?"
date: 2006-12-29
forum: Server Platforms
---

### Post by casperlingus on 2006-12-29
I don't have a clear, specific question to ask, except, "is my setup safe?"   I would like to explain the setup that I have at home and ask if anyone sees a problem with it.  My dad is really paranoid about security, and I'm not familiar with the scope of security issues.

I'm not sure how significant it is, but our home has a static IP address in the DMZ.  It has had the same IP address for the last 4 years.  I have no need for dyndns.

Our home has 6 computers.   4 windows machines, and two linux boxes.  There's a router with firewall on the DMZ acting as the gateway.  One of the linux boxes is my main computer, for which I have set up a specific port (not 22) to accept SSH requests.  I have enabled port forwarding from the router to my computer's internal (static) IP address.  If someone wanted to SSH into my computer, they would need our DMZ IP address AND the port#.

Additionally, I have an old 400 MHz computer running Ubuntu server, with Samba and Apache.  It is setup to act as a fileserver for the house, via samba, so all machines can access its 300 GB HDD.  I have also port forwarded all http requests from the router to *that* computer.  That works as well:  all you do is type my IP address into a browser from anywhere in the world and you get my homepage served from that computer.

To summarize:
1) Our network has a static IP from the DMZ
2) Port forwarding has been enabled on two ports
    -One non-standard port for SSH requests to a Ubuntu box
    -Standard port forwarding for HTTP requests to an Ubuntu Server box
3) All machines (4 windows, 2 linux) are running samba

Is there any reason to feel insecure about this?

Casper...

---

### Post by meng on 2006-12-29
(I'm not a networking expert, but...)
I assume you have a wireless home network - any encryption or other security measures?
You may wish to consider RSA key encryption with your SSH if you haven't got this already.

---

### Post by houstonbofh on 2006-12-29
A few points...

First on the SSH, since everyone moves the SSH port, people now stealth sweep for SSH on most ports.  I leave mine on 22, and run fail2ban.  I LOVE this program.  I just wish the repositories were more current.

On the web server, what else you got?  Is it LAMP?  Have you removed all the cgi scripts you do not need?  Is all your active code secure?  The overall answer is probably, but you need to look further.

The router...  Is it a real firewall, or a UPnP cheap hunk of junk?  A lot of attack vectors are set up to look like games to consumer routers.

The Windows boxes.  They are your most likely source of trouble.  You just can't keep them clean without constant supervision.

---

### Post by Brazen on 2006-12-29
It sounds like your pretty secure from the outside, but like Rome you can be conquered from within.  Using limited user accounts, having a good virus scanner (Trend Micro or Kapersky) and using Firefox with the NoScript addon are two of my top suggestions on the Windows boxen.  If limiting to Firefox is unfeasible, make sure you have a malware scanner also (though I think Trend Micro and Kapersky scan for all malware).

The other thing is wireless security:  don't broadcast your SSID, change the default SSID, add WEP or WPA, and use wireless MAC filtering.

---

### Post by evilghost on 2006-12-29
You are fairly secure, I can't rate you as any more secure because you've got Win32 machines :)

SSH:  Changing the default port is good.  Consider also setting these options in /etc/ssh/sshd_config and moving to key based authentication.

Keybased auth:  [http://www.cyberciti.biz/tips/ssh-public-key-based-authentication-how-to.html](http://www.cyberciti.biz/tips/ssh-public-key-based-authentication-how-to.html)

```

PermitRootLogin no
PasswordAuthentication no
MaxAuthTries 1
RSAAuthentication yes
PubkeyAuthentication yes

```

Apache:  You may want to consider using suhosin if you're running PHP.  Additionally I'd use mod-security as well as mod-evasive for additional protection.

suhosin:  [http://advosys.ca/viewpoints/2006/11/hardening-php-servers-with-suhosin/](http://advosys.ca/viewpoints/2006/11/hardening-php-servers-with-suhosin/)
mod_evasive:  [http://advosys.ca/viewpoints/2006/08/installing-mod_evasive-in-ubuntu/](http://advosys.ca/viewpoints/2006/08/installing-mod_evasive-in-ubuntu/)
mod_security:  [http://www.debuntu.org/2006/08/13/86-secure-your-apache2-with-mod-security](http://www.debuntu.org/2006/08/13/86-secure-your-apache2-with-mod-security)

fail2ban:  An excellent tool, I **strongly** recommend using fail2ban.  Point it at any authentication system you have.  I've got mine pointed at SSH as well as Apache (watching 404s).  Below is my configuration.

```

# Fail2Ban configuration file
#
# $Revision: 1.2.2.1 $
#
# 2005.06.21  modified for readability  Iain Lea  iain@bricbrac.de

[DEFAULT]
background = false
logtargets = /var/log/fail2ban.log
syslog-target = /dev/log
syslog-facility = 1
pidlock = /var/run/fail2ban.pid
maxfailures = 10
bantime = 3600
findtime = 600
ignoreip = 192.168.1.0/24
cmdstart = 
cmdend = 
polltime = 1
reinittime = 10
maxreinits = -1

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

# Option:  fwstart
# Notes.:  command executed once at the start of Fail2Ban.
# Values:  CMD  Default:
#
fwstart = iptables -N fail2ban-%(__name__)s
          iptables -A fail2ban-%(__name__)s -j RETURN
          iptables -I INPUT -p %(protocol)s --dport %(port)s -j fail2ban-%(__name__)s

# Option:  fwend
# Notes.:  command executed once at the end of Fail2Ban
# Values:  CMD  Default:
#
fwend = iptables -D INPUT -p %(protocol)s --dport %(port)s -j fail2ban-%(__name__)s
        iptables -F fail2ban-%(__name__)s
        iptables -X fail2ban-%(__name__)s

# Option:  fwcheck
# Notes.:  command executed once before each fwban command
# Values:  CMD  Default:
#
fwcheck = iptables -L INPUT | grep -q fail2ban-%(__name__)s

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
enabled = true
host = 192.168.1.2
port = 25
user = 
password = 
from = fail2ban
to = root@localhost
localtime = true
subject = [Fail2Ban] <section>: Banned <ip>
message = The IP <ip> has just been banned by Fail2Ban after <failures> attempts against <section>.<br>

[Apache]
enabled = true
logfile = /var/log/apache2/error.log
port = 80:443
timeregex = \S{3} \S{3} \d{2} \d{2}:\d{2}:\d{2} \d{4}
timepattern = %%a %%b %%d %%H:%%M:%%S %%Y
failregex = File does not exist

[Webmail]
enabled = true
logfile = /home/e-smith/files/ibays/primary/logs/errors
port = 80:443
timeregex = \S{3}-\S{3}-\d{4} \d{2}:\d{2}:\d{2}
timepattern = [%%d-%%b-%%Y %%H:%%M:%%S
failregex = Authentication failed

[SSH]
enabled = true
logfile = /var/log/auth.log
port = 57601
timeregex = \S{3}\s{1,2}\d{1,2} \d{2}:\d{2}:\d{2}
timepattern = %%b %%d %%H:%%M:%%S
failregex = Authentication failure|Failed password|Invalid user

[dovecot]
enabled = true
logfile = /var/log/auth.log
port = 993:995
timeregex = \S{3}\s{1,2}\d{1,2} \d{2}:\d{2}:\d{2}
timepattern = %%b %%d %%H:%%M:%%S
failregex = authentication failure

[postfix]
enabled = true
logfile = /var/log/mail.log
port = 465
timeregex = \S{3}\s{1,2}\d{1,2} \d{2}:\d{2}:\d{2}
timepattern = %%b %%d %%H:%%M:%%S
failregex = Access denied

```

---


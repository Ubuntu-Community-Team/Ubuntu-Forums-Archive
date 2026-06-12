---
title: "Fail2ban not banning?"
date: 2010-05-05
forum: Server Platforms
---

### Post by dacool25 on 2010-05-05
I've had fail2ban installed for quite a while now, but every once and a while I'll look in the logs and see a message like so:

```
2010-05-03 08:40:02,410 fail2ban.actions: WARNING [courierimap] 118.129.167.99 already banned
2010-05-03 08:40:28,464 fail2ban.actions: WARNING [courierimap] 118.129.167.99 already banned
2010-05-03 08:40:53,549 fail2ban.actions: WARNING [courierimap] 118.129.167.99 already banned
2010-05-03 08:41:19,615 fail2ban.actions: WARNING [courierimap] 118.129.167.99 already banned
2010-05-03 08:41:44,674 fail2ban.actions: WARNING [courierimap] 118.129.167.99 already banned
2010-05-03 08:42:10,754 fail2ban.actions: WARNING [courierimap] 118.129.167.99 already banned
2010-05-03 08:42:35,823 fail2ban.actions: WARNING [courierimap] 118.129.167.99 already banned
2010-05-03 08:42:35,823 fail2ban.actions: WARNING [courierimap] Unban 118.129.167.99
2010-05-03 08:43:01,959 fail2ban.actions: WARNING [courierimap] Ban 118.129.167.99

```

I understand that fail2ban takes a little while to actually search the logs in order to block the ports, but if it's already unbanning the ip address, doesn't that mean that it's seen it in the log?

Here's my jail.local:

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
bantime  = 180
maxretry = 4

# "backend" specifies the backend used to get files modification. Available
# options are "gamin", "polling" and "auto".
# yoh: For some reason Debian shipped python-gamin didn't work as expected
#      This issue left ToDo, so polling is default backend for now
backend = polling

#
# Destination email address used solely for the interpolations in
# jail.{conf,local} configuration files.
destemail = webmaster@mydomain.com

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
maxretry = 3

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

enabled = true
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


[pure-ftpd]
enabled  = true
port     = ftp
filter   = pure-ftpd
logpath  = /var/log/messages
maxretry = 3


#
# Mail servers
#

[postfix]

enabled  = false
port	 = smtp,ssmtp
filter   = postfix
logpath  = /var/log/mail.log


[courierimap]

enabled  = true
port     = imap2
filter   = courierlogin
logpath  = /var/log/mail.log
maxretry = 4

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

enabled  = true
port	 = smtp,ssmtp,imap2,imap3,imaps,pop3,pop3s
filter   = sasl
# You might consider monitoring /var/log/warn.log instead
# if you are running postfix. See http://bugs.debian.org/507990
logpath  = /var/log/mail.log
maxretry = 4


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

---

### Post by Queue29 on 2010-05-05
IIRC, bantime is measured in seconds, so your

```
bantime  = 180
```

is blocking them for only 3 minutes. Which, by the looks of your logs, appears to be correct.

I think it also has a 3 digit limitation, so the max ban time is 999s, or about 16 minutes.

---

### Post by dacool25 on 2010-05-05
Yeah, I'm fine with a 3 minute blocking time. What I'm worried about is the messages saying that it's "already blocked". Is that normal?

---

### Post by cdenley on 2010-05-05
Post this output.
```

sudo iptables -n -L INPUT

```

---

### Post by dacool25 on 2010-05-05
Here's the output, just bear in mind that I'm not blocking any ip addresses at the moment.

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
fail2ban-apache  tcp  --  0.0.0.0/0            0.0.0.0/0           multiport dports 80,443 
fail2ban-sasl  tcp  --  0.0.0.0/0            0.0.0.0/0           multiport dports 25,465,143,220,993,110,995 
fail2ban-ssh  tcp  --  0.0.0.0/0            0.0.0.0/0           multiport dports 22 
fail2ban-courierimap  tcp  --  0.0.0.0/0            0.0.0.0/0           multiport dports 143 
fail2ban-pure-ftpd  tcp  --  0.0.0.0/0            0.0.0.0/0           multiport dports 21 

```

---

### Post by cdenley on 2010-05-05
> **dacool25 said:**
> Here's the output, just bear in mind that I'm not blocking any ip addresses at the moment.

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
fail2ban-apache  tcp  --  0.0.0.0/0            0.0.0.0/0           multiport dports 80,443 
fail2ban-sasl  tcp  --  0.0.0.0/0            0.0.0.0/0           multiport dports 25,465,143,220,993,110,995 
fail2ban-ssh  tcp  --  0.0.0.0/0            0.0.0.0/0           multiport dports 22 
fail2ban-courierimap  tcp  --  0.0.0.0/0            0.0.0.0/0           multiport dports 143 
fail2ban-pure-ftpd  tcp  --  0.0.0.0/0            0.0.0.0/0           multiport dports 21 

```

I just wanted to make sure there wasn't a rule inserted before the fail2ban chain which was accepting traffic from banned IP's. Even with the short bantime, it looks like they are still managing to attempt authentication when they should be banned. I don't think this should happen. Can you test to see if you can get banned, or provide your public IP so we can? Can you post the output for
```

sudo iptables -L -n

```
while someone is banned?

---

### Post by dacool25 on 2010-05-05
Well, how would I test it for courier? I have roundcube webmail on the server, but that doesn't trigger a courier failed login attempt in the logs. 

Just for kicks, this is what happens with ftp failed logins (but those seem to be correctly blocking):

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
fail2ban-apache  tcp  --  0.0.0.0/0            0.0.0.0/0           multiport dports 80,443 
fail2ban-sasl  tcp  --  0.0.0.0/0            0.0.0.0/0           multiport dports 25,465,143,220,993,110,995 
fail2ban-ssh  tcp  --  0.0.0.0/0            0.0.0.0/0           multiport dports 22 
fail2ban-courierimap  tcp  --  0.0.0.0/0            0.0.0.0/0           multiport dports 143 
fail2ban-pure-ftpd  tcp  --  0.0.0.0/0            0.0.0.0/0           multiport dports 21 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain fail2ban-apache (1 references)
target     prot opt source               destination         
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           

Chain fail2ban-courierimap (1 references)
target     prot opt source               destination         
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           

Chain fail2ban-pure-ftpd (1 references)
target     prot opt source               destination         
DROP       all  --  149.152.132.12       0.0.0.0/0           
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           

Chain fail2ban-sasl (1 references)
target     prot opt source               destination         
RETURN     all  --  0.0.0.0/0            0.0.0.0/0           

Chain fail2ban-ssh (1 references)
target     prot opt source               destination         
RETURN     all  --  0.0.0.0/0            0.0.0.0/0 
```

---

### Post by cdenley on 2010-05-05
You're only blocking port 143 for connections banned with that filter. They are probably authenticating using another port (SSL?) or another service which logs "LOGIN FAILED" to /var/log/mail.log.

---

### Post by dacool25 on 2010-05-06
Alright, here's the log for my latest courier breakin attempt:

```
May  6 11:07:27 cw-ws pop3d: Connection, ip=[::ffff:76.73.39.90]
May  6 11:07:27 cw-ws pop3d: LOGIN FAILED, user=admin, ip=[::ffff:76.73.39.90]
May  6 11:07:32 cw-ws pop3d: LOGIN FAILED, user=info, ip=[::ffff:76.73.39.90]
May  6 11:07:38 cw-ws pop3d: LOGIN FAILED, user=postmaster, ip=[::ffff:76.73.39.90]
May  6 11:07:43 cw-ws pop3d: LOGIN FAILED, user=postmaster, ip=[::ffff:76.73.39.90]
May  6 11:07:48 cw-ws pop3d: LOGIN FAILED, user=sales, ip=[::ffff:76.73.39.90]

```
It looks like it's using pop3d, so how could I find out what port (if it's not 143)?

---

### Post by cdenley on 2010-05-06
I believe pop3 uses TCP 110.
```

sudo netstat -tlnp

```
Or you can just filter all traffic from banned IP's.
```

[courierimap]

enabled  = true
banaction = iptables-allports
port     = anyport
filter   = courierlogin
logpath  = /var/log/mail.log
maxretry = 4

```

---

### Post by dacool25 on 2010-05-06
Don't even see pop3:

```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:81              0.0.0.0:*               LISTEN      2075/apache2    
tcp        0      0 0.0.0.0:8081            0.0.0.0:*               LISTEN      2075/apache2    
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      2363/pure-ftpd (SER
tcp        0      0 *externalip*:53       0.0.0.0:*               LISTEN      1723/mydns      
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      1723/mydns      
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      913/sshd        
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1811/master     
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      2075/apache2    
tcp        0      0 0.0.0.0:60902           0.0.0.0:*               LISTEN      685/rpc.statd   
tcp        0      0 127.0.0.1:10024         0.0.0.0:*               LISTEN      2677/amavisd (maste
tcp        0      0 127.0.0.1:10025         0.0.0.0:*               LISTEN      1811/master     
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN      1115/mysqld     
tcp        0      0 127.0.0.1:783           0.0.0.0:*               LISTEN      1186/spamd.pid  
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      656/portmap     
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      2075/apache2    
tcp6       0      0 :::21                   :::*                    LISTEN      2363/pure-ftpd (SER
tcp6       0      0 ::1:53                  :::*                    LISTEN      1723/mydns      
tcp6       0      0 :::22                   :::*                    LISTEN      913/sshd        
tcp6       0      0 :::993                  :::*                    LISTEN      1683/couriertcpd
tcp6       0      0 :::995                  :::*                    LISTEN      1719/couriertcpd
tcp6       0      0 :::110                  :::*                    LISTEN      1698/couriertcpd
tcp6       0      0 :::143                  :::*                    LISTEN      1662/couriertcpd

```

---

### Post by cdenley on 2010-05-06
> **dacool25 said:**
> Don't even see pop3

pop3d is part of courier, which is listening on port 110. It is also listening on 993 and 995, so you should block those ports as well.

---

### Post by dacool25 on 2010-05-06
Hmm, then how come it doesn't have a foreign address? Would that be why it's not blocking it?

---

### Post by cdenley on 2010-05-06
> **dacool25 said:**
> Hmm, then how come it doesn't have a foreign address? Would that be why it's not blocking it?

Listening processes don't have foreign addresses. It IS blocking on the port you told it to block on. However, it isn't the port the attackers are using, which is why fail2ban tries to ban them when they are already banned.

---

### Post by dacool25 on 2010-05-06
I see, I see. Hmm, I would of thought that the mail logs would have said the port that they are connecting to, no?

---

### Post by cdenley on 2010-05-06
> **dacool25 said:**
> I see, I see. Hmm, I would of thought that the mail logs would have said the port that they are connecting to, no?

No, but it did leave you a pretty good hint (pop3d). The port that gets filtered as the result of a ban is specified in fail2ban's jail.conf file. You set that to "imap2", which means port TCP 143.
```

getent services imap2

```
So fail2ban bans them, which filters traffic coming from their IP on port 143. Except they're not using port 143, they're using the pop3 service, probably on port 110, or port 995 with SSL. Even if they were using IMAP, they would still be able to use it with SSL on port 993.

---

### Post by dacool25 on 2010-05-06
I see! Here's the results of that:
```
imap2                 143/tcp imap
```

So in my jail.local file if I just add the name of the service that uses port 110, it should block on that port, right?

```
[courierimap]

enabled  = true
port     = imap2
filter   = courierlogin
logpath  = /var/log/mail.log   
maxretry = 4

```

So my next question is, you guessed it :) ...What's the name of the service that uses 110?

---

### Post by dacool25 on 2010-05-06
Found it, it's just pop3.

So I could just edit my jail.local as so, right?
```
[courierimap]

enabled  = true
port     = imap2,pop3
filter   = courierlogin
logpath  = /var/log/mail.log   
maxretry = 4
```

---

### Post by cdenley on 2010-05-06
> **dacool25 said:**
> Found it, it's just pop3.

So I could just edit my jail.local as so, right?
```
[courierimap]

enabled  = true
port     = imap2,pop3
filter   = courierlogin
logpath  = /var/log/mail.log   
maxretry = 4
```

But then you still have 993 and 995!
```

[courierimap]

enabled  = true
port     = imap2,pop3,imaps,pop3s
filter   = courierlogin
logpath  = /var/log/mail.log   
maxretry = 4

```
Or you can just filter all ports like I suggested earlier.
[http://ubuntuforums.org/showpost.php?p=9248670&postcount=10](http://ubuntuforums.org/showpost.php?p=9248670&postcount=10)

---

### Post by dacool25 on 2010-05-06
I see what you're saying now. I'll do that. I really appreciate your help, and I'll update soon and see if it worked.

---


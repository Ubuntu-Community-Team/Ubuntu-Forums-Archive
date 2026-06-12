---
title: "Postfix cannot receive, can send. PPTP connection."
date: 2014-09-19
forum: Server Platforms
---

### Post by Malalo on 2014-09-19
Hello !

I had set up a server a while ago but it crashed hard. So I'm in the process of re-building it from scratch, since the old hard drive is unreadable.

I'm trying to setup the mail server with Postfix. I can send mail to web addresses (such as Hotmail and Gmail) by going through my ISP's SMTP relay.
This works fine.

However, I cannot seem to receive anything. The port 25 does not reply to a telnet from outside. It is not a "your ISP is blocking port 25" issue, please read my setup.

Here is my setup :
- Dynamic WAN IP address, I have a NO-IP client updating it for my [www.domain.com](www.domain.com) and ftp.domain.com aliases.
- PPTP tunnel with fixed IP address and all ports open. Alias mail.domain.com points to this IP address.
- PPTP connection seems to be working (ifconfig shows it with correct IP address).

Copy of main.cf (domain information masked with ~~~~~) :
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = mail.~~~~~.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = $mydomain
mydestination = mail.~~~~~.com, ~~~~~.com
relayhost = smtp.myisp.com
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
swap_bangpath = no
masquerade_domains = $mydomain
allow_percent_hack = no
mynetworks = *my fixed PPTP IP address*, 127.0.0.1

```

Copy of master.cf :
```
#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master" or
# on-line: http://www.postfix.org/master.5.html).
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
#smtp      inet  n       -       -       -       1       postscreen
#smtpd     pass  -       -       -       -       -       smtpd
#dnsblog   unix  -       -       -       -       0       dnsblog
#tlsproxy  unix  -       -       -       -       0       tlsproxy
#submission inet n       -       -       -       -       smtpd
#  -o syslog_name=postfix/submission
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_reject_unlisted_recipient=no
#  -o smtpd_client_restrictions=$mua_client_restrictions
#  -o smtpd_helo_restrictions=$mua_helo_restrictions
#  -o smtpd_sender_restrictions=$mua_sender_restrictions
#  -o smtpd_recipient_restrictions=
#  -o smtpd_relay_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       -       -       -       smtpd
#  -o syslog_name=postfix/smtps
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_reject_unlisted_recipient=no
#  -o smtpd_client_restrictions=$mua_client_restrictions
#  -o smtpd_helo_restrictions=$mua_helo_restrictions
#  -o smtpd_sender_restrictions=$mua_sender_restrictions
#  -o smtpd_recipient_restrictions=
#  -o smtpd_relay_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628       inet  n       -       -       -       -       qmqpd
pickup    unix  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      unix  n       -       n       300     1       qmgr
#qmgr     unix  n       -       n       300     1       oqmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       -       -       -       smtp
relay     unix  -       -       -       -       -       smtp
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
#
# ====================================================================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# Many of the following services use the Postfix pipe(8) delivery
# agent.  See the pipe(8) man page for information about ${recipient}
# and other message envelope options.
# ====================================================================
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
#
# ====================================================================
#
# Recent Cyrus versions can use the existing "lmtp" master.cf entry.
#
# Specify in cyrus.conf:
#   lmtp    cmd="lmtpd -a" listen="localhost:lmtp" proto=tcp4
#
# Specify in main.cf one or more of the following:
#  mailbox_transport = lmtp:inet:localhost
#  virtual_transport = lmtp:inet:localhost
#
# ====================================================================
#
# Cyrus 2.1.5 (Amos Gouaux)
# Also specify in main.cf: cyrus_destination_recipient_limit=1
#
#cyrus     unix  -       n       n       -       -       pipe
#  user=cyrus argv=/cyrus/bin/deliver -e -r ${sender} -m ${extension} ${user}
#
# ====================================================================
# Old example of delivery via Cyrus.
#
#old-cyrus unix  -       n       n       -       -       pipe
#  flags=R user=cyrus argv=/cyrus/bin/deliver -e -m ${extension} ${user}
#
# ====================================================================
#
# See the Postfix UUCP_README file for configuration details.
#
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix	-	n	n	-	2	pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}


```

Any ideas ?

Thanks !

---

### Post by Malalo on 2014-09-19
Some additional information

hosts file :
```
127.0.0.1	localhost
127.0.1.1	server

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
127.0.0.1	mail.~~~~~.com
*PPTP fixed IP address*	mail.~~~~~.com
```

netstat -anltp :
```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN      11149/dovecot   
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN      11149/dovecot   
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN      2024/perl       
tcp        0      0 127.0.0.1:3350          0.0.0.0:*               LISTEN      1489/xrdp-sesman
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1213/sshd       
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      32502/cupsd     
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      18515/master    
tcp        0      0 0.0.0.0:3389            0.0.0.0:*               LISTEN      1483/xrdp       
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN      11149/dovecot   
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN      11149/dovecot   
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1404/mysqld     
tcp        0      0 local_IP_address:10000     work_IP:61670     ESTABLISHED 18655/perl      
tcp        0      0 local_IP_address:10000     work_IP:61671     ESTABLISHED 18656/perl      
tcp        0      0 local_IP_address:38367     ISP_address_for_PPTP_tunnel:1723     ESTABLISHED 10395/pptp      
tcp        0   1675 local_IP_address:10000     work_IP:61669     ESTABLISHED 18654/index.cgi 
tcp6       0      0 :::110                  :::*                    LISTEN      11149/dovecot   
tcp6       0      0 :::143                  :::*                    LISTEN      11149/dovecot   
tcp6       0      0 :::80                   :::*                    LISTEN      1585/apache2    
tcp6       0      0 :::22                   :::*                    LISTEN      1213/sshd       
tcp6       0      0 ::1:631                 :::*                    LISTEN      32502/cupsd     
tcp6       0      0 :::25                   :::*                    LISTEN      18515/master    
tcp6       0      0 :::993                  :::*                    LISTEN      11149/dovecot   
tcp6       0      0 :::995                  :::*                    LISTEN      11149/dovecot   
tcp6       1      0 ::1:35565               ::1:631                 CLOSE_WAIT  1348/cups-browsed
tcp6       1      0 ::1:35648               ::1:631                 CLOSE_WAIT  2338/indicator-prin
```

---


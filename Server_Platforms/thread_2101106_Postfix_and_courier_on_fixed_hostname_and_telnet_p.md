---
title: "Postfix and courier on fixed hostname and telnet problems"
date: 2013-01-03
forum: Server Platforms
---

### Post by jimmi4u on 2013-01-03
Hi folks!
I'm quite new on this, played many hours with installing a mail server,  but I'm stuck on several issues an need help for resolving them. 

- I'm running Ubuntu 12.04.1 LTS on a VPS with a fixed host (not my domain)
- I set up the A/C Names and the MX record pointing to the IP Adress of the host and    resolving them is possible. 

What I want to do is:
 - install only an IMAP server (courier is already installed)
 - install Postfix as a marthost forwarding mails from the host to another server
 - install roundcube for webmail
 - clamAV, amavis are also necessary

but  the problem is that I cannot telnet to localhost on any port. master is  listening on 0.0.0.0, firewall has the ports open but I'm always  getting a connection timed out.
The second part is that I don't know  which adresse I should give as FQDN for postfix. The hostname (which is  unfortunately not a FQDN but only the host which I can't change) or the  full domain name of the mailserver (hostname + domain) or my domain name  which points to the IP adress of the mailserver. I'm not sure. 
So those were the first two questions and  I hope that someone can answer them. I read a lot of instruction but they all lead to the same disaster.
Thanks in advice. 
jimmi
oh yes the netstat -pltun:
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 serverIP:53        0.0.0.0:*               LISTEN      188/named
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      188/named
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      441/sshd
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      7223/master
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      188/named
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      6544/mysqld
tcp6       0      0 :::53                   :::*                    LISTEN      188/named
tcp6       0      0 :::22                   :::*                    LISTEN      441/sshd
tcp6       0      0 :::25                   :::*                    LISTEN      7223/master
tcp6       0      0 :::993                  :::*                    LISTEN      6495/couriertcpd
tcp6       0      0 :::995                  :::*                    LISTEN      6430/couriertcpd
tcp6       0      0 :::110                  :::*                    LISTEN      6379/couriertcpd
tcp6       0      0 :::143                  :::*                    LISTEN      6452/couriertcpd
udp        0      0 serverIP:53        0.0.0.0:*                           188/named
udp        0      0 127.0.0.1:53            0.0.0.0:*                           188/named
udp6       0      0 :::53                   :::*                                188/named

and the /etc/postfix/master.cf:
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
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       -       -       -       smtpd
#  -o syslog_name=postfix/smtps
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628       inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       n       300     1       oqmgr
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

mail.err:
Jan  3 16:40:01 "myhostname" sm-msp-queue[824]: My unqualified host name ("myhostname") unknown; sleeping for retry
Jan  3 16:41:01 "myhostmane" sm-msp-queue[824]: unable to qualify my own domain name ("myhostname") -- using short name
(the "myhostname" was changed here)

---


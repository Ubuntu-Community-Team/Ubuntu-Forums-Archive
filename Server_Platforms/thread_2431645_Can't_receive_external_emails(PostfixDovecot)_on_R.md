---
title: "Can't receive external emails(Postfix/Dovecot) on Raspberry pi"
date: 2019-11-19
forum: Server Platforms
---

### Post by jelletje18 on 2019-11-19
About a week ago my mailserver, locally hosted on a raspberry pi, was still working. I could receive and send email via the gmail website. I used pop3(port 995) to receive email and smtp(port 587) to send email. (For privacy reasons i used example.com instead of my actual domain name.)


Two days ago things stopped working as normal. Things i can do right now:


 - I can send emails to external addresses using gmail.
 - I can receive emails, using pop3, sent to my own emailaddress.
 - I can send emails to my own emailaddress from my own server using sendmail. So local emails work.


The problem arises when I try to send an email from an external emailaddress(e.g. hotmail) to my server. Nothing happens at all. It does not show op in any logs(/var/log/mail.log) and some hours later, on the external email, I receive an email that the mail could not be sent.


I can ping my server, my webserver is function fine. I can telnet into my server just fine.


The ports are successfully opened, I even tried to completely open the Pi to the world, this did not change anything. I have a static IP-address as well. In the router I have assigned a static IP to the Pi


I tried openssl s_client -connect mail.example.com:995, this gives no errors.


This is my main.cf:


```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname


smtpd_banner = $myhostname ESMTP $mail_name (Raspbian)
biff = no


# appending .domain is the MUA's job.
append_dot_mydomain = no


# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h


readme_directory = no


# TLS parameters
smtpd_tls_cert_file=/etc/letsencrypt/live/example.com/fullchain.pem
smtpd_tls_key_file=/etc/letsencrypt/live/example.com/privkey.pem
smtpd_use_tls=yes
smtpd_tls_auth_only = yes


smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_auth_enable = yes


smtpd_recipient_restrictions =
          permit_sasl_authenticated,
          permit_mynetworks,
          reject_unauth_destination


# Milter configuration
#milter_default_action = accept
#milter_protocol = 6
#smtpd_milters = local:/opendkim/opendkim.sock
#non_smtpd_milters = $smtpd_milters


# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.


myhostname = example.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhost
relayhost = [smtp.tweak.nl]:587
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all


#Handing off local delivery to Dovecot's LMTP, and telling it where to store mail
virtual_transport = lmtp:unix:private/dovecot-lmtp


#Virtual domains, users, and aliases
virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual-mailbox-domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual-mailbox-maps.cf
virtual_alias_maps = mysql:/etc/postfix/mysql-virtual-alias-maps.cf


inet_protocols = ipv4
```


Here is the result of netstat -tulpn:


```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN      9283/dovecot
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN      9283/dovecot
tcp        0      0 0.0.0.0:5355            0.0.0.0:*               LISTEN      10120/systemd-resol
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      1076/smbd
tcp        0      0 0.0.0.0:587             0.0.0.0:*               LISTEN      1052/master
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN      734/vncserver-x11-c
tcp        0      0 0.0.0.0:8112            0.0.0.0:*               LISTEN      1187/python
tcp        0      0 0.0.0.0:465             0.0.0.0:*               LISTEN      1052/master
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      812/sshd
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1052/master
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      1076/smbd
tcp        0      0 0.0.0.0:58846           0.0.0.0:*               LISTEN      1179/python
tcp        0      0 0.0.0.0:61696           0.0.0.0:*               LISTEN      1179/python
tcp6       0      0 :::993                  :::*                    LISTEN      9283/dovecot
tcp6       0      0 :::995                  :::*                    LISTEN      9283/dovecot
tcp6       0      0 127.0.0.1:8005          :::*                    LISTEN      849/java
tcp6       0      0 :::3306                 :::*                    LISTEN      938/mysqld
tcp6       0      0 :::5355                 :::*                    LISTEN      10120/systemd-resol
tcp6       0      0 :::139                  :::*                    LISTEN      1076/smbd
tcp6       0      0 :::5900                 :::*                    LISTEN      734/vncserver-x11-c
tcp6       0      0 :::8080                 :::*                    LISTEN      849/java
tcp6       0      0 :::80                   :::*                    LISTEN      4326/apache2
tcp6       0      0 :::22                   :::*                    LISTEN      812/sshd
tcp6       0      0 :::443                  :::*                    LISTEN      4326/apache2
tcp6       0      0 :::445                  :::*                    LISTEN      1076/smbd
tcp6       0      0 :::61696                :::*                    LISTEN      1179/python
```


dovecot -n


```
# 2.2.27 (c0f36b0): /etc/dovecot/dovecot.conf
# Pigeonhole version 0.4.16 (fed8554)
# OS: Linux 4.19.66-v7+ armv7l Debian 9.11 ext4
auth_mechanisms = plain login
log_path = /var/log/dovecot.log
mail_location = maildir:/data/mail/vhosts/%d/%n
namespace {
  inbox = yes
  location =
  mailbox {
    special_use = \Drafts
    name = Drafts
  }
  mailbox {
    special_use = \Junk
    name = Junk
  }
  mailbox {
    special_use = \Sent
    name = Sent
  }
  mailbox {
    special_use = \Sent
    name = Sent Messages
  }
  mailbox {
    special_use = \Trash
    name = Trash
  }
  prefix =
  name = inbox
}
passdb {
  args = /etc/dovecot/dovecot-sql.conf.ext
  driver = sql
}
postmaster_address = %d
protocols = " imap lmtp pop3"
service replication-notify-fifo {
  name = aggregator
}
service anvil-auth-penalty {
  name = anvil
}
service auth-worker {
  user = vmail
  name = auth-worker
}
service {
  unix_listener {
    group = postfix
    mode = 0666
    user = postfix
    path = /var/spool/postfix/private/auth
  }
  unix_listener {
    mode = 0600
    user = vmail
    path = auth-userdb
  }
  user = dovecot
  name = auth
}
service config {
  name = config
}
service dict-async {
  name = dict-async
}
service dict {
  name = dict
}
service login/proxy-notify {
  name = director
}
service dns-client {
  name = dns_client
}
service doveadm-server {
  name = doveadm
}
service imap-hibernate {
  name = imap-hibernate
}
service {
  inet_listener {
    port = 0
    name = imap
  }
  name = imap-login
}
service imap-urlauth {
  name = imap-urlauth-login
}
service imap-urlauth-worker {
  name = imap-urlauth-worker
}
service token-login/imap-urlauth {
  name = imap-urlauth
}
service imap-master {
  name = imap
}
service indexer-worker {
  name = indexer-worker
}
service indexer {
  name = indexer
}
service ipc {
  name = ipc
}
service {
  unix_listener {
    group = postfix
    mode = 0600
    user = postfix
    path = /var/spool/postfix/private/dovecot-lmtp
  }
  name = lmtp
}
service log-errors {
  name = log
}
service {
  inet_listener {
    port = 0
    name = pop3
  }
  name = pop3-login
}
service login/pop3 {
  name = pop3
}
service replicator-doveadm {
  name = replicator
}
service login/ssl-params {
  name = ssl-params
}
service stats-mail {
  name = stats
}
ssl = required
ssl_cert = </etc/letsencrypt/live/example.com/fullchain.pem
ssl_key =  # hidden, use -P to show it
userdb {
  args = uid=vmail gid=vmail home=/data/mail/vhosts/%d/%n
  driver = static
}
protocol lmtp {
  service replication-notify-fifo {
    name = aggregator
  }
  service anvil-auth-penalty {
    name = anvil
  }
  service auth-worker {
    name = auth-worker
  }
  service auth-client {
    name = auth
  }
  service config {
    name = config
  }
  service dict-async {
    name = dict-async
  }
  service dict {
    name = dict
  }
  service login/proxy-notify {
    name = director
  }
  service dns-client {
    name = dns_client
  }
  service doveadm-server {
    name = doveadm
  }
  service imap-hibernate {
    name = imap-hibernate
  }
  service imap {
    name = imap-login
  }
  service imap-urlauth {
    name = imap-urlauth-login
  }
  service imap-urlauth-worker {
    name = imap-urlauth-worker
  }
  service token-login/imap-urlauth {
    name = imap-urlauth
  }
  service imap-master {
    name = imap
  }
  service indexer-worker {
    name = indexer-worker
  }
  service indexer {
    name = indexer
  }
  service ipc {
    name = ipc
  }
  service lmtp {
    name = lmtp
  }
  service log-errors {
    name = log
  }
  service pop3 {
    name = pop3-login
  }
  service login/pop3 {
    name = pop3
  }
  service replicator-doveadm {
    name = replicator
  }
  service login/ssl-params {
    name = ssl-params
  }
  service stats-mail {
    name = stats
  }
}
protocol lda {
  service replication-notify-fifo {
    name = aggregator
  }
  service anvil-auth-penalty {
    name = anvil
  }
  service auth-worker {
    name = auth-worker
  }
  service auth-client {
    name = auth
  }
  service config {
    name = config
  }
  service dict-async {
    name = dict-async
  }
  service dict {
    name = dict
  }
  service login/proxy-notify {
    name = director
  }
  service dns-client {
    name = dns_client
  }
  service doveadm-server {
    name = doveadm
  }
  service imap-hibernate {
    name = imap-hibernate
  }
  service imap {
    name = imap-login
  }
  service imap-urlauth {
    name = imap-urlauth-login
  }
  service imap-urlauth-worker {
    name = imap-urlauth-worker
  }
  service token-login/imap-urlauth {
    name = imap-urlauth
  }
  service imap-master {
    name = imap
  }
  service indexer-worker {
    name = indexer-worker
  }
  service indexer {
    name = indexer
  }
  service ipc {
    name = ipc
  }
  service lmtp {
    name = lmtp
  }
  service log-errors {
    name = log
  }
  service pop3 {
    name = pop3-login
  }
  service login/pop3 {
    name = pop3
  }
  service replicator-doveadm {
    name = replicator
  }
  service login/ssl-params {
    name = ssl-params
  }
  service stats-mail {
    name = stats
  }
}
protocol imap {
  service replication-notify-fifo {
    name = aggregator
  }
  service anvil-auth-penalty {
    name = anvil
  }
  service auth-worker {
    name = auth-worker
  }
  service auth-client {
    name = auth
  }
  service config {
    name = config
  }
  service dict-async {
    name = dict-async
  }
  service dict {
    name = dict
  }
  service login/proxy-notify {
    name = director
  }
  service dns-client {
    name = dns_client
  }
  service doveadm-server {
    name = doveadm
  }
  service imap-hibernate {
    name = imap-hibernate
  }
  service imap {
    name = imap-login
  }
  service imap-urlauth {
    name = imap-urlauth-login
  }
  service imap-urlauth-worker {
    name = imap-urlauth-worker
  }
  service token-login/imap-urlauth {
    name = imap-urlauth
  }
  service imap-master {
    name = imap
  }
  service indexer-worker {
    name = indexer-worker
  }
  service indexer {
    name = indexer
  }
  service ipc {
    name = ipc
  }
  service lmtp {
    name = lmtp
  }
  service log-errors {
    name = log
  }
  service pop3 {
    name = pop3-login
  }
  service login/pop3 {
    name = pop3
  }
  service replicator-doveadm {
    name = replicator
  }
  service login/ssl-params {
    name = ssl-params
  }
  service stats-mail {
    name = stats
  }
}
protocol pop3 {
  service replication-notify-fifo {
    name = aggregator
  }
  service anvil-auth-penalty {
    name = anvil
  }
  service auth-worker {
    name = auth-worker
  }
  service auth-client {
    name = auth
  }
  service config {
    name = config
  }
  service dict-async {
    name = dict-async
  }
  service dict {
    name = dict
  }
  service login/proxy-notify {
    name = director
  }
  service dns-client {
    name = dns_client
  }
  service doveadm-server {
    name = doveadm
  }
  service imap-hibernate {
    name = imap-hibernate
  }
  service imap {
    name = imap-login
  }
  service imap-urlauth {
    name = imap-urlauth-login
  }
  service imap-urlauth-worker {
    name = imap-urlauth-worker
  }
  service token-login/imap-urlauth {
    name = imap-urlauth
  }
  service imap-master {
    name = imap
  }
  service indexer-worker {
    name = indexer-worker
  }
  service indexer {
    name = indexer
  }
  service ipc {
    name = ipc
  }
  service lmtp {
    name = lmtp
  }
  service log-errors {
    name = log
  }
  service pop3 {
    name = pop3-login
  }
  service login/pop3 {
    name = pop3
  }
  service replicator-doveadm {
    name = replicator
  }
  service login/ssl-params {
    name = ssl-params
  }
  service stats-mail {
    name = stats
  }

```




Postfix master.cf:
```
#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master" or
# on-line: [http://www.postfix.org/master.5.html](http://www.postfix.org/master.5.html)).
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (no)    (never) (100)
# ==========================================================================
smtp       inet  n       -       n       -       -       smtpd
#smtp      inet  n       -       y       -       1       postscreen
#smtpd     pass  -       -       y       -       -       smtpd
#dnsblog   unix  -       -       y       -       0       dnsblog
#tlsproxy  unix  -       -       y       -       0       tlsproxy
submission inet  n       -       n       -       -       smtpd
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
smtps     inet  n       -       y       -       -       smtpd
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
#628       inet  n       -       y       -       -       qmqpd
pickup    unix  n       -       y       60      1       pickup
cleanup   unix  n       -       y       -       0       cleanup
qmgr      unix  n       -       n       300     1       qmgr
#qmgr     unix  n       -       n       300     1       oqmgr
tlsmgr    unix  -       -       y       1000?   1       tlsmgr
rewrite   unix  -       -       y       -       -       trivial-rewrite
bounce    unix  -       -       y       -       0       bounce
defer     unix  -       -       y       -       0       bounce
trace     unix  -       -       y       -       0       bounce
verify    unix  -       -       y       -       1       verify
flush     unix  n       -       y       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       y       -       -       smtp
relay     unix  -       -       y       -       -       smtp
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       y       -       -       showq
error     unix  -       -       y       -       -       error
retry     unix  -       -       y       -       -       error
discard   unix  -       -       y       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       y       -       -       lmtp
anvil     unix  -       -       y       -       1       anvil
scache    unix  -       -       y       -       1       scache
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
scalemail-backend unix  -       n       n       -       2       pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}
```


I hope this is enough information for you to be able to help me, if it isn't, please let me know and I'll post more.

---

### Post by darkod on 2019-11-19
When you receive the non-delivery report that the external message couldn't be sent, does it offer some error code etc? That might help you more than looking at the config files. I would start there.

Also since you mentioned gmail, it seems you are going through them, right? Could they have implemented/changed something that broke your current functionality?

Also, did you search your public IP to see whether it was somehow blacklisted on the main blacklists?

---

### Post by TheFu on 2019-11-19
Also, many ISPs on residential connections will block port 25/tcp, so test if a connection is possible by telneting from an outside IP to your public IP on port 25/tcp.  The ehlo should include your hostname.

OTOH, if only gmail in/out is the intention, then postfix is overkill. There are single-email address solutions that are less complex.

And please don't open all the ports to a raspberry pi.  Only the exact, specific ports that need to be opened and only for the exact, specific, clients which need access.  

I don't use pop3 ever since imap became available.  All clients see the same message store that way.

Rather than the raw config file, the output from **postconf -n** would be helpful.

---

### Post by jelletje18 on 2019-11-20
> **darkod said:**
> When you receive the non-delivery report that the external message couldn't be sent, does it offer some error code etc? That might help you more than looking at the config files. I would start there.

Also since you mentioned gmail, it seems you are going through them, right? Could they have implemented/changed something that broke your current functionality?

Also, did you search your public IP to see whether it was somehow blacklisted on the main blacklists?
[FONT=arial]Thank you both for your quick response! This is the error I'm receiving:
```
11/19/2019 5:14:09 PM - Server at VE1EUR03HT058.eop-EUR03.prod.protection.outlook.com returned '550 5.4.312 Message expired, DNS query failed(ErrorRetry)'
11/19/2019 5:08:35 PM - Server at example.com (0.0.0.0) returned '450 4.4.312 DNS query failed [Message=ErrorRetry] [LastAttemptedServerName=example.com] [AM5EUR03FT022.eop-EUR03.prod.protection.outlook.com](ErrorRetry)'
```
But as far as I can see my DNS is correct, right? [https://mxtoolbox.com/SuperTool.aspx?action=mx%3ajellebuitenhuis.nl&run=toolpage](https://mxtoolbox.com/SuperTool.aspx?action=mx%3ajellebuitenhuis.nl&run=toolpage)

I am going through my ISP's SMTP server. Gmail was just an example, I could have also used POP3 in Outlook or any other mail client. The issues is that the email does not arrive at my Pi at all, nothing happens in the logs.
I've checked several websites, but I'm not blacklisted anywhere I could find.

> **TheFu said:**
> Also, many ISPs on residential connections will block port 25/tcp, so test if a connection is possible by telneting from an outside IP to your public IP on port 25/tcp. The ehlo should include your hostname.

OTOH, if only gmail in/out is the intention, then postfix is overkill. There are single-email address solutions that are less complex.

And please don't open all the ports to a raspberry pi. Only the exact, specific ports that need to be opened and only for the exact, specific, clients which need access. 

I don't use pop3 ever since imap became available. All clients see the same message store that way.

Rather than the raw config file, the output from **postconf -n** would be helpful.

Luckily I have a very good ISP who does not block any ports. I can telnet into them all and they are all opened. 
Gmail was only an example to be able to receive email in one place.
I know not to open all ports, that was a test to see if ports where the issues, they weren't, it didn't change anything.

Here is postconf -n:
```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
inet_interfaces = all
inet_protocols = ipv4
mailbox_size_limit = 0
mydestination = localhost
myhostname = mail.jellebuitenhuis.nl
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost = [smtp.tweak.nl]:587
smtpd_banner = $myhostname ESMTP $mail_name (Raspbian)
smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_unauth_destination,
smtpd_sasl_auth_enable = yes
smtpd_sasl_path = private/auth
smtpd_sasl_type = dovecot
smtpd_tls_auth_only = yes
smtpd_tls_cert_file = /etc/letsencrypt/live/jellebuitenhuis.nl/fullchain.pem
smtpd_tls_key_file = /etc/letsencrypt/live/jellebuitenhuis.nl/privkey.pem
smtpd_use_tls = yes
virtual_alias_maps = mysql:/etc/postfix/mysql-virtual-alias-maps.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual-mailbox-domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual-mailbox-maps.cf
virtual_transport = lmtp:unix:private/dovecot-lmtp

```[/FONT]

---

### Post by darkod on 2019-11-20
The message about the dns query is quite clear.

Also, if the below is your domain, then the dns is not right. You put mail. instead of mail.jellebuitenhuis.nl.

```
darko@nuc6:~$ dig mx jellebuitenhuis.nl

; <<>> DiG 9.11.3-1ubuntu1.10-Ubuntu <<>> mx jellebuitenhuis.nl
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 63639
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;jellebuitenhuis.nl.        IN    MX


;; ANSWER SECTION:
jellebuitenhuis.nl.    299    IN    MX    10 mail.


;; Query time: 67 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Wed Nov 20 13:25:29 CET 2019
;; MSG SIZE  rcvd: 67
```

You should modify the MX to point to the full FQDN, for example mail.jellebuitenhuis.nl and not just mail.

After that it should be OK because you seem to have a correct A record for mail:
```
darko@nuc6:~$ dig mail.jellebuitenhuis.nl


; <<>> DiG 9.11.3-1ubuntu1.10-Ubuntu <<>> mail.jellebuitenhuis.nl
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 38374
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;mail.jellebuitenhuis.nl.    IN    A


;; ANSWER SECTION:
mail.jellebuitenhuis.nl. 299    IN    A    84.245.9.242


;; Query time: 65 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Wed Nov 20 13:25:45 CET 2019
;; MSG SIZE  rcvd: 68
```

---

### Post by jelletje18 on 2019-11-20
That was the problem, thank you so much!
The supportdesk at my provider told me to change it to 'mail.', but it seems that is wrong.

---


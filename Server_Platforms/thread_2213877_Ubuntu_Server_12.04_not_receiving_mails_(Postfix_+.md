---
title: "Ubuntu Server 12.04 not receiving mails (Postfix + Dovecot  + Mysql)"
date: 2014-03-29
forum: Server Platforms
---

### Post by Br_Attila on 2014-03-29
Ok guys I need some help. My server does not receive any mails from outside.

I can send mails from localhost to outside ... [EMAIL="mymail@myserver.com"]mymail@myserver.com[/EMAIL] to [EMAIL="something@gmail.com"]something@gmail.com[/EMAIL]
I can send mails from local to local .. [EMAIL="mymail1@myserver.com"]mymail1@myserver.com[/EMAIL] to [EMAIL="mymail2@myserver.com"]mymail2@myserver.com[/EMAIL]
I can receive mails from local ... but I can't from outside.

Here is my postconf -n

```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
inet_interfaces = all
mailbox_size_limit = 0
mydestination = localhost
myhostname = mail.mydomain.eu
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost = smtp.myisp.xxx
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_path = private/auth
smtpd_sasl_type = dovecot
smtpd_tls_auth_only = yes
smtpd_tls_cert_file = /etc/ssl/certs/dovecot.pem
smtpd_tls_key_file = /etc/ssl/private/dovecot.pem
smtpd_use_tls = yes
virtual_alias_maps = mysql:/etc/postfix/mysql-virtual-alias-maps.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual-mailbox-domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual-mailbox-maps.cf
virtual_transport = lmtp:unix:private/dovecot-lmtp


```

iptables -L

```


Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


```

mail.log & mail.err is empty

MX is ok!

telnet myserver.xxx 587 OK
telnet myserver.xxx 143 OK

telnet myserver.xxx 993 

```
telnet mydomain 993
Trying xxx.xxx.xxx.xxx...
Connected to mydomain.
Escape character is '^]'.


```

dovecot -n

```
# 2.0.19: /etc/dovecot/dovecot.conf
# OS: Linux 3.5.0-47-generic x86_64 Ubuntu 12.04.4 LTS ext4
auth_mechanisms = login
auth_verbose = yes
mail_location = maildir:/var/mail/vhosts/%d/%n
mail_privileged_group = vmail
passdb {
  args = /etc/dovecot/dovecot-sql.conf.ext
  driver = sql
}
postmaster_address = attila@mydomain
protocols = imap pop3 lmtp
service auth-worker {
  user = vmail
}
service auth {
  unix_listener /var/spool/postfix/private/auth {
    group = postfix
    mode = 0666
    user = postfix
  }
  unix_listener auth-userdb {
    mode = 0600
    user = vmail
  }
  user = dovecot
}
service lmtp {
  unix_listener /var/spool/postfix/private/dovecot-lmtp {
    group = postfix
    mode = 0600
    user = postfix
  }
}
ssl_cert = </etc/ssl/certs/dovecot.pem
ssl_key = </etc/ssl/private/dovecot.pem
userdb {
  args = uid=vmail gid=vmail home=/var/mail/vhosts/%d/%n
  driver = static
}


```

 cat /etc/postfix/master.cf

```

#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd -o content_filter=spamassassin
#smtp      inet  n       -       -       -       1       postscreen
#smtpd     pass  -       -       -       -       -       smtpd
#dnsblog   unix  -       -       -       -       0       dnsblog
#tlsproxy  unix  -       -       -       -       0       tlsproxy
submission inet n       -       -       -       -       smtpd
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

spamassassin unix -     n       n       -       -       pipe
        user=spamd argv=/usr/bin/spamc -f -e
        /usr/sbin/sendmail -oi -f ${sender} ${recipient}



```

UPDATE : for example if I send a mail from my gmail acc to my server, the connection does not even appears in logs - no non-delivery report

dig 

```

; <<>> DiG 9.8.1-P1 <<>> mydomain mx
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 56653
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 4, ADDITIONAL: 5

;; QUESTION SECTION:
;mydomain.                    IN      MX

;; ANSWER SECTION:
mydomain.             3600    IN      MX      10 mail.mydomain.

;; AUTHORITY SECTION:
mydomain.             39583   IN      NS      ns3.myns.
mydomain.             39583   IN      NS      ns4.myns.
mydomain.             39583   IN      NS      ns1.myns.
mydomain.             39583   IN      NS      ns2.myns.

;; ADDITIONAL SECTION:
ns1.myns.         36507   IN      A       
ns1.myns.         40640   IN      AAAA    
ns2.myns.         36507   IN      A       
ns3.myns.         36507   IN      A       
ns4.myns.         36507   IN      A       



```

---

### Post by TheFu on 2014-03-29
Ouch.  Is there a hw-firewall/router that needs port 25 forwarded?
Does your ISP allow port 25/tcp inbound? That is the port that MTAs use.
The other ports are just for client connections.

---

### Post by nerdtron on 2014-03-29
Why are the logs empty? There should be logs is you send emails from local to outside and send mails from local to local. You need to fix this too. Logs are important for a mail server.
How did you make sure that the MX record for you domain is setup correctly? Have you checked your domain in mxtoolbox.com?
This is why we need to see the logs, are mails reaching the mail server and get rejected, or the emails never arrive at all?

---

### Post by SeijiSensei on 2014-03-30
> mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128

That only allows traffic from localhost.  You need to add your local subnet, e.g, 192.168.1.0/24, to this list.  Then message traffic passing through your router will be accepted by Postfix.

Read these documents for details: 
[http://www.postfix.org/postconf.5.html#smtpd_relay_restrictions](http://www.postfix.org/postconf.5.html#smtpd_relay_restrictions)
[http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html)

From the first of these:
> By default, the Postfix SMTP server accepts:
[list]
[*]Mail from clients whose IP address matches $mynetworks, or:
[*]Mail to remote destinations that match $relay_domains, except for addresses that contain sender-specified routing (user@elsewhere@domain), or:
[*]Mail to local destinations that match $inet_interfaces or $proxy_interfaces, $mydestination, $virtual_alias_domains, or $virtual_mailbox_domains. 
[/list]
If you ran those telnet tests from the server itself, that can be deceptive as they may be permitted by the localhost rule.  You can test from another machine on your network by connecting to the server's network IP address, but ultimately you should test from a machine outside your network entirely.

---

### Post by Br_Attila on 2014-04-03
MX records are ok,and port forwarding also is ok.but the port 25 is blocked :(
that's the problem. I don't really undestand how it's worked until now ...
logs are empty - I mean no error.

---

### Post by Catalys on 2014-04-03
Add to your master.cf:
 
```
26     inet  n       -       -       -       -       smtpd -o content_filter=spamassassin
```


So you can use port 26 for SMTP :).

---

### Post by TheFu on 2014-04-03
> **Br_Attila said:**
> MX records are ok,and port forwarding also is ok.but the port 25 is blocked :(
that's the problem. I don't really undestand how it's worked until now ...
logs are empty - I mean no error.

Call your ISP and complain. If it is a non-residential connection, they should help. If it is for a house, there are other options ... like a [cheap email gateway]("http://www.dyndns.com/support/kb/cat_relay.html") for $40/yr or get a VPS and run your own email gateway.  The key is to have email NOT use port 25 on your home system.

Setting up your email server to listen on a different port doesn't tell the world about it. THAT is the issue that can only be solved with an external system listening for SMTP on port 25. Period.

---

### Post by Catalys on 2014-04-03
> **TheFu said:**
> Call your ISP and complain. If it is a non-residential connection, they should help. If it is for a house, there are other options ... like a [cheap email gateway]("http://www.dyndns.com/support/kb/cat_relay.html") for $40/yr or get a VPS and run your own email gateway.  The key is to have email NOT use port 25 on your home system.

Setting up your email server to listen on a different port doesn't tell the world about it. THAT is the issue that can only be solved with an external system listening for SMTP on port 25. Period.


Agree, you should indeed look for a VPS to handle this. If you really need it, you can still add the line in the master.cf I have send before. Note: Adding the line, will open both 25 and 26, so it's not like 25 will close.

---

### Post by TheFu on 2014-04-03
OR ......

Let the router do the port translation and leave port 25 alone so that other machines inside your network don't get confused.  We have these fancy routers with all sorts of capabilities - why not use them?

I've been doing this with ssh for years.

---


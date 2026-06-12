---
title: "Postix Setup Help"
date: 2008-08-07
forum: Server Platforms
---

### Post by njschwartz on 2008-08-07
Hi all!  I am pretty new to Ubuntu although I have tried a few other distros in the past like gentoo, but only just to see what is was like.  I have recently installed a LAMP server and got it setup to host my website and act as a DNS without any major issues.  I then thought to myself that it would be cool to host my own mail server.  Unfortunately, despite my best efforts I cannot make it work.  I have been following the guide at [http://flurdy.com/docs/postfix/#install](http://flurdy.com/docs/postfix/#install).  I have to admit I don't really know what I am doing so please be patient with me.  So the issue I am having at the moment, I think anyway, is with the postfix setup.  I got to the point in the guide where it stated it should work and to try to test it.  When I do telnet localhost 25 however I get no response from postfix.  I am not really sure where I am going astray.  Below are my master.cf and main.cf files.  Any suggestions would be greatly appreciated!

My /etc/postfix/main.cf file:

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

myhostname = nateserver.nateandstephie.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
#mydestination = nateandstephie.com, Nateserver, localhost.localdomain, localhost
mydestination =
relayhost =
mynetworks = 127.0.0.0/8 192.168.11.0/24
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks_style = host
local_recipient_maps =

# how long if undelivered before sending warning update to sender
delay_warning_time = 4h
# will it be a permanent error or temporary
unknown_local_recipient_reject_code = 450
# how long to keep message on queue before return as failed.
# some have 3 days, I have 16 days as I am backup server for some people
# whom go on holiday with their server switched off.
maximal_queue_lifetime = 7d
# max and min time in seconds between retries if connection failed
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
# how long to wait when servers connect before receiving rest of data
smtp_helo_timeout = 60s
# how many address can be used in one message.
# effective stopper to mass spammers, accidental copy in whole address list
# but may restrict intentional mail shots.
smtpd_recipient_limit = 16
# how many error before back off.
smtpd_soft_error_limit = 3
# how many max errors before blocking it.
smtpd_hard_error_limit = 12

# Requirements for the HELO statement
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname,
        reject_invalid_hostname, permit
# Requirements for the sender details
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender,
        reject_unknown_sender_domain, reject_unauth_pipelining, permit
# Requirements for the connecting server
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org,
        reject_rbl_client blackholes.easynet.nl,
        reject_rbl_client dnsbl.njabl.org
# Requirement for the recipient address
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination

# require proper helo at connections
smtpd_helo_required = yes
# waste spammers time before rejecting them
smtpd_delay_reject = yes
disable_vrfy_command = yes

# not sure of the difference of the next two
# but they are needed for local aliasing
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
# this specifies where the virtual mailbox folders will be located

virtual_mailbox_base = /var/spool/mail/virtual
# this is for the mailbox location for each user
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
# and their user id
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf
# and group id
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
# and this is for aliases
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
# and this is for domain lookups
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
# this is how to connect to the domains (all virtual, but the option is there)
# not used yet
# transport_maps = mysql:/etc/postfix/mysql_transport.cf
inet_protocols = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
```

My /etc/postfix/master.cf file:

```
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       n       -       -       smtpd
#submission inet n       -       -       -       -       smtpd
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       -       -       -       smtpd
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628      inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
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
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       -       -       -       smtp
        -o smtp_fallback_relay=
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

---

### Post by windependence on 2008-08-07
First see if postfix is actually running:

```
ps -aux | grep postfix
```

-Tim

---

### Post by HermanAB on 2008-08-07
Here you go:
[http://www.citadel.org](http://www.citadel.org)
(It takes about 20 minutes to run the easy install script)

Citadel is good for tens of thousands of users and is a better solution for most people, since it is a complete solution.  

In contrast, Postfix is like Lego - to make a full system, you also need MySQL, Dovecot, Apache, Roundcube and more so it takes forever to make it all work together.

Cheers,

Herman

---

### Post by windependence on 2008-08-07
I agree with Herman. A single package like Citadel is much easier to install and configure.

You can also try [Zimbra.]("http://www.zimbra.com")

-Tim

---

### Post by hyper_ch on 2008-08-07
I'd follow this:

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p5](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p5)

---

### Post by windependence on 2008-08-07
Thanks hyper_ch. The problem I have with this is while it's a great cut and paste tutorial, I have absolutely no idea why I'm doing what I'm doing here. I don't particularly feel confident with that since I have to support it. At least the others I understand how they all work. ;)

-Tim

---

### Post by njschwartz on 2008-08-07
Thanks for the replies all.  I am considering other options like possibly citadel or maybe even Zimbra since I have read a lot of people suggesting how easy they are.  Nevertheless, I would still like to understand what I am doing wrong with postfix.  Postfix appears to be running but still not working.  Thanks again all!

This is the output of ps aux | grep postfix: 

```
root     11353  0.0  0.2  36684  2152 ?        Ss   06:15   0:00 /usr/lib/postfix/master
postfix  11356  0.0  0.2  38784  2092 ?        S    06:15   0:00 qmgr -l -t fifo -u
postfix  12716  0.0  0.1  38740  2052 ?        S    16:15   0:00 pickup -l -t fifo -u -c
1000     12812  0.0  0.0   5164   832 pts/0    R+   17:08   0:00 grep postfix

```

---

### Post by hyper_ch on 2008-08-08
had a look at that howto?

---


---
title: "Postfix, can't receive email from outside"
date: 2013-09-22
forum: Server Platforms
---

### Post by trademark3 on 2013-09-22
Hello,

I'm stuck for hours now on a Postfix configuration problem (well, I guess the problem comes from it). 
What I can do:

[LIST]
[*]Send mail to outside 
[*]Receive mail from local address (even if the mail is sent from outside) 
[/LIST]

What I can't:
[LIST]
[*]Receive mail from outside 
[/LIST]

I'm not sure what could be interesting to post here so I'll begin with the postfix main.cf, please tell me what you need. I renamed my domain flower.net and the server address server.prodiver.net

```
unknown_address_reject_code = 450
unknown_client_reject_code = 450
unknown_hostname_reject_code = 450
smtp-filter_destination_concurrency_limit = 2
lmtp-filter_destination_concurrency_limit = 2
parent_domain_matches_subdomains =
inet_interfaces = all
mynetworks_style = host
mynetworks = 127.0.0.0/8
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases

# this specifies where the virtual mailbox folders will be located 
virtual_mailbox_base = /var/spool/mail/virtual
# this is for the mailbox location for each user 
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
# and this is for aliases 
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
# and this is for domain lookups 
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
# this is how to connect to the domains (all virtual, but the option is there) 
# not used yet 
# transport_maps = mysql:/etc/postfix/mysql_transport.cf

virtual_uid_maps = static:5000
virtual_gid_maps = static:5000

mydomain = flower.net
myorigin = $mydomain
myhostname = server.provider.net
# We use virtual domain so mydestination and local_recipient_map need to be empty.
mydestination =
local_recipient_maps =
relay_domains = $mydestination
home_mailbox = Maildir/
mailbox_command =

masquerade_exceptions = root
masquerade_domains = mail.flower.net
mail_spool_directory = /var/spool/mail
recipient_delimiter = +
local_destination_concurrency_limit = 2
default_destination_concurrency_limit = 10
smtpd_banner = $myhostname ESMTP $mail_name
mailbox_delivery_lock = fcntl
debug_peer_level = 1
relay_recipient_maps = hash:/etc/postfix/relay_recipients

# Requirements for the HELO statement 
smtpd_helo_restrictions = permit_mynetworks
# Requirements for the sender details 
# Add permit_sasl_authenticated to you existing smtpd_sender_restrictions
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
# Requirements for the connecting server 
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl
# Requirement for the recipient address 
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:10023, permit
smtpd_data_restrictions = reject_unauth_pipelining

# require proper helo at connections 
smtpd_helo_required = yes
# waste spammers time before rejecting them 
smtpd_delay_reject = yes
disable_vrfy_command = yes

# how long if undelivered before sending warning update to sender 
delay_warning_time = 4h
# will it be a permanent error or temporary 
unknown_local_recipient_reject_code = 450

queue_directory = /var/spool/postfix

# how long to keep message on queue before return as failed. 
# some have 3 days, I have 16 days as I am backup server for some people 
# whom go on holiday with their server switched off. 
maximal_queue_lifetime = 2d
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

queue_run_delay = 500
bounce_queue_lifetime = 8h
smtpd_helo_required = yes
line_length_limit = 2048
bounce_size_limit = 50000
notify_classes= resource,software
soft_bounce=no
message_size_limit = 10000000
queue_minfree = 0
default_destination_recipient_limit = 20
command_time_limit = 240

maps_rbl_reject_code = 550
maps_rbl_domains =
        relays.ordb.org,
        relays.visi.com,
        ipwhos.rfc-ignorant.org,
        list.dsbl.org,
        bl.spamcop.net,
        opm.blitzed.org,
        list.dsbl.org,
        sbl.spamhaus.org,
        blackholes.easynet.nl,
        cbl.abuseat.org

mailbox_size_limit = 5500000000
inet_protocols = all

# SASL
smtpd_sasl_auth_enable = yes
# If your potential clients use Outlook Express or other older clients 
# this needs to be set to yes 
broken_sasl_auth_clients = no
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =

# TLS parameters
# smtp_use_tls = no 
smtp_tls_security_level = may
# smtpd_use_tls=yes 
smtpd_tls_security_level = may
# smtpd_tls_auth_only = no 
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
# smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache 
# smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache 
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt

```

Thank you.

---

### Post by SeijiSensei on 2013-09-23
If you are using a residential connection, your ISP has probably blocked inbound SMTP connections on port 25.  Since running servers is typically forbidden by the Terms of Service on residential Internet accounts, your ISP may or may not be helpful in resolving this issue.

---

### Post by trademark3 on 2013-09-23
Thank you for your response, badly I'm not using the port 25. I'm using the port 587 for SMTP and 143 for IMAP. I forgot to say that I had "secure" this mail server.

Any other idea?

---

### Post by MeneM on 2013-09-24
Have you configured postfix to use 587 for ssl/smtp traffic?

(Postfix, does not do Imap b.t.w. You will need other software to provide that sort of functionality, This is a nice starting place: [https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto))

---

### Post by trademark3 on 2013-09-24
Yes it's configured, for info, I post my master.cf.

I'm using courier for the IMAP side.

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
# smtp      inet  n       -       -       -       -       smtpd

submission inet n       -       -       -       -       smtpd
  -o smtpd_sasl_auth_enable=yes
# if you do not want to restrict it encryption only, comment out next line
  -o smtpd_tls_auth_only=yes
# -o smtpd_tls_security_level=encrypt
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject_unauth_destination,reject
  -o smtpd_sasl_security_options=noanonymous,noplaintext
  -o smtpd_sasl_tls_security_options=noanonymous
# -o milter_macro_daemon_name=ORIGINATING<
smtps inet n - - - - smtpd
  -o smtpd_tls_wrappermode=yes
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_tls_auth_only=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
  -o smtpd_sasl_security_options=noanonymous,noplaintext
  -o smtpd_sasl_tls_security_options=noanonymous
# -o milter_macro_daemon_name=ORIGINATING
#628       inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
#       -o content_filter= 
#       -o receive_override_options=no_header_body_checks
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

Thanks.

---

### Post by SeijiSensei on 2013-09-24
Remote mail servers will be using port 25 to send you mail, not 587.  If you're not listening on port 25, you won't get inbound mail.

---

### Post by trademark3 on 2013-09-24
Hmm ok, so I uncommented the line > # smtp      inet  n       -       -       -       -       smtpd in the master.cf.

I'm not sure what I need to do to accept inbound mail on port 25 (apart uncommenting the quoted line).
Obviously this is not enough because I still don't receive mails.

---

### Post by moonpup on 2013-09-24
Assuming port 25 TCP inbound to your server is not blocked, then it could be a DNS issue. Do you have an MX (mail exchanger) record setup for your server? If there is no MX record for your server and domain, then other email servers on the internet can't find you. Also, email is very strict and requires matching forward and reverse records for the host.

---

### Post by trademark3 on 2013-09-24
My DNS file is (with IP and domain replaced):

> * 10800 IN A 42.42.42.42
@ 10800 IN A 42.42.42.42
mail 10800 IN A 42.42.42.42
flower.net 10800 IN MX 10 mail.flower.net.

By the way what could block my port 25? My firewall authorizes it, not sure what else I need to set.

---

### Post by SeijiSensei on 2013-09-24
```

Seiji@ghostworld:~$ host mail.flower.net
mail.flower.net is an alias for flower.net.
flower.net has address 66.197.19.22
flower.net mail is handled by 10 flower.net.

Seiji@ghostworld:~$ telnet mail.flower.net 25
Trying 66.197.19.22...
[times out]

Seiji@ghostworld:~$ sudo nmap -sT mail.flower.net

Starting Nmap 6.00 ( http://nmap.org ) at 2013-09-24 18:20 EDT
Nmap scan report for mail.flower.net (66.197.19.22)
Host is up (0.036s latency).
rDNS record for 66.197.19.22: host00854.ve.carpathiahost.net
Not shown: 992 closed ports
PORT     STATE    SERVICE
21/tcp   open     ftp
22/tcp   open     ssh
25/tcp   filtered smtp
80/tcp   open     http
110/tcp  open     pop3
995/tcp  open     pop3s
1720/tcp filtered H.323/Q.931
3306/tcp open     mysql

Nmap done: 1 IP address (1 host up) scanned in 1.99 seconds

```

Something is filtering inbound port 25; my guess is that it is your ISP.  I'm actually more concerned that I can see your MySQL server from a remote location.  Is there some reason for that?  If you are running MySQL only to support the webserver, revert back to the default my.cnf which binds MySQL exclusively to localhost.  If other remote machines need to connect to the MySQL port, either add specific iptables rules enabling their IP addresses and blocking all others, or set up VPN tunnels between the clients and server.  OpenVPN with a [shared static key]("http://openvpn.net/static.html") is my choice for point-to-point tunnels.

---

### Post by moonpup on 2013-09-24
Did you make any changes on your end, or perhaps call your ISP? It appears to be working now...

nmap mail.flower.net

Starting Nmap 6.25 ( [http://nmap.org](http://nmap.org) ) at 2013-09-24 21:10 EDT
Nmap scan report for mail.flower.net (66.197.19.22)
Host is up (0.037s latency).
rDNS record for 66.197.19.22: host00854.ve.carpathiahost.net
Not shown: 989 closed ports
PORT     STATE    SERVICE
21/tcp   open     ftp
22/tcp   open     ssh
25/tcp   open     smtp
80/tcp   open     http
110/tcp  open     pop3
135/tcp  filtered msrpc
139/tcp  filtered netbios-ssn
445/tcp  filtered microsoft-ds
995/tcp  open     pop3s
3306/tcp open     mysql
4444/tcp filtered krb524

Nmap done: 1 IP address (1 host up) scanned in 3.81 seconds

telnet mail.flower.net 25
Trying 66.197.19.22...
Connected to flower.net.
Escape character is '^]'.
220 host00854.ve.carpathiahost.net ESMTP Sendmail 8.12.11.20060308/8.12.11; Tue, 24 Sep 2013 21:10:51 -0400
^]
telnet> quit
Connection closed.

---

### Post by trademark3 on 2013-09-25
Hmm, actually flower.net is just a place-holder for my real domain name. I didn't write it to avoid hacking if my server was poorly configured. However it's amusing that flower.net resolved the problem, haha.
I sent a mail to you both with the real domain name, if anyone want to know, just ask by mail please.

Here the lines (again masked with some place-holders):

> $ sudo nmap -sT mail.hyc.io

Starting Nmap 6.00 ( [http://nmap.org](http://nmap.org) ) at 2013-09-25 07:07 CEST
Nmap scan report for mail.masked_domain.net (42.42.42.42)
Host is up (0.19s latency).
rDNS record for 42.42.42.42: server.provider.net
Not shown: 986 filtered ports
PORT     STATE  SERVICE
20/tcp   closed ftp-data
21/tcp   closed ftp
22/tcp   open   ssh
25/tcp   open   smtp
53/tcp   closed domain
80/tcp   open   http
110/tcp  open   pop3
143/tcp  open   imap
443/tcp  closed https
465/tcp  open   smtps
587/tcp  open   submission
993/tcp  open   imaps
995/tcp  open   pop3s
8443/tcp closed https-alt

Nmap done: 1 IP address (1 host up) scanned in 25.84 seconds


And the telnet

> $ telnet mail.masked_domain.net 25
Trying 42.42.42.42...
Connected to mail.masked_domain.net.
Escape character is '^]'.
220 server.provider.net ESMTP Postfix


I can access the server on port 25 via telnet, so it's opened. Conclusion: it should work? But it still doesn't...

---

### Post by trademark3 on 2013-09-26
Thanks to everyone, it's resolved! My DNS record was badly configured. Best config:

> * 10800 IN A 42.42.42.42
@ 10800 IN A 42.42.42.42
@ 10800 IN MX 10 mail.flower.net.

Moreover, in my main.cf, 
> smtpd_recipient_restriction = check_policy_service inet:127.0.0.1:10023
was not good since I rollbacked my spamassassin & compagnie installation... So removing this line solved the second problem.

---

### Post by mroussin51 on 2013-10-24
Perhaps your server is receiving the mail but it is going into a different directory than the default mail directory. Maybe you changed the Maildir like this:

 [B]sudo postconf -e 'home_mailbox = Maildir/'
[/B]
Try the following command: **MAIL=/home/username/Maildir/ mail** 

I assume your mail has not bounced and your server is receiving the mail.

regards,

The Rooster

I am sorry, like duh, I screwed that one up.

regards,

mroussin51

---


---
title: "setting up mail server help"
date: 2010-08-09
forum: Server Platforms
---

### Post by duceduc on 2010-08-09
I have been searching for answers and trying to get my mail server up at 100%. I used [this guide]("http://ubuntuforums.org/showthread.php?t=185913") and have finished my configuration but have a few hiccups. My issue is that I cannot receive mails from outside my domain. 

I have setup an mx record with zoneedit and is active. I do a ```
dig mx domain.com
``` and I can see my mx record.

I can *telnet localhost 25* with success. Thus,I can receive and send with this test.

**Actual Test**
My mail server can send and receive mails locally using squirrelmail just fine. However, I am not able to receive any emails from outside (gmail, yahoo, hotmail accounts). I get these errors after couple hours. ```
The recipient server did not accept our requests to connect.
Delivery to the following recipients has been delayed.

``` 

If my isp **is blocking** port 25, I would not be able to send messages out correct? I can do that with squirrelmail. 

I would show you some logs but I don't know which logs to look for. I tried mail.log when I was testing an email send from my gmail account, but I don't get any output in the log file.

At this point,  I am stomped. Need some assistance. Thanks you.

---

### Post by Bachstelze on 2010-08-09
> **duceduc said:**
> 
My mail server can send and receive mails using squirrelmail just fine.

From where?

---

### Post by duceduc on 2010-08-09
> **Bachstelze said:**
> From where?

I can send/receive emails connected to squirrelmail remotely or within my network.

---

### Post by Bachstelze on 2010-08-09
> **duceduc said:**
> I can send/receive emails connected to squirrelmail remotely or within my network.

Yes, but those emails you receive, where are they sent from?

---

### Post by duceduc on 2010-08-09
Ah. Yes. Those emails are from my contact form's websites in which I'm hosting on the same server. Sorry if I wasn't clear. 

Tunnel vision I guess :P

---

### Post by Bachstelze on 2010-08-09
Okay, so it's probably just local delivery.  Can you PM me an address on the domain so I can try to send mail to it and see what my server says?

---

### Post by duceduc on 2010-08-10
Here is the main.cf
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
myorigin = /etc/mailname

smtpd_banner = $ducsu.com ESMTP $duc (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
#smtpd_use_tls=yes
#smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
#smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.ducsu.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = ducsu.com
mydestination = 
local_recipient_maps =
relayhost = smtp.carol.jp
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128

mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

delay_warning_time = 4h
unknown_local_recipient_reject_code = 450
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
smtp_helo_timeout = 60s
smtpd_recipient_limit = 16
smtpd_soft_error_limit = 3
smtpd_hard_error_limit = 12

smtpd_helo_restrictions 	= permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_sender_restrictions	= permit_sasl_authenticated, permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_client_restrictions 	= reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
smtpd_recipient_restrictions	= reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:10023, permit 
smtpd_data_restrictions 	= reject_unauth_pipelining

smtpd_helo_required = yes
smtpd_delay_reject  = yes
disable_vrfy_command = yes

alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf

virtual_uid_maps = static:5000
virtual_gid_maps = static:5000

#Amavis-new
content_filter = amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings

#SASL
smtpd_ssl_auth_enable = yes
broken_sasl_auth_clients = no
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =

```

Here is the master.cf
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
smtp      inet  n       -       -       -       -       smtpd
   -o content_filter=spamassassin

submission inet n       -       -       -       -       smtpd
#  -o smtpd_tls_security_level=encrypt
   -o smtpd_sasl_auth_enable=yes
   -o smtpd_client_restrictions=permit_sasl_authenticated,reject_unauth_destination,reject
   -o smtpd_sasl_security_options=noanonymous,noplaintext
   -o smtpd_sasl_tls_security_options=noanonymous
#  -o milter_macro_daemon_name=ORIGINATING
smtps     inet  n       -       -       -       -       smtpd
   -o smtpd_tls_wrappermode=yes
   -o smtpd_sasl_auth_enable=yes
   -o smtpd_tls_auth_only=yes
   -o smtpd_client_restrictions=permit_sasl_authenticated,reject
   -o smtpd_sasl_security_options=noanonymous,noplaintext
   -o smtpd_sasl_tls_security_options=noanonymous
#  -o milter_macro_daemon_name=ORIGINATING
#628       inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
	-o content_filters=
	-o receive_override_options=no_header_body_checks
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
scalemail-backend unix	-	n	n	-	2	pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

amavis		unix	-	-	-	-	2	smtp
	-o smtp_data_done_timeout=1200
	-o smtp_send_xforward_command=yes
	-o disable_dns_lookups=yes
	-o max_use=20

127.0.0.1:10025	inet	n	-	-	-	-	smtpd
	-o content_filter=
	-o local_recipient_maps=
	-o relay_recipient_maps=
	-o smtpd_restriction_classes=
	-o smtpd_delay_reject=no
	-o smtpd_client_restrictions=permit_mynetworks,reject
	-o smtpd_helo_restrictions=
	-o smptd_sender_restrictions=
	-o smtpd_recipient_restrictions=permit_mynetworks,reject
	-o smtpd_data_restrictions=reject_unauth_pipelining
	-o smtpd_end_of_data_restrictions=
	-o mynetworks=127.0.0.0/8
	-o smtpd_error_sleep_time=0
	-o smtpd_soft_error_limit=1001
	-o smtpd_hard_error_limit=1000
	-o smtpd_client_connection_count_limit=0
	-o smtpd_client_connection_rate_limit=0
	-o receive_override_options=no_header_body_checks,no_unknown_recipient_checks

spamassassin	unix	-	n	n	-	-	pipe
	user=spamd argv=/usr/bin/spamc -f -e /usr/sbin/sendmail -oi -f ${sender} ${recipient}


```

---

### Post by Bachstelze on 2010-08-10
Okay so the weird banner is just because of the dollar signs you have here

```
smtpd_banner = $ducsu.com ESMTP $duc (Ubuntu)
```

Not a big deal, but any reason to have them?

---

### Post by duceduc on 2010-08-10
I solved my issue. I didn't open ports for my mail server on my router :oops:	

> **Bachstelze said:**
> Okay so the weird banner is just because of the dollar signs you have here

```
smtpd_banner = $ducsu.com ESMTP $duc (Ubuntu)
```

Not a big deal, but any reason to have them?

So that is where the banner came from when I telnet. 
No reason. 
That was the default line and I changed it to reflect my server.
Thank you.

If I may just bother you with one more issue I have with vsftpd. I started a post, but I am not getting any response. If you have the time to look at it, I'd appreciate the help.

Look at [VSFTPD thread]("http://ubuntuforums.org/showthread.php?t=518293&page=7"), postcount #64.

---


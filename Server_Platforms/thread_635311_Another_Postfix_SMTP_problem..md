---
title: "Another Postfix SMTP problem."
date: 2007-12-08
forum: Server Platforms
---

### Post by rekon on 2007-12-08
I know there are a few similar threads regarding Postfix & SMTP problems but I have sifted through them all and none of them pertain to my problem. If you know of a thread that exists that will help me resolve this issue, please point me to it! 

I am running Feisty Fawn server edition and followed Flurdy's "[How to set up a mail server on a GNU / Linux system]("http://flurdy.com/docs/postfix")"

Everything was working just great, I was able to send and recieve email for about a month straight. But now, out of the blue, I am recieving the error "postfix/qmgr[5487]: warning: connect to transport smtp: Connection refused"

I did not reboot the machine, nor did I change anything, it just suddenly started reporting this error. Also, sometimes out of the blue my /var/run/clamav and /var/log/clamav folders group gets changed from virtual to root which causes the virus scanner to fail. I still can't figure out why this is, but after I run chown -R virtual:virtual /var/run/clamav/ and /var/log/clamav it works fine.

Anyways, does anybody have any idea why my SMTP service would fail like this? All of my outbound messages are being deferred and it's getting annoying. 

Here are the contents of my main.cf and master.cf files..

master.cf
```
#

# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
	-o cleanup_service_name=pre-cleanup
#submission inet n       -       -       -       -       smtpd
#  -o smtpd_enforce_tls=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
smtps     inet  n       -       n       -       -       smtpd
	-o smtpd_tls_wrappermode=yes
	-o smtpd_sasl_auth_enable=yes
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#628      inet  n       -       -       -       -       qmqpd
587       inet  n       -       n       -       -       smtpd
	-o smtpd_enforce_tls=yes
	-o smtpd_sasl_auth_enable=yes
pickup    fifo  n       -       -       60      1       pickup
pre-cleanup unix n      -       -       -       0       cleanup
	-o virtual_alias_maps=
	-o canonical_maps=
	-o sender_canonical_maps=
	-o recipient_canonical_maps=
	-o masquerade_domains=
cleanup   unix  n       -       -       -       0       cleanup
	-o mime_header_checks=
	-o nested_header_checks=
	-o body_checks=
	-o header_checks=
amavis 	  unix  -       -       -       -       2       smtp
	-o smtp_data_done_timeout=1200
	-o smtp_send_xforward_command=yes
127.0.0.1:10025 inet n  -       -       -       -       smtpd
	-o content_filter=
	-o local_recipient_maps=
	-o relay_recipient_maps=
	-o smtpd_restriction_classes=
	-o smtpd_client_restrictions=
	-o smtpd_helo_restrictions=
	-o smtpd_sender_restrictions=
	-o smtpd_recipient_restrictions=permit_mynetworks,reject
	-o strict_rfc821_envelopes=yes
	-o mynetworks=127.0.0.0/8
	-o smtpd_error_sleep_time=0 -o smtpd_soft_error_limit=1001
	-o smtpd_hard_error_limit=1001
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
tlsmgr    unix  -       -       n       300   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
#smtp      unix  -       -       -       -       -       smtp
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       -       -       -       smtp
	-o fallback_relay=
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache	  unix	-	-	-	-	1	scache
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
scalemail-backend unix	-	n	n	-	2	pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

```


main.cf
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

# TLS parameters



# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = optisvr.pctechcentral.com
myorigin = /etc/mailname
mydestination =
relayhost = smtp-server.woh.rr.com
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks_style = host
masquerade_domains = optisvr.pctechcentral.com
masquerade_exceptions = root
delay_warning_time = 4h
unknown_local_recipient_reject_code = 450
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
smtp_helo_timeout = 60s
smtpd_recipient_limit = 16
smtpd_soft_error_limit = 3
smtpd_hard_error_limit = 12

smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_client_restrictions = reject_rbl_client smtp.dnsbl.sorbs.net
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000, permit
smtpd_helo_required = yes
smtpd_delay_reject = yes
disable_vrfy_command = yes

smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_path = smtpd
#smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = 

alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf

smtpd_use_tls = yes
smtpd_tls_cert_file = /etc/postfix/postfix.cert
smtpd_tls_key_file = /etc/postfix/postfix.key
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

content_filter = amavis:[127.0.0.1]:10024
#receieve_override_options = no_address_mappings
```


It is a virtual domain, mysql setup, and I had to follow the tutorial to get it all working right. Like I said it WAS working, and now it no longer is...If I can provide anymore information to help you help me, please let me know! Thanks for taking your time to read this :)

---

### Post by rekon on 2007-12-08
Well I thought maybe I had a problem with my Relay server with my ISP but that is not the issue. I can send emails to local recipients but anything beyond my local addresses I receive the SMTP connection error. Any thoughts?

---

### Post by HermanAB on 2007-12-08
Postfix has some queue debug utilities - can't remember the names.  Look on the Postfix web site for debug help:
[http://www.postfix.org/DEBUG_README.html](http://www.postfix.org/DEBUG_README.html)

Otherwise, I would stop all mail services, confirm they are stopped with 'ps -e', then restart things carefully and watch the error messages in /var/log/messages and other mail related log files.  Any clues will be in there.

I usually debug things using the simplest tools I can find - since I don't want to debug the tool - I use simple tools i can trust.  So I debug things with 'telnet' and 'mail'.

For example, to see whether postfix is listening:
$ telnet ipaddress 25

To send a simple message:
$ mail -s test [email]joesoap@example.com[/email]
.

while at the same time watching the logs with one or more 'tail' commands:
$ sudo tail -f /var/log/messages

$ sudo tail -f /var/log/maillog

'Hope that helps!

Herman

---

### Post by rekon on 2007-12-08
Thanks for your reply Herman. I have been trying to debug it for the past few days now and everything starts up with no errors. I am able to telnet into the machine on port 25 and create an email, but after I try to send it, it gets stuck in the queue with the error SMTP connection refused. I gave up and am currently installing 7.10 and following this guide: [http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10](http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10) ... 

Hopefully it will workout! Since this is my own little personal server that I basically use to learn on I have the luxery of reformatting and installing everything again and again until I get it right. 

I would still love to know what caused the SMTP service to fail, and I am guessing it was something to do with the content filtering since I was able to telnet in and create an email. 

Anyways, thanks alot for your reply and I will post back when I get it all working again.

---

### Post by HermanAB on 2007-12-09
OK, but postfix.org is your best reference.  Postfix is so complex, that there is no substitute for reading the manual.

One day when you are fed-up with Postfix, try Citadel.  It is the only zero maintenance mail system I know of.  I am too busy to afford screwing around with systems all the time.  Once I set something up, it has to keep working for years without wasting my time and Citadel fits that requirement purrrrrfectly.

Cheers,

H.

---

### Post by MJN on 2007-12-09
> **rekon said:**
> ```

#smtp      unix  -       -       -       -       -       smtp
```

It's because you commented out the client entry - don't - it's needed!

The reason it was working is likely because the smtp daemon was running before you made this step. Only now that it's had to be called/started again does the mistake manifest itself.

Mathew

---


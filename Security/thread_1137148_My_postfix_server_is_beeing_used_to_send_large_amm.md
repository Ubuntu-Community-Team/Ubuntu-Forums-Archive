---
title: "My postfix server is beeing used to send large ammounts of spam."
date: 2009-04-25
forum: Security
---

### Post by trileru808 on 2009-04-25
Hello people. I have a big problem. My postfix server is beeing used to send large ammounts of spam. I noticed this a few days ago when users from my network were complaining that some of their email end up as spam in other networks. I configured my mail server properly and dns also, and that usually didn't happen. Last night one user forwarded me an email from gmail:

The mail system

<example@gmail.com>: delivery temporarily suspended: host
    alt4.gmail-smtp-in.l.google.com[209.85.221.90] refused to talk to me:
    421-4.7.0 [89.xxx.yyy.zzz] Our system has detected an unusual amount of
    421-4.7.0 unsolicited mail originating from your IP address. To protect
our
    421-4.7.0 users from spam, mail sent from your IP address has been
    temporarily 421-4.7.0 blocked. Please visit
    [http://www.google.com/mail/help/bulk_mail.html](http://www.google.com/mail/help/bulk_mail.html) 421 4.7.0 to review our
Bulk
    Email Senders Guidelines. 30si2121724qyk.13


 and I started to worry :). My build is made exactly like this [http://www.howtoforge.com/perfect-server-ubuntu-8.10](http://www.howtoforge.com/perfect-server-ubuntu-8.10) . I checked the server, and the mailqueue was 10.000 long. That's nuts for a company with 30 total mail users, by witch 10 are very active. So I started to dig arround... (elementary my dear Watson :)) ) and then I saw the logs. At least I tried to but „cat” and „less” were going nuts..so I downloaded the logs so I can check them proper from a decent graphical text editor. Because they were 150 megs long for a day last 3-4 days. Time to check out what's going on. Couldn't understand jack since I am relatively new to linux world. The large amount of data in the logs was the thing that really worried me. After a few test mails, I realized that Gmail and Yahoo are refusing the mails coming from my server. Internal emails were slowed alot last days, and alot of incoming mail was marked as spam, even from trusted domains we used for exchanging data.
First actions I took the action of blocking port 25 by witch mail servers cumunicate to each other.  Commented out the following line from /etc/postfix/master.cf :

smtp      inet  n       -       -       -       -       smtpd

restarted then shut down postfix and then I cleaned the postfix queue with „postsuper -d ALL”, finalising with killing each process that was in the list of „lsof -i :25” (like 40-50 entries). Now postfix doesn't send out spam. Emails inside the network work very good now, we can send out emails, we just can't receive any outside email since I closed port 25. What can I do next to receive emails from outside, minus the spam problem? 

Here are the config files and logs:
/etc/postfix/main.cf :

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
delay_warning_time = 4h
unknown_local_recipient_reject_code = 450
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
#smtpd_tls_ask_ccert = yes
#smtpd_tls_req_ccert = no
smtp_tls_cert_file = /etc/postfix/ssl/smtp.crt
smtp_tls_key_file = /etc/postfix/ssl/smtp.key
smtp_tls_CAfile = /etc/postfix/ssl/cacertt.pem

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

mydomain = mydomain.com
myhostname = mail.mydomain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = /etc/postfix/local-host-names
relayhost = 
mynetworks = 89.xxx.yyy.0/30, 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
message_size_limit = 50000000
recipient_delimiter = +
inet_interfaces = all
inet_protocols = ipv4
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination, reject_unauth_pipelining, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, permit
#smtpd_data_restrictions = reject_unauth_pipelining
#smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
#smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
#smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
smtpd_helo_required = yes
smtpd_delay_reject = yes
disable_vrfy_command = yes
smtpd_recipient_limit = 100
smtpd_soft_error_limit = 10
smtpd_hard_error_limit = 20
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 2
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
message_size_limit = 52400000
virtual_maps = hash:/etc/postfix/virtusertable


and /etc/postfix/master.cf

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
#smtp      inet  n       -       -       -       -       smtpd 
	-o message_size_limit=50000000
submission inet n       -       -       -       -       smtpd
smtps	  inet  n       -       -       -       -       smtpd
  -o smtpd_tls_security_level=encrypt
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
  -o milter_macro_daemon_name=ORIGINATING
  -o smtpd_tls_wrappermode=yes
  -o message_size_limit=25000000
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
scalemail-backend unix	-	n	n	-	2	pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}


/var/log/mail.info (a small part)

Apr 25 07:09:07 server1 postfix/smtp[24538]: connect to mhost01h.leeds.ac.uk[129.11.77.238]:25: Connection timed out
Apr 25 07:09:07 server1 postfix/smtp[24554]: connect to video.fox23news.com[66.179.120.80]:25: Connection timed out
Apr 25 07:09:07 server1 postfix/smtp[24554]: C3B3959462A: to=<82817@video.fox23news.com>, relay=none, delay=474297, delays=474267/0.15/30/0, dsn=4.4.1, status=deferred (connect to video.fox23news.com[66.179.120.80]:25: Connection timed out)
Apr 25 07:09:07 server1 postfix/smtp[24554]: C3B3959462A: to=<82849@video.fox23news.com>, relay=none, delay=474297, delays=474267/0.15/30/0, dsn=4.4.1, status=deferred (connect to video.fox23news.com[66.179.120.80]:25: Connection timed out)
Apr 25 07:09:07 server1 postfix/smtp[24554]: C3B3959462A: to=<82862@video.fox23news.com>, relay=none, delay=474297, delays=474267/0.15/30/0, dsn=4.4.1, status=deferred (connect to video.fox23news.com[66.179.120.80]:25: Connection timed out)
Apr 25 07:09:07 server1 postfix/smtp[24554]: C3B3959462A: to=<82867@video.fox23news.com>, relay=none, delay=474297, delays=474267/0.15/30/0, dsn=4.4.1, status=deferred (connect to video.fox23news.com[66.179.120.80]:25: Connection timed out)
Apr 25 07:09:07 server1 postfix/smtp[24554]: C3B3959462A: to=<82868@video.fox23news.com>, relay=none, delay=474297, delays=474267/0.15/30/0, dsn=4.4.1, status=deferred (connect to video.fox23news.com[66.179.120.80]:25: Connection timed out)
Apr 25 07:09:07 server1 postfix/smtp[24554]: C3B3959462A: to=<82869@video.fox23news.com>, relay=none, delay=474297, delays=474267/0.15/30/0, dsn=4.4.1, status=deferred (connect to video.fox23news.com[66.179.120.80]:2


/var/log/mail.warn


pr 25 16:27:19 server1 last message repeated 2 times
Apr 25 16:27:19 server1 postfix/smtp[6947]: warning: open active 52500595847: No such file or directory
Apr 25 16:27:19 server1 postfix/smtp[6947]: warning: open active 3B2B25949CA: No such file or directory
Apr 25 16:27:19 server1 postfix/smtp[6947]: warning: open active 63927595257: No such file or directory
Apr 25 16:27:19 server1 postfix/smtp[6947]: warning: open active 6D766595A09: No such file or directory
Apr 25 16:27:19 server1 postfix/smtp[6947]: warning: open active E4E14594BC2: No such file or directory
Apr 25 16:27:19 server1 postfix/smtp[6947]: warning: open active 4208A594956: No such file or directory
Apr 25 16:27:19 server1 postfix/smtp[6947]: warning: open active 3F288594FFF: No such file or directory
Apr 25 16:27:19 server1 postfix/smtp[6947]: warning: open active 163331D4A89: No such file or directory
Apr 25 16:27:19 server1 postfix/smtp[6947]: warning: open active E9D721D1BD3: No such file or directory
Apr 25 16:27:19 server1 postfix/smtp[6947]: warning: open active 7C2A91D0C66: No such file or directory
Apr 25 16:27:19 server1 postfix/smtp[6947]: warning: open active 4A67C5948A7: No such file or directory
Apr 25 16:27:19 server1 postfix/smtp[6947]: warning: open active 4A67C5948A7: No such file or directory
Apr 25 16:27:19 server1 postfix/smtp[6947]: warning: open active AF9681D1B30: No such file or directory
Apr 25 16:27:19 server1 postfix/smtp[6947]: warning: open active 3AE40595C6D: No such file or directory
Apr 25 16:27:19 server1 postfix/smtp[6947]: warning: open active BDDEF1D1879: No such file or directory
Apr 25 16:27:19 server1 postfix/smtp[6947]: warning: open active BDDEF1D1879: No such file or directory
Apr 25 16:27:19 server1 postfix/smtp[6947]: warning: open active A203C1D1A8B: No such file or directory
Apr 25 16:27:19 server1 postfix/smtp[6947]: warning: open active BAA47595EC0: No such file or directory
Apr 25 16:27:19 server1 postfix/smtp[6947]: warning: open active 38F311D100F: No such file or directory


/var/log/mail.log


Apr 25 07:08:37 server1 postfix/qmgr[17815]: 1D2A41D4775: from=<E-cards@Hallmark.com>, size=2084, nrcpt=16 (queue active)
Apr 25 07:08:37 server1 postfix/qmgr[17815]: 182C51D474A: from=<E-cards@Hallmark.com>, size=2084, nrcpt=16 (queue active)
Apr 25 07:08:37 server1 postfix/qmgr[17815]: 1FEAF1D194E: from=<E-cards@Hallmark.com>, size=2190, nrcpt=16 (queue active)
Apr 25 07:08:37 server1 postfix/qmgr[17815]: 120B11D1AF7: from=<E-cards@Hallmark.com>, size=2190, nrcpt=16 (queue active)
Apr 25 07:08:37 server1 postfix/qmgr[17815]: 138CE594CCF: from=<E-cards@Hallmark.com>, size=2147, nrcpt=16 (queue active)
Apr 25 07:08:37 server1 postfix/qmgr[17815]: 1FB985959B7: from=<E-cards@Hallmark.com>, size=2181, nrcpt=16 (queue active)
Apr 25 07:08:37 server1 postfix/qmgr[17815]: 179EC5943A2: from=<E-cards@Hallmark.com>, size=2147, nrcpt=16 (queue active)
Apr 25 07:08:37 server1 postfix/qmgr[17815]: 196335945FE: from=<E-cards@Hallmark.com>, size=2147, nrcpt=16 (queue active)
Apr 25 07:08:37 server1 postfix/qmgr[17815]: 163401D187D: from=<E-cards@Hallmark.com>, size=2190, nrcpt=16 (queue active)
Apr 25 07:08:37 server1 postfix/qmgr[17815]: 157D31D144A: from=<E-cards@Hallmark.com>, size=2190, nrcpt=16 (queue active)
Apr 25 07:08:37 server1 postfix/qmgr[17815]: 14113595D24: from=<E-cards@Hallmark.com>, size=2190, nrcpt=16 (queue active)
Apr 25 07:08:37 server1 postfix/qmgr[17815]: 1868F1D15A8: from=<E-cards@Hallmark.com>, size=2190, nrcpt=16 (queue active)
Apr 25 07:08:37 server1 postfix/qmgr[17815]: 15E0C1D4841: from=<E-cards@Hallmark.com>, size=2084, nrcpt=16 (queue active)
Apr 25 07:08:37 server1 postfix/qmgr[17815]: 142E31D4D5D: from=<E-cards@Hallmark.com>, size=2084, nrcpt=16 (queue active)
Apr 25 07:08:37 server1 postfix/qmgr[17815]: 12159595887: from=<E-cards@Hallmark.com>, size=2181, nrcpt=16 (queue active)
Apr 25 07:08:37 server1 postfix/error[24557]: 126F21D140C: to=<billingcompliance@ouhsc.edu>, relay=none, delay=165993, delays=165993/0.04/0/0.06, dsn=4.0.0, status=deferred (delivery temporarily suspended: host smtp4.ouhsc.edu[157.142.11.65] refused to talk to me: 554 smtp4 ESMTP Blocked - see [https://support.proofpoint.com/dnsbl-lookup.cgi?ip=89.238.221.142](https://support.proofpoint.com/dnsbl-lookup.cgi?ip=89.238.221.142))
Apr 25 07:08:37 server1 postfix/error[24536]: 1FEAF1D194E: to=<rbrevett@lincoln.edu>, relay=none, delay=163665, delays=163665/0/0/0.06, dsn=4.0.0, status=deferred (delivery temporarily suspended: host smtp3.lincoln.edu[192.131.155.110] refused to talk to me: 554 pps1.lincoln.edu ESMTP not accepting messages)
Apr 25 07:08:37 server1 postfix/error[24559]: 1482E1D12AE: to=<astrid-rasmussen@ouhsc.edu>, relay=none, delay=166105, delays=166105/0.04/0/0.08, dsn=4.0.0, status=deferred (delivery temporarily suspended: host smtp4.ouhsc.edu[157.142.11.65] refused to talk to me: 554 smtp4 ESMTP Blocked - see [https://support.proofpoint.com/dnsbl-lookup.cgi?ip=89.238.221.142](https://support.proofpoint.com/dnsbl-lookup.cgi?ip=89.238.221.142))
Apr 25 07:08:37 server1 postfix/error[24535]: 1D2A41D4775: to=<geoshorty@home.com>, relay=none, delay=26981, delays=26981/0.04/0/0.08, dsn=4.4.1, status=deferred (delivery temporarily suspended: connect to mx1.home.com[10.42.23.11]:25: Connection timed out)
Apr 25 07:08:37 server1 postfix/error[24566]: 1868F1D15A8: to=<tj_sutton@bellsouth.net>, relay=none, delay=230975, delays=230975/0.02/0/0.03, dsn=4.0.0, status=deferred (delivery temporarily suspended: host gateway-f1.isp.att.net[204.127.217.16] refused to talk to me: 550-89.238.221.142 blocked by ldap:ou=rblmx,dc=att,dc=net 550 Error - Blocked for abuse. See [http://att.net/blocks](http://att.net/blocks))
Apr 25 07:08:37 server1 postfix/error[24565]: 120B11D1AF7: to=<rdaerr@kent.edu>, relay=none, delay=163652, delays=163652/0.03/0/0.03, dsn=4.0.0, status=deferred (delivery temporarily suspended: host mx2.kent.edu.gslb.pphosted.com[208.86.201.10] refused to talk to me: 554 mx.kent.edu.pph5a.pphosted.com ESMTP Blocked - see [https://support.proofpoint.com/dnsbl-lookup.cgi?ip=89.238.221.142](https://support.proofpoint.com/dnsbl-lookup.cgi?ip=89.238.221.142))
Apr 25 07:08:37 server1 postfix/error[24566]: 1868F1D15A8: to=<tjacks78@bellsouth.net>, relay=none, delay=230975, delays=230975/0.02/0/0.05, dsn=4.0.0, status=deferred (delivery temporarily suspended: host gateway-f1.isp.att.net[204.127.217.16] refused to talk to me: 550-89.238.221.142 blocked by ldap:ou=rblmx,dc=att,dc=net 550 Error - Blocked for abuse. See [http://att.net/blocks](http://att.net/blocks))
Apr 25 07:08:37 server1 postfix/qmgr[17815]: 186EB1D4366: from=<E-cards@Hallmark.com>, size=2105, nrcpt=16 (queue active)
Apr 25 07:08:37 server1 postfix/qmgr[17815]: 45CA11D1385: from=<E-cards@Hallmark.com>, size=2190, nrcpt=16 (queue active)
Apr 25 07:08:37 server1 postfix/qmgr[17815]: 4961259450F: from=<E-cards@Hallmark.com>, size=2147, nrcpt=16 (queue active)
Apr 25 07:08:37 server1 postfix/qmgr[17815]: 4F6151D10E1: from=<E-cards@Hallmark.com>, size=2190, nrcpt=16 (queue active)
Apr 25 07:08:37 server1 postfix/qmgr[17815]: 40D38594671: from=<E-cards@Hallmark.com>, size=2147, nrcpt=16 (queue active)
Apr 25 07:08:37 server1 postfix/qmgr[17815]: 46FC71D1362: from=<E-cards@Hallmark.com>, size=2190, nrcpt=16 (queue active)
Apr 25 07:08:37 server1 postfix/qmgr[17815]: 4EA371D1B18: from=<E-cards@Hallmark.com>, size=2190, nrcpt=16 (queue active)
Apr 25 07:08:37 server1 postfix/qmgr[17815]: 41F3B1D4B20: from=<E-cards@Hallmark.com>, size=2084, nrcpt=16 (queue active)
Apr 25 07:08:37 server1 postfix/qmgr[17815]: 440D51D152A: from=<E-cards@Hallmark.com>, size=2190, nrcpt=16 (queue active)


What can I do?

Thank you very much for reading my problem, and have a nice evening.

---

### Post by HermanAB on 2009-04-25
Howdy,

Have a look at the list of users on the machine.  You may have been compromized and someone can now log in with SSH and do what he wants.

The user account list:
$ sudo cat /etc/passwd

If you see a rogue, remove him:
$ sudo userdel -r username

Then look at the logs in /var/log and see who logged in.  For example:
$ ls /var/log
$ sudo tail -n 10000 /var/log/messages | less

If you can figure out who is logging in and sending the spam, block him with a drop command in iptables:
$ sudo iptables -I INPUT -i eth0 -s 1.2.3.4 -j DROP

Add some UCE controls to postfix /etc/mail/main.cf:
[http://www.postfix.org/uce.html](http://www.postfix.org/uce.html)

---


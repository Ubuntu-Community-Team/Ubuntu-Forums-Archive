---
title: "postfix spam. someone is using my server to send spam and it's not open relay"
date: 2010-03-19
forum: Server Platforms
---

### Post by trileru808 on 2010-03-19
Hello. I have an Ubuntu 9.04 server with postfix/courier installed. Last week I had thousands of spam in mailq and alot of connections on port 25. I got on many blacklists and I try to get rid of this problem.
My configuration is pretty tight and I am not an open relay. Can you tell me please what should I do? Last time happened 5 days ago, I just closed port 25 and cleared the mailq and added some stuff at "smtpd_recipient_restrictions" but now it happened again. If my server isn't an open relay, how could this happen?

Here's my configuration and some text from the logs


/etc/postfix/main.cf

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific: Specifying a file name will cause the first
# line of that file to be used as the name. The Debian default
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
smtpd_tls_cert_file = /etc/postfix/ssl/newssl/1/cert.pem
smtpd_tls_key_file = /etc/postfix/ssl/newssl/1/key.pem
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
#smtpd_tls_ask_ccert = yes
#smtpd_tls_req_ccert = no
smtp_tls_cert_file = /etc/postfix/ssl/newssl/2/cert.pem
smtp_tls_key_file = /etc/postfix/ssl//newssl/2/key.pem
smtp_tls_CAfile = /etc/postfix/ssl/newssl/2/cacert.pem

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

mydomain = mail.xxx.ro
myhostname = mail.xxx.ro
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
#$mydomain
mydestination = /etc/postfix/local-host-names
relayhost = 
#$mydomain
mynetworks = 127.0.0.0/8
mynetworks_style = host
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
smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_unauth_destination, reject_unauth_pipelining, reject_non_fqdn_sender, reject_non_fqdn_recipient, reject_unknown_sender_domain, reject_invalid_hostname, reject_unknown_recipient_domain, reject_unauth_destination, reject_rbl_client bl.spamcop.net, reject_rbl_client list.dsbl.org, reject_rbl_client zen.spamhaus.org, reject_rbl_client dnsbl.sorbs.net, permit
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
#smtpd_helo_restrictions = permit_mynetworks, reject_unknown_hostname, permit
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, permit
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
smtpd_helo_required = yes
smtpd_delay_reject = yes
disable_vrfy_command = yes
strict_rfc821_envelopes = yes
invalid_hostname_reject_code = 554
multi_recipient_bounce_reject_code = 554
non_fqdn_reject_code = 554
relay_domains_reject_code = 554
unknown_address_reject_code = 554
unknown_client_reject_code = 554
unknown_hostname_reject_code = 554
unknown_local_recipient_reject_code = 554
unknown_relay_recipient_reject_code = 554
unknown_sender_reject_code = 554
unknown_virtual_alias_reject_code = 554
unknown_virtual_mailbox_reject_code = 554
unverified_recipient_reject_code = 554
unverified_sender_reject_code = 554
soft_bounce = yes
smtpd_recipient_limit = 100
smtpd_soft_error_limit = 10
smtpd_hard_error_limit = 20
smtpd_tls_auth_only = no
#smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/newssl/1/cacert.pem
smtpd_tls_loglevel = 2
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
#message_size_limit = 52400000
virtual_maps = hash:/etc/postfix/virtusertable

/etc/postfix/master.cf


#
# Postfix master process configuration file. For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type private unpriv chroot wakeup maxproc command + args
# (yes) (yes) (yes) (never) (100)
# ==========================================================================
smtp inet n - - - - smtpd 
-o message_size_limit=25000000
submission inet n - - - - smtpd
-o smtpd_tls_security_level=encrypt
-o smtpd_sasl_auth_enable=yes
-o smtpd_client_restrictions=permit_sasl_authenticated,reject
-o milter_macro_daemon_name=ORIGINATING
-o message_size_limit=25000000
#	-o smtpd_tls_wrappermode=yes
smtps	 inet n - - - - smtpd
-o smtpd_tls_security_level=encrypt
-o smtpd_sasl_auth_enable=yes
-o smtpd_client_restrictions=permit_sasl_authenticated,reject
-o milter_macro_daemon_name=ORIGINATING
-o smtpd_tls_wrappermode=yes
-o message_size_limit=25000000
#628 inet n - - - - qmqpd
pickup fifo n - - 60 1 pickup
cleanup unix n - - - 0 cleanup
qmgr fifo n - n 300 1 qmgr
#qmgr fifo n - - 300 1 oqmgr
tlsmgr unix - - - 1000? 1 tlsmgr
rewrite unix - - - - - trivial-rewrite
bounce unix - - - - 0 bounce
defer unix - - - - 0 bounce
trace unix - - - - 0 bounce
verify unix - - - - 1 verify
flush unix n - - 1000? 0 flush
proxymap unix - - n - - proxymap
proxywrite unix - - n - 1 proxymap
smtp unix - - - - - smtp
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay unix - - - - - smtp
-o smtp_fallback_relay=
# -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq unix n - - - - showq
error unix - - - - - error
retry unix - - - - - error
discard unix - - - - - discard
local unix - n n - - local
virtual unix - n n - - virtual
lmtp unix - - - - - lmtp
anvil unix - - - - 1 anvil
scache unix - - - - 1 scache
#
# ====================================================================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# Many of the following services use the Postfix pipe(8) delivery
# agent. See the pipe(8) man page for information about ${recipient}
# and other message envelope options.
# ====================================================================
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop unix - n n - - pipe
flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
#
# See the Postfix UUCP_README file for configuration details.
#
uucp unix - n n - - pipe
flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail unix - n n - - pipe
flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp unix - n n - - pipe
flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix	-	n	n	-	2	pipe
flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman unix - n n - - pipe
flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
${nexthop} ${user}



/var/log/mail.log




Mar 18 20:49:43 server1 postfix/smtp[10076]: 4BAF83CC22D: to=<ebenezer.b@ideefixe.com>, relay=smtp-gate.ebiuniverse.com[212.154.28.211]:25, delay=10869, delays=10832/36/0.78/0.12, dsn=4.0.0, status=SOFTBOUNCE (host smtp-gate.ebiuniverse.com[212.154.28.211] said: 553 sorry, this recipient is not in my validrcptto list (#5.7.1) (in reply to RCPT TO command))
Mar 18 20:49:43 server1 postfix/smtp[10323]: 40F883CC0D5: to=<curren.misti@lottobuilder.com>, relay=mail.lottobuilder.com[129.121.117.2]:25, delay=13544, delays=13507/34/0.55/2, dsn=4.1.1, status=SOFTBOUNCE (host mail.lottobuilder.com[129.121.117.2] said: 550 5.1.1 sorry, no mailbox here by that name (chkuser) (in reply to RCPT TO command))
Mar 18 20:49:43 server1 postfix/smtp[10858]: 40F883CC0D5: to=<curra.mariele@techie.com>, relay=mailin-02.mx.aol.com[64.12.90.65]:25, delay=13544, delays=13507/35/0.77/1.5, dsn=4.1.1, status=SOFTBOUNCE (host mailin-02.mx.aol.com[64.12.90.65] said: 550 5.1.1 <curra.mariele@techie.com>: Recipient address rejected: techie.com (in reply to RCPT TO command))
Mar 18 20:49:43 server1 postfix/smtp[10582]: 4BAF83CC22D: to=<ebetak@microstore.fr>, relay=mailhost.microstore.fr[195.68.51.122]:25, delay=10869, delays=10832/36/0.35/0.21, dsn=4.0.0, status=SOFTBOUNCE (host mailhost.microstore.fr[195.68.51.122] said: 554 Transaction failed (in reply to RCPT TO command))
Mar 18 20:49:43 server1 postfix/smtp[10639]: 4BAF83CC22D: to=<ebickleman@nomblot.fr>, relay=mx-vh.fr.clara.net[80.168.44.17]:25, delay=10869, delays=10832/37/0.26/0.07, dsn=4.0.0, status=SOFTBOUNCE (host mx-vh.fr.clara.net[80.168.44.17] said: 550 "ebickleman@nomblot.fr" is not a known user (in reply to RCPT TO command))
Mar 18 20:49:43 server1 postfix/smtp[10260]: 4BAF83CC22D: to=<eberlein.tristian@naj.com.pl>, relay=av.waw.cdp.pl[62.89.91.146]:25, delay=10869, delays=10832/37/0.34/0.09, dsn=4.7.1, status=SOFTBOUNCE (host av.waw.cdp.pl[62.89.91.146] said: 550 5.7.1 <eberlein.tristian@naj.com.pl>: Recipient address rejected: temporarily blocked because of previous errors - retrying too fast. penalty: 30 seconds x 0 retries. (in reply to RCPT TO command))
Mar 18 20:49:43 server1 postfix/smtp[9342]: Host offered STARTTLS: [post.dp-media.de]
Mar 18 20:49:43 server1 postfix/smtp[10252]: 40F883CC0D5: to=<curran.r@21cn.net>, relay=mta.21cn.net[59.36.102.89]:25, delay=13544, delays=13507/34/3/0.62, dsn=4.0.0, status=SOFTBOUNCE (host mta.21cn.net[59.36.102.89] said: 550 ?no such user (in reply to RCPT TO command))
Mar 18 20:49:43 server1 postfix/smtp[9705]: connect to gruene.isar.de[67.215.65.132]:25: Connection timed out
Mar 18 20:49:43 server1 postfix/smtp[9705]: 172113CC27D: to=<emka@gruene.isar.de>, relay=none, delay=9870, delays=9833/7.2/30/0, dsn=4.4.1, status=deferred (connect to gruene.isar.de[67.215.65.132]:25: Connection timed out)
Mar 18 20:49:43 server1 postfix/smtp[10323]: Host offered STARTTLS: [marsoul.univ-paris5.fr]
Mar 18 20:49:43 server1 postfix/smtp[10323]: 4BAF83CC22D: to=<eberto.k@psycho.univ-paris5.fr>, relay=marsoul.univ-paris5.fr[193.51.86.84]:25, delay=10869, delays=10832/37/0.2/0.06, dsn=4.0.0, status=SOFTBOUNCE (host marsoul.univ-paris5.fr[193.51.86.84] said: 550 <eberto.k@psycho.univ-paris5.fr>: Recipient address rejected: User unknown (in reply to RCPT TO command))
Mar 18 20:49:43 server1 postfix/smtp[10079]: 4BAF83CC22D: to=<eberhard.m@mail.energetyka.kalisz.pl>, relay=none, delay=10868, delays=10832/36/0.14/0, dsn=4.4.1, status=deferred (connect to dns.energetyka.kalisz.pl[193.243.146.15]:25: Connection refused)
Mar 18 20:49:43 server1 postfix/smtp[10351]: 4BAF83CC22D: to=<ebettley@laso.com.ar>, relay=mail.laso.com.ar[200.11.113.130]:25, delay=10869, delays=10832/36/1/0.3, dsn=4.1.1, status=SOFTBOUNCE (host mail.laso.com.ar[200.11.113.130] said: 550 5.1.1 <ebettley@laso.com.ar>: Recipient address rejected: User unknown in relay recipient table (in reply to RCPT TO command))
Mar 18 20:49:43 server1 postfix/smtp[10572]: 4BAF83CC22D: to=<eberl877@backproblems.com>, relay=smtp.secureserver.net[216.69.186.201]:25, delay=10870, delays=10832/35/2.1/0.39, dsn=4.0.0, status=SOFTBOUNCE (host smtp.secureserver.net[216.69.186.201] said: 550 #5.1.0 Address rejected [email]eberl877@backproblems.com[/email] (in reply to RCPT TO command))
Mar 18 20:49:43 server1 postfix/smtp[10260]: connect to spacestat.com[216.240.187.151]:25: Connection refused
Mar 18 20:49:43 server1 postfix/smtp[10582]: 4BAF83CC22D: to=<eberhard50@sensor.com.pl>, relay=poczta.sensor.com.pl[212.160.170.2]:25, delay=10870, delays=10832/37/0.26/0.23, dsn=4.0.0, status=SOFTBOUNCE (host poczta.sensor.com.pl[212.160.170.2] said: 550 <eberhard50@sensor.com.pl>: Recipient address rejected: User unknown in virtual alias table (in reply to RCPT TO command))
Mar 18 20:49:43 server1 postfix/smtp[10323]: 4BAF83CC22D: to=<ebenezer.g@tmt.de>, relay=mx.tmt.de[217.145.99.51]:25, delay=10870, delays=10832/37/0.21/0.05, dsn=4.1.1, status=SOFTBOUNCE (host mx.tmt.de[217.145.99.51] said: 550 5.1.1 <ebenezer.g@tmt.de>: Recipient address rejected: User unknown in local recipient table (in reply to RCPT TO command))
Mar 18 20:49:43 server1 postfix/smtp[10358]: 40F883CC0D5: to=<currie.kuehn@evonline.net>, relay=evonline.net[208.109.199.187]:25, delay=13545, delays=13507/34/0.63/3.2, dsn=4.0.0, status=SOFTBOUNCE (host evonline.net[208.109.199.187] said: 550 sorry, no mailbox here by that name. (#5.7.17) (in reply to RCPT TO command))
Mar 18 20:49:44 server1 postfix/smtp[10079]: 4161A3CC22B: host hrndva-smtpin01.mail.rr.com[71.74.56.243] refused to talk to me: 554 5.7.1 - ERROR: Mail refused - <xxx.xxx.xxx.xxx> - See [http://security.rr.com/cgi-bin/block...xx.xxx.xxx.xxx](http://security.rr.com/cgi-bin/block...xx.xxx.xxx.xxx)
Mar 18 20:49:44 server1 postfix/smtp[10582]: connect to cluster3.eu.messagelabs.com[85.158.139.67]:25: Connection refused
Mar 18 20:49:44 server1 postfix/smtp[10079]: 4161A3CC22B: to=<easy@cinci.rr.com>, relay=hrndva-smtpin02.mail.rr.com[71.74.56.244]:25, delay=10880, delays=10842/37/0.59/0, dsn=4.7.1, status=deferred (host hrndva-smtpin02.mail.rr.com[71.74.56.244] refused to talk to me: 554 5.7.1 - ERROR: Mail refused - <xxx.xxx.xxx.xxx> - See [http://security.rr.com/cgi-bin/block...xx.xxx.xxx.xxx](http://security.rr.com/cgi-bin/block...xx.xxx.xxx.xxx))
Mar 18 20:49:44 server1 postfix/smtp[10582]: Host offered STARTTLS: [cluster3.eu.messagelabs.com]
Mar 18 20:49:44 server1 postfix/smtp[10064]: 475003CC235: to=<eda.rodenburg@hkcable.com.hk>, relay=mail.hkcable.com.hk[61.10.0.169]:25, delay=10815, delays=10776/31/6.4/0.74, dsn=4.1.1, status=SOFTBOUNCE (host mail.hkcable.com.hk[61.10.0.169] said: 550 5.1.1 <eda.rodenburg@hkcable.com.hk>... User unknown (in reply to RCPT TO command))
Mar 18 20:49:44 server1 postfix/smtp[9363]: Host offered STARTTLS: [about.com.mail9.psmtp.com]
Mar 18 20:49:44 server1 postfix/smtp[10079]: 4161A3CC22B: to=<earvin.citro@erfolgskonzept.com>, relay=mxlb.ispgateway.de[80.67.18.126]:25, delay=10881, delays=10842/38/0.19/0.06, dsn=4.0.0, status=SOFTBOUNCE (host mxlb.ispgateway.de[80.67.18.126] said: 554 Sorry, no mailbox here by that name. (in reply to RCPT TO command))
Mar 18 20:49:44 server1 postfix/smtp[10582]: 4161A3CC22B: to=<earthman.zebadiah@diageo.com>, relay=cluster3.eu.messagelabs.com[194.106.220.51]:25, delay=10881, delays=10842/38/0.38/0.28, dsn=4.0.0, status=SOFTBOUNCE (host cluster3.eu.messagelabs.com[194.106.220.51] said: 553-Message filtered. Please see the FAQs section on spam 553-at [http://www.messagelabs.com/support/](http://www.messagelabs.com/support/) for more 553 information. (#5.7.1) (in reply to end of DATA command))
Mar 18 20:49:44 server1 postfix/smtp[10358]: 4161A3CC22B: to=<easey.isak@email.it>, relay=mx.email.it[212.97.34.36]:25, delay=10881, delays=10842/38/0.35/0.15, dsn=4.1.1, status=SOFTBOUNCE (host mx.email.it[212.97.34.36] said: 550 5.1.1 <easey.isak@email.it>: Recipient address rejected: User unknown (in reply to RCPT TO command))
Mar 18 20:49:44 server1 postfix/smtp[10260]: 4BAF83CC22D: to=<ebenezer.b@spacestat.com>, relay=none, delay=10870, delays=10832/37/0.42/0, dsn=4.4.1, status=deferred (connect to spacestat.com[216.240.187.151]:25: Connection refused)
Mar 18 20:49:44 server1 postfix/smtp[10568]: connect to rollenspieltreff.de[148.160.29.10]:25: Connection timed out
Mar 18 20:49:44 server1 postfix/smtp[10568]: 172113CC27D: to=<emilio.pellegrino@rollenspieltreff.de>, relay=none, delay=9872, delays=9833/8.4/30/0, dsn=4.4.1, status=deferred (connect to rollenspieltreff.de[148.160.29.10]:25: Connection timed out)



/var/log/mail.info


Mar 19 11:42:45 server1 postfix/smtp[11312]: EA7EE3CC2C8: to=<f.lausberg@wdr.de>, relay=smtp41.wdr.de[149.219.195.41]:25, delay=62577, delays=62368/208/0.28/0.09, dsn=4.0.0, status=SOFTBOUNCE (host smtp41.wdr.de[149.219.195.41] said: 550 #5.1.0 Address rejected [email]f.lausberg@wdr.de[/email] (in reply to RCPT TO command))
Mar 19 11:42:46 server1 postfix/smtp[12076]: Host offered STARTTLS: [mailgate.stone-rich.at]
Mar 19 11:42:46 server1 postfix/smtp[10547]: connect to listeningparty.tv[67.215.65.132]:25: Connection timed out
Mar 19 11:42:46 server1 postfix/smtp[11822]: EA7EE3CC2C8: to=<f.kruesmann@spectralite.ca>, relay=mx1.xittel.net[205.151.16.100]:25, delay=62577, delays=62368/208/0.65/0.17, dsn=4.0.0, status=SOFTBOUNCE (host mx1.xittel.net[205.151.16.100] said: 554 Service unavailable; Client host [xxxx.ro] blocked using Barracuda Reputation; [http://www.barracudanetworks.com/reputation/?r=1&ip=](http://www.barracudanetworks.com/reputation/?r=1&ip=) (in reply to RCPT TO command))
Mar 19 11:42:46 server1 postfix/smtp[10547]: 87B123CC951: to=<jg-soft@listeningparty.tv>, relay=none, delay=39042, delays=38832/180/30/0, dsn=4.4.1, status=deferred (connect to listeningparty.tv[67.215.65.132]:25: Connection timed out)
Mar 19 11:42:46 server1 postfix/smtp[11822]: EA7EE3CC2C8: lost connection with mx1.xittel.net[205.151.16.100] while sending DATA command
Mar 19 11:42:46 server1 postfix/smtp[11224]: EA7EE3CC2C8: to=<f.kueppers@misteradgood.de>, relay=none, delay=62576, delays=62368/208/0.12/0, dsn=4.4.1, status=deferred (connect to misteradgood.de[80.81.243.184]:25: Connection refused)
Mar 19 11:42:46 server1 postfix/smtp[12076]: EA7EE3CC2C8: to=<f.lincoln@i-net.at>, relay=mailgate.stone-rich.at[80.75.240.147]:25, delay=62577, delays=62368/207/2.2/0.13, dsn=4.0.0, status=SOFTBOUNCE (host mailgate.stone-rich.at[80.75.240.147] said: 550 <f.lincoln@i-net.at>, Recipient unknown (in reply to RCPT TO command))
Mar 19 11:42:46 server1 postfix/smtp[11224]: E5B903CC13C: host cdptpa-smtpin01.mail.rr.com[75.180.132.243] refused to talk to me: 554 5.7.1 - ERROR: Mail refused - <> - See [http://security.rr.com/cgi-bin/block-lookup?](http://security.rr.com/cgi-bin/block-lookup?)
Mar 19 11:42:46 server1 postfix/smtp[10547]: E5B903CC13C: to=<dbig@dublinia.ie>, relay=mail.dublinia.ie[82.195.156.10]:25, delay=66190, delays=65980/209/0.26/0.15, dsn=4.0.0, status=SOFTBOUNCE (host mail.dublinia.ie[82.195.156.10] said: 550 Requested action not taken: mailbox unavailable or not local (in reply to RCPT TO command))
Mar 19 11:42:46 server1 postfix/smtp[12079]: 9F9463CC3EF: lost connection with gbrsecurity.telesp.net.br[200.171.222.88] while receiving the initial server greeting
Mar 19 11:42:46 server1 postfix/smtp[11656]: connect to online-hacker.de[216.8.179.23]:25: Connection timed out
Mar 19 11:42:46 server1 postfix/smtp[11656]: 87B123CC951: to=<jguvj@online-hacker.de>, relay=none, delay=39042, delays=38832/180/30/0, dsn=4.4.1, status=deferred (connect to online-hacker.de[216.8.179.23]:25: Connection timed out)
Mar 19 11:42:46 server1 postfix/smtp[12032]: EA7EE3CC2C8: to=<f.kruesmann@tvv.volley.de>, relay=mxa.volley.de[62.146.95.134]:25, delay=62577, delays=62368/208/1.3/0.1, dsn=4.3.0, status=SOFTBOUNCE (host mxa.volley.de[62.146.95.134] said: 553 5.3.0 <f.kruesmann@tvv.volley.de>... No such user here (in reply to RCPT TO command))
Mar 19 11:42:46 server1 postfix/smtp[11822]: E5B903CC13C: to=<dbenevento@crosswinds.net>, relay=mx3.crosswinds.net[8.21.33.47]:25, delay=66190, delays=65980/209/0.5/0.15, dsn=4.7.1, status=SOFTBOUNCE (host mx3.crosswinds.net[8.21.33.47] said: 554 5.7.1 <dbenevento@crosswinds.net>: Recipient address rejected: Access denied (in reply to RCPT TO command))
Mar 19 11:42:46 server1 postfix/smtp[11224]: E5B903CC13C: to=<dbifalco2@ec.rr.com>, relay=cdptpa-smtpin02.mail.rr.com[75.180.132.244]:25, delay=66190, delays=65980/209/0.66/0, dsn=4.7.1, status=deferred (host cdptpa-smtpin02.mail.rr.com[75.180.132.244] refused to talk to me: 554 5.7.1 - ERROR: Mail refused - <> - See [http://security.rr.com/cgi-bin/block-lookup?](http://security.rr.com/cgi-bin/block-lookup?))

---

### Post by madverb on 2010-03-19
Are you certain it isn't an open relay?

---

### Post by trileru808 on 2010-03-19
I tested it on abuse.net and it said that it isn't... The settings are also for not open relay.


from abuse.net

Relay test result

All tests performed, no relays accepted.

---

### Post by jrssystemsnet on 2010-03-19
The server is probably compromised some other way - for example, are you running Apache on the same box?

You showed us the lines from the logs showing those messages going OUT to other servers... but you didn't show us the lines from the logs showing those messages arriving IN the queue to begin with, which would help answer your question.

Once we see the lines showing those messages getting in the queue to begin with, we can start figuring out whether the server is compromised elsewhere, or whether someone using AUTH SMTP had their account get compromised, or what.

---

### Post by jrssystemsnet on 2010-03-19
How about try giving us the output of **grep ebenezer\.b\@ideefixe\.com /var/log/mail.log** and we'll go from there.

---

### Post by KB1JWQ on 2010-03-19
Concur.  We need inject information.

---


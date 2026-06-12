---
title: "ClamAV Postfix Scanning"
date: 2010-12-31
forum: Server Platforms
---

### Post by xathras1982 on 2010-12-31
Hi,
I've followed the Postfix, SpamAssassin, ClamAV tutorial. However, I have a question.

I've sent an email with an attachment with a known virus signature, however I can't see anything to say that it was scanned for viruses, just spamassassin - any ideas?

Below is the email details:


> 
Return-Path: <xxxxxx@gmail.com>
X-Original-To: [email]xxxxxx@xxxxxx.dyndns.info[/email]
Delivered-To: [email]xxxxxx@xxxxxx.dyndns.info[/email]
Received: by ubuntu.lan (Postfix, from userid 5001)
id 5D59620F7E; Fri, 31 Dec 2010 16:52:10 +0000 (GMT)
X-Spam-Checker-Version: SpamAssassin 3.3.1 (2010-03-16) on ubuntu.lan
X-Spam-Level: 
X-Spam-Status: No, score=-0.8 required=2.0 tests=DKIM_SIGNED,DKIM_VALID,
DKIM_VALID_AU,FREEMAIL_FROM,HTML_MESSAGE,RCVD_IN_D NSWL_LOW,TVD_SPACE_RATIO,
T_TO_NO_BRKTS_FREEMAIL autolearn=ham version=3.3.1
Received: from mail-bw0-f50.google.com (mail-bw0-f50.google.com [209.85.214.50])
by ubuntu.lan (Postfix) with ESMTP id E5E0620EA7
for <xxxxxxx@xxxxxx.dyndns.info>; Fri, 31 Dec 2010 16:52:08 +0000 (GMT)
Received: by bwg12 with SMTP id 12so11548214bwg.23
for <xxxxxxx@xxxxxx.dyndns.info>; Fri, 31 Dec 2010 08:52:07 -0800 (PST)
DKIM-Signature: v=1; a=rsa-sha256; c=relaxed/relaxed;
d=gmail.com; s=gamma;
h=domainkey-signature:mime-version:received:received:date:message-id
:subject:from:to:content-type;
bh=D9ehJNImbDLGrWmOTi3ZAhcJMBJPZcYw2UtPhWD9Bdw
b=cUgFMsjp605vZWh+EWmqKXuIsgZuxyTKHYkqEcJA2tPxFhCa tbQyc0MXmLNJFGDCvl
pH8A5cym49EbA8UqqbtVDA1ahx84exYlU7V2ZgAXdLyJpGSZvm mXYIz8819g+frpaDSz
ydx7hF43CzMzRGTNEKqnhyr8Ru+x/N3LCpioQ=
DomainKey-Signature: a=rsa-sha1; c=nofws;
d=gmail.com; s=gamma;
h=mime-version:date:message-id:subject:from:to:content-type;
b=NbIUovC1wsPjv+rKyfjpqBFY59h04IKWFVae3KIV1iAsyBpq U/RVTfNx4erNznbreB
WJSiguOp851s/mY2TNrRuxP2/VZg2un53FqTYOQ5LLfJJdrnDxik06a8CeiO06TAXOXq
Pau8JPATe5uEb1jE2ZqLb9zfZKllfs9getRmw=
MIME-Version: 1.0
Received: by 10.204.99.73 with SMTP id t9mr14072411bkn.34.1293814327180; Fri,
31 Dec 2010 08:52:07 -0800 (PST)
Received: by 10.204.134.145 with HTTP; Fri, 31 Dec 2010 08:52:07 -0800 (PST)
Date: Fri, 31 Dec 2010 16:52:07 +0000
Message-ID: <AANLkTik81J3WfgrmAh9Edv_Znh3HivwRRnbL1z6WQ+BM@mai l.gmail.com>
Subject: testing
From: xxxx <xxxxxx@gmail.com>
To: [email]xxxxxx@xxxxxx.dyndns.info[/email]
Content-Type: multipart/alternative; boundary=001485f7bf2c607de10498b79f67


Below is my main.cf file:

> 
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
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-x.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-x.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = ubuntu.lan
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = x.dyndns.info, ubuntu.lan, localhost.lan, localhost
relayhost = relay.o2broadband.co.uk
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command =
mailbox_size_limit = 0
recipient_delimiter = +

inet_interfaces = all

maps_rbl_domains = blackholes.mail-abuse.org
smtpd_recipient_restrictions = permit_mynetworks,
permit_sasl_authenticated,
reject_unauth_destination
check_relay_domains
#check_policy_service inet:127.0.0.1:60000

smtpd_client_restrictions = permit_mynetworks,
reject_maps_rbl
reject_unknown_client

smtpd_sender_restrictions = permit_mynetworks,
reject_invalid_hostname
reject_unknown_sender_domain
reject_non_fqdn_sender
reject_maps_rbl


home_mailbox = Maildir/
inet_protocols = all

disable_vrfy_command = yes
smtpd_delay_reject = yes
smtpd_helo_required = yes
reject_non_fqdn_hostname = yes
reject_invalid_hostname = yes

strict_rfc821_envelopes = yes
unknown_address_reject_code = 554
unknown_hostname_reject_code = 554
unknown_client_reject_code = 554


content_filter = smtp-amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings



Here is my master.cf

> 
# Postfix master process configuration file. For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ================================================== ========================
# service type private unpriv chroot wakeup maxproc command + args
# (yes) (yes) (yes) (never) (100)
# ================================================== ========================
smtp inet n - - - - smtpd
-o content_filter=spamassassin
#submission inet n - - - - smtpd
# -o smtpd_tls_security_level=encrypt
# -o smtpd_sasl_auth_enable=yes
# -o smtpd_client_restrictions=permit_sasl_authenticate d,reject
# -o milter_macro_daemon_name=ORIGINATING
#smtps inet n - - - - smtpd
# -o smtpd_tls_wrappermode=yes
# -o smtpd_sasl_auth_enable=yes
# -o smtpd_client_restrictions=permit_sasl_authenticate d,reject
# -o milter_macro_daemon_name=ORIGINATING
#628 inet n - - - - qmqpd
pickup fifo n - - 60 1 pickup
-o content_filter=
-o receive_override_options=no_header_body_checks
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
# ================================================== ==================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# Many of the following services use the Postfix pipe( delivery
# agent. See the pipe( man page for information about ${recipient}
# and other message envelope options.
# ================================================== ==================
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop unix - n n - - pipe
flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
#
# ================================================== ==================
#
# Recent Cyrus versions can use the existing "lmtp" master.cf entry.
#
# Specify in cyrus.conf:
# lmtp cmd="lmtpd -a" listen="localhost:lmtp" proto=tcp4
#
# Specify in main.cf one or more of the following:

uucp unix - n n - - pipe
flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail unix - n n - - pipe
flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp unix - n n - - pipe
flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix - n n - 2 pipe
flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman unix - n n - - pipe
flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
${nexthop} ${user}

spamassassin unix - n n - - pipe


user=spamd argv=/usr/bin/spamc -f -e
/usr/sbin/sendmail -oi -f ${sender} ${recipient}

smtp-amavis unix - - - - 2 smtp
-o smtp_data_done_timeout=1200
-o smtp_send_xforward_command=yes
-o disable_dns_lookups=yes
-o max_use=20

127.0.0.1:10025 inet n - - - - smtpd
-o content_filter=
-o local_recipient_maps=
-o relay_recipient_maps=
-o smtpd_restriction_classes=
-o smtpd_delay_reject=no
-o smtpd_client_restrictions=permit_mynetworks,reject
-o smtpd_helo_restrictions=
-o smtpd_sender_restrictions=
-o smtpd_recipient_restrictions=permit_mynetworks,rej ect
-o smtpd_data_restrictions=reject_unauth_pipelining
-o smtpd_end_of_data_restrictions=
-o mynetworks=127.0.0.0/8
-o smtpd_error_sleep_time=0
-o smtpd_soft_error_limit=1001
-o smtpd_hard_error_limit=1000
-o smtpd_client_connection_count_limit=0
-o smtpd_client_connection_rate_limit=0
-o receive_override_options=no_header_body_checks,no_ unknown_recipient_checks


---

### Post by xathras1982 on 2010-12-31
main.cf and master.cf amendments

---

### Post by xathras1982 on 2011-01-01
Sorry, forgot to add that the ClamAV, ClamAV daemon are running. I've also done a update on ClamAV.

---

### Post by Vegan on 2011-01-01
What is the problem? Does the receiver pick up the malware?

---

### Post by xathras1982 on 2011-01-01
Hi Vegan,
No, there is no record that the malware was detected. It passes through and i can see the end attachment in squirrelmail.
 
I would expect it to remove?

---

### Post by James78 on 2011-01-01
Can you try using the Eicar test virus? It's a simple way to test if the virus is detected, without using an actual virus.
[http://www.eicar.org/anti_virus_test_file.htm](http://www.eicar.org/anti_virus_test_file.htm)

Also, did you use [this guide]("https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto#ClamSMTP SMTP Virus Filter")? I see some indiscrepancies between your configuration and the one it lists there. I've used that guide to configure my own email server, and it detects viruses fine.

---

### Post by stmiller on 2011-01-01
Yeah clam should put something like this in the headers, 

```

X-Virus-Scanned: amavisd-new at domain.com
X-Spam-Flag: NO
X-Spam-Score: -2.3
X-Spam-Level: 
X-Spam-Status: No, score=-2.3 tagged_above=-999 required=5
	tests=[RCVD_IN_DNSWL_MED=-2.3] autolearn=ham

```

What is your /etc/clamav/clamd.conf?

Make sure it has 

ScanMail true

---

### Post by Roger_Smith on 2011-01-01
Need to make sure ClamAV is enabled in the amavis 15-av_scanners by uncommenting the ClamAV section.  Also need to make sure the @bypass_virus_checks_maps line in the 15-content_filter_mode is uncommented, as well as the @bypass_spam_checks_maps if you want SA to kick in.  These should be located in the /etc/amavis/conf.d/ folder.

I believe by default the amavisd-new config just passes email without touching it.

---

### Post by xathras1982 on 2011-01-02
Hi,
Thanks I revisted [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) and compared the configuration to mine and found the error of my ways :)

---

### Post by venol on 2011-04-24
the problem contrary with me. I Can't see header spamassassin, but I can see Header Clamav.

---


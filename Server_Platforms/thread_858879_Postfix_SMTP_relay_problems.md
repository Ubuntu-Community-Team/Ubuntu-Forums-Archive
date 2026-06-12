---
title: "Postfix SMTP relay problems"
date: 2008-07-14
forum: Server Platforms
---

### Post by psatyshur on 2008-07-14
Hi,

I am attempting to setup Postfix to send MDADM alerts to my email address in Ubuntu Server 8.04. However, I am having trouble setting up Postfix to do this. I am trying to send the email through the SMTP server of my web hosting company (1and1.com). To do this, I have set the 'relayhost' directive in Postfix's main.cf file. The server requires authentication, and must be connected on port 587. I believe I have set these as well.

I have tried sending mail from MDADM

```
sudo mdadm -F /dev/md0 -m patrick@xxxxxx.net -t -1
```

as well as from mutt, and get the same response: 

```
Diagnostic-Code: X-Postfix; unknown user: "patrick"
```

I notice in the mail.log, postfix indicates that the relay=local. shouldnt this be 1and1.com? Does anyone have any suggestions of things I can try? I have been going over the manual for Postfix for several hours, but for a n00b like myself, it is hard to comprehend.

I have attached the full text of some of the important files below. Let me know if more information is required.


/var/log/mail.log
```
Jul 14 00:09:27 Quasar postfix/pickup[9736]: 5F6BE56208F: uid=0 from=<root>
Jul 14 00:09:27 Quasar postfix/cleanup[9977]: 5F6BE56208F: message-id=<20080714050927.5F6BE56208F@xxxxxx.net>
Jul 14 00:09:27 Quasar postfix/qmgr[9735]: 5F6BE56208F: from=<root@xxxxxx.net>, size=787, nrcpt=1 (queue active)
Jul 14 00:09:27 Quasar postfix/local[9979]: 5F6BE56208F: to=<patrick@xxxxxx.net>, relay=local, delay=0.06, delays=0.04/0.01/0/0.02, dsn=5.1.1, status=bounced (unknown user: "patrick")
Jul 14 00:09:27 Quasar postfix/cleanup[9977]: 6B55D562090: message-id=<20080714050927.6B55D562090@xxxxxx.net>
Jul 14 00:09:27 Quasar postfix/bounce[9980]: 5F6BE56208F: sender non-delivery notification: 6B55D562090
Jul 14 00:09:27 Quasar postfix/qmgr[9735]: 6B55D562090: from=<>, size=2443, nrcpt=1 (queue active)
Jul 14 00:09:27 Quasar postfix/qmgr[9735]: 5F6BE56208F: removed
Jul 14 00:09:27 Quasar postfix/local[9979]: 6B55D562090: to=<pat@xxxxxx.net>, orig_to=<root@xxxxxx.net>, relay=local, delay=0.03, delays=0.02/0/0/0.01, dsn=2.0.0, status=sent (delivered to mailbox)
Jul 14 00:09:27 Quasar postfix/qmgr[9735]: 6B55D562090: removed

```

Error email
```
From: Mail Delivery System <MAILER-DAEMON@xxxxxx.net>
Subject: Undelivered Mail Returned to Sender
To: root@xxxxxx.net
Auto-Submitted: auto-replied

[-- Attachment #1: Notification --]
[-- Type: text/plain, Encoding: 7bit, Size: 0.4K --]

This is the mail system at host xxxxxx.net.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to postmaster.

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                   The mail system

<patrick@xxxxxx.net>: unknown user: "patrick"

[-- Attachment #2: Delivery report --]
[-- Type: message/delivery-status, Encoding: 7bit, Size: 0.3K --]

Reporting-MTA: dns; xxxxxx.net
X-Postfix-Queue-ID: 5F6BE56208F
X-Postfix-Sender: rfc822; root@xxxxxx.net
Arrival-Date: Mon, 14 Jul 2008 00:09:27 -0500 (CDT)

Final-Recipient: rfc822; patrick@xxxxxx.net
Action: failed
Status: 5.1.1
Diagnostic-Code: X-Postfix; unknown user: "patrick"

[-- Attachment #3: Undelivered Message --]
[-- Type: message/rfc822, Encoding: 7bit, Size: 0.7K --]

From: quasar@xxxxxx.net
To: patrick@xxxxxx.net
Subject: TestMessage event on /dev/md0:Quasar

This is an automatically generated mail message from mdadm
running on Quasar

A TestMessage event had been detected on md device /dev/md0.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sda1[0] sdd1[3] sdc1[2] sdb1[1]
      1875026112 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]

unused devices: <none>

```

postfix.cf
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version
#
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

myhostname = xxxxxx.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = xxxxxx.net, 1and1.com

relayhost = [smtp.1and1.com]:submission
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options =

mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
```

master.cf
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

### Post by psatyshur on 2008-07-14
Anyone?

---

### Post by Ocelaris on 2008-11-20
well, you have "relayhost=[1and1.com]:submission 

shouldn't that be 1and1.com alone without the brakcets? I realize this is really an old post. but wondering if you figured it out. I have postfix working, but mdadm isn't talking to postfix...

To troubleshoot postfix from mdadm, I came across a post which reccomended telnetting into your box (localhost) port 25, and run through the typical email commands... it's kinda tricky, but good way to test continuity through email vs. the mdadm host.

telnet 127.0.0.1 25

IF everything is working, you walk through making an email from headers... 

My problem is that Mdadm just pauses after I send that command to send a test email... 

sudo mdadm  --monitor --scan --test /dev/md0 delay=3600 

just sits there... no email...

---

### Post by kennedy7 on 2008-12-03
Have you checked port forwarding on your wireless router. If you havent set it then it wont relay messages.

---

### Post by Rickolati on 2011-03-07
I realise this is a very old post, but ahve you been able to get it working.

when I look at the mail.log file I can see that it bounced back and it seems like it is due to the "from address being incorrect.

I am using gmail to send

---


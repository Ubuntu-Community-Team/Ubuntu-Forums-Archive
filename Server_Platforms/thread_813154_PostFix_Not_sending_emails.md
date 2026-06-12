---
title: "PostFix Not sending emails"
date: 2008-05-30
forum: Server Platforms
---

### Post by rock lobster on 2008-05-30
Hey everyone I have an issue with my postfix server not sending emails. The server retrieves emails no problem, but when I go to send an email it just times out. This is all being done on my other machine this is not local. I tried telneting to port 25 nada, but when I do it locally it gets there no problem. Its like its refusing remote connections. I might be missing a config some where but I am not 100% with Postfix. I am willing to send you guys any info you need at all. Oh and my ISP doesn't block the port its a business line. 


Thank you

---

### Post by Koybe on 2008-05-30
Without your conf it's gonna be hard.

First guess : Look at my_networks setting and be sure you accept your own network.

---

### Post by rock lobster on 2008-05-30
Well for starters just a little more info to help out I am using webmin to set this all up. I did check the my_network settings and that is set to default (all connected networks). I am not to sure if that helps or if we are even on the same page. I have used webmin to setup all of this.

---

### Post by volkswagner on 2008-05-31
You should post some log files for relevant information. 

/var/log/mail.err
/var/log/mail.log
/var/log/mail.info
 /var/log/auth.log

---

### Post by Monicker on 2008-05-31
It would still be good to post /etc/postfix/main.cf and /etc/postfix/master.cf, to show your postfix configuration.  Webmin would just be altering those files.

---

### Post by rock lobster on 2008-05-31
Yeah the logs don't show much they don't even show that I am trying to send mail. I do have the config files below.  

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

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = polaris.baronlabs.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = baronlabs.net
mydestination = polaris.baronlabs.net, localhost.baronlabs.net, , localhost, baronlabs.net
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
smtpd_sasl_auth_enable = yes

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
scalemail-backend unix	-	n	n	-	2	pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}


```


If the logs are totally necessary then I can attach them.

---

### Post by rock lobster on 2008-06-04
Just an update this is the message I get when I try to connect to it using telnet 

Connecting To baronlabs.net...Could not open connection to the host, on port 25:
 Connect failed


But it works internally I guess I can try changing the port at a later time, but I hope my config files look okay

---

### Post by rock lobster on 2008-06-06
Well looks like my server is working correctly there was just a DNS issue that I can address later. But there are still more pressing issues that I wanted to get some feed back on. 


I am getting loads of warning... and it wont allow me to login to the server to send emails... 


mail.warn

```
Jun  5 19:36:17 polaris postfix/smtpd[5492]: warning: unknown[192.168.1.2]: SASL LOGIN authentication failed: authentication failure
Jun  5 19:43:16 polaris postfix/smtpd[6087]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory
Jun  5 19:43:16 polaris postfix/smtpd[6087]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory
Jun  5 19:43:16 polaris postfix/smtpd[6087]: warning: SASL authentication failure: no secret in database
Jun  5 19:43:16 polaris postfix/smtpd[6087]: warning: unknown[192.168.1.2]: SASL CRAM-MD5 authentication failed: authentication failure
Jun  5 19:43:16 polaris postfix/smtpd[6087]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory
Jun  5 19:43:16 polaris postfix/smtpd[6087]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory
Jun  5 19:43:16 polaris postfix/smtpd[6087]: warning: SASL authentication failure: no secret in database
Jun  5 19:43:16 polaris postfix/smtpd[6087]: warning: unknown[192.168.1.2]: SASL NTLM authentication failed: authentication failure
Jun  5 19:43:16 polaris postfix/smtpd[6087]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory
Jun  5 19:43:16 polaris last message repeated 4 times
```

Any ideas how to correct this problem?

---

### Post by osjak on 2008-06-07
Have you setup certificates for SASL to work with? Here's a good tutorial on configuring Postfix on Ubuntu:
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

---


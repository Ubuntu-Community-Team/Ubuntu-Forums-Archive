---
title: "PHP mail() command"
date: 2012-11-22
forum: Server Platforms
---

### Post by Blind-Summit on 2012-11-22
Hello all,
I'm really having a hard time configuring mail support on my 12.04 intranet box. I have sendmail installed, but it's probably not configured properly. I then tried to follow some postfix guides but nothing seems to work.

Ubuntu is running under hyper-v alongside an MS Exchange server which can be used, if needed, to aid in sending emails out. I only need to send mails from the server (server@localhost).

The server name is (originally) "Ubuntu" and the apache host for the intranet is called "hub". The server is statically assigned 192.168.1.10 and the exchange server is on 192.168.1.6.

Here is the tail end of /var/log/mail.log

```
Nov 22 17:00:01 hub postfix/pickup[5059]: 35C1F62351: uid=0 from=<root>
Nov 22 17:00:01 hub postfix/cleanup[5132]: 35C1F62351: message-id=<20121122170001.35C1F62351@hub>
Nov 22 17:00:01 hub postfix/qmgr[5060]: 35C1F62351: from=<root@mail.topthatpublishing.com>, size=322, nrcpt=1 (queue active)
Nov 22 17:00:01 hub postfix/pickup[5059]: 4B5BC6234E: uid=0 from=<root>
Nov 22 17:00:01 hub postfix/cleanup[5132]: 4B5BC6234E: message-id=<20121122170001.4B5BC6234E@hub>
Nov 22 17:00:01 hub postfix/qmgr[5060]: 4B5BC6234E: from=<root@mail.topthatpublishing.com>, size=647, nrcpt=1 (queue active)
Nov 22 17:00:25 hub postfix/smtp[5357]: fatal: specify a password table via the `smtp_sasl_password_maps' configuration parameter
Nov 22 17:00:26 hub postfix/master[5056]: warning: process /usr/lib/postfix/smtp pid 5357 exit status 1
Nov 22 17:00:26 hub postfix/master[5056]: warning: /usr/lib/postfix/smtp: bad command startup -- throttling
Nov 22 17:01:01 hub postfix/pickup[5059]: 5EFA862356: uid=0 from=<root>
Nov 22 17:01:01 hub postfix/cleanup[5132]: 5EFA862356: message-id=<20121122170101.5EFA862356@hub>
Nov 22 17:01:01 hub postfix/qmgr[5060]: 5EFA862356: from=<root@mail.topthatpublishing.com>, size=322, nrcpt=1 (queue active)
Nov 22 17:01:01 hub postfix/pickup[5059]: 64B1262354: uid=0 from=<root>
Nov 22 17:01:01 hub postfix/cleanup[5132]: 64B1262354: message-id=<20121122170101.64B1262354@hub>
Nov 22 17:01:01 hub postfix/qmgr[5060]: 64B1262354: from=<root@mail.topthatpublishing.com>, size=647, nrcpt=1 (queue active)
Nov 22 17:01:26 hub postfix/smtp[5378]: fatal: specify a password table via the `smtp_sasl_password_maps' configuration parameter
Nov 22 17:01:27 hub postfix/master[5056]: warning: process /usr/lib/postfix/smtp pid 5378 exit status 1
Nov 22 17:01:27 hub postfix/master[5056]: warning: /usr/lib/postfix/smtp: bad command startup -- throttling
Nov 22 17:02:27 hub postfix/smtp[5380]: fatal: specify a password table via the `smtp_sasl_password_maps' configuration parameter

```

My /etc/postfix/main.cf (edited)

```
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

myhostname = hub
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = example.com, hub, localhost.localdomain, localhost
relayhost = mail.example.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.1.1/120
mailbox_command =
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtp_sasl_auth_enable = yes

```

I'd simply like to be able to call mail via CLI, but most importantly I need PHP mail() to work.

Thank you

---

### Post by spillage2 on 2012-11-22
Hi,

Might be worth looking here:
 [http://www.havetheknowhow.com/Configure-the-server/Install-ssmtp.html](http://www.havetheknowhow.com/Configure-the-server/Install-ssmtp.html)

cheers,

Spill.

---

### Post by Blind-Summit on 2012-11-23
Thanks Spill - the setup of ssmtp seems a lot easier. I tried to connect to the Exchange server, and then using my @googlemail.com address.

Exchange didn't seem to work, but the gmail redirect seemed fine.

the error was "ssmtp: Cannot open ...." and then the domain name:port. 

I tried different ports to no avail.

---

### Post by Blind-Summit on 2012-11-27
I have managed to get SSMTP to work on the command line, but the mail() command still won't send.

I had enable the IP address on my exchange server (hence the CLI working)

Anything I can do to test it? PHP returns true from the mail function!

---

### Post by Blind-Summit on 2012-11-27
Sigh,

Finally got the php mail() to work, but I can't set any headers (notably the from and reply-to fields).

I have enabled: FromLineOverride=YES but that doesn't seem to help.

---


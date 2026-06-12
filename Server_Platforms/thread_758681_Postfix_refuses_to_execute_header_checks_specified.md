---
title: "Postfix refuses to execute header checks specified"
date: 2008-04-18
forum: Server Platforms
---

### Post by 2min_noodles on 2008-04-18
Hi Guys,

:confused:

I am relatively new at Postfix, and am busy working on a special project at the moment requiring postfix and mailscanner/anything else that works nice. I found the problem that I had specified everything exactly the way I saw it on countless websites on the net, but still I cannot get my incoming mail to be moved to my hold queue for further processing.

It is a minimal config that I have, as to ensure I get the basics working, and then build it up from there, but so far I have had no luck. 

Please see the following for a listing of my main.cf file, and for my header_checks file :

****** main.cf **********
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
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = administrator-desktop
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = ***.***.com, administrator-desktop, localhost.localdomain, localhost
relayhost = 196.***.***.90
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
header_checks = regexp:/etc/postfix/header_checks
mime_header_checks = regexp:/etc/postfix/header_checks

****** header_checks : *********

/^Recieved:/ HOLD

I have set it up to accept from localhost only for now, as I am still testing and want to ensure that nothing else inside our network will talk to it, hence the mynetworks = 127.0.0.0/8. I also removed out smarthost address and domain name, since that is all correct. I checked my postfix version (2.4.5), and it does support the regexp command according to postmap -m. 

What am I missing here guys? This machine takes the mail and delivers it immediately to the smarthost, and then goes out onto the net. So I know that part works, but not the taking incoming messages and moving it into hold.

PS: This machine will act as a "SPAM" smarthost, killing selected attachments before they even exit out network, as to do better bandwidth management.

Any Ideas?

Regards,

2min_noodles

---

### Post by jpeddicord on 2008-04-18
Moved to Server Platforms; FF&H is for forum-related questions and problems.

---

### Post by 2min_noodles on 2008-04-26
Dont worry, finally found the error. Locally generated mail does NOT produce Recieved entries, nor FROM fields. When creating a message from the localhost via telnet, after you selected data mode, the following should be put there:
From: xxxx
To: xxxx
Subject: xxxx
xxxx

So, the telnet session should show something like this :

Trying xxx.xxx.xxx.xxx ....
Connected to xxx
Escape Character is '^]'
220 your box name Postfix (Ubuntu)
EHLO xxxx
250-xxxxx
*** Whole bunch more of 250's ***
mail from: sender@address
250 2.1.0 Ok
rcpt to: recipient@address
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR.<LF>
From:xxxx
To:xxxx
Subject:xxxx
your text
.
250 2.0.0 Ok: queued as xxxxxxxxxxxxx


No-where on the net did I find any mention of this, so, as I said, I am new at this, but found the solution. This is here for anyone else that made this small, and possibly stupid mistake.

---


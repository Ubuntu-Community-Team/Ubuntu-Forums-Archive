---
title: "Postfix - send mail problem"
date: 2007-10-28
forum: Server Platforms
---

### Post by satimis on 2007-10-28
Hi folks,


Ubuntu 7.04 server amd64


Just finished installing the mail server and encountered problem on testing it.  Steps performed as follows;

$ sudo useradd -m -s /bin/bash fmaster
$ sudo passwd fmaster```

Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully

```

$ telnet localhost 25```

Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
220 ubuntu.xyz.com ESMTP Postfix (Ubuntu)
ehlo localhost
250-ubuntu.xyz.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from: root@localhost
250 2.1.0 Ok
rcpt to: fmaster@localhost
451 4.3.5 Server configuration error

```
Please advise how to fix the problem. TIA


satimis

---

### Post by MJN on 2007-10-28
Post the extract of /var/log/mail.log (or .err) that shows Postfix (re)starting and/or what's happening when someone connects to send mail. Your Postfix config (main.cf) would also be useful.

Mathew

---

### Post by satimis on 2007-10-28
> **MJN said:**
> Post the extract of /var/log/mail.log (or .err) that shows Postfix (re)starting and/or what's happening when someone connects to send mail. Your Postfix config (main.cf) would also be useful.

Mathew
This was my first test.   The mail server is not in production yet.


$ tail /var/log/mail.log ```

Oct 28 09:58:26 ubuntu postfix/smtpd[5839]: connect from localhost.localdomain[127.0.0.1]
Oct 28 09:59:27 ubuntu postfix/smtpd[5839]: warning: unknown smtpd restriction: "permit_eth0"
Oct 28 09:59:27 ubuntu postfix/smtpd[5839]: NOQUEUE: reject: RCPT from localhost.localdomain[127.0.0.1]: 451 4.3.5 Server configuration error; from=<root@localhost> to=<fmaster@localhost> proto=ESMTP helo=<localhost>
Oct 28 10:04:27 ubuntu postfix/smtpd[5839]: timeout after RCPT from localhost.localdomain[127.0.0.1]
Oct 28 10:04:27 ubuntu postfix/cleanup[5850]: 24457DF0193: message-id=<20071028170427.24457DF0193@ubuntu.xyz.com>
Oct 28 10:04:27 ubuntu postfix/qmgr[4899]: 24457DF0193: from=<double-bounce@ubuntu.xyz.com>, size=981, nrcpt=1 (queue active)
Oct 28 10:04:27 ubuntu postfix/smtpd[5839]: disconnect from localhost.localdomain[127.0.0.1]
Oct 28 10:04:27 ubuntu postfix/local[5851]: warning: required alias not found: postmaster
Oct 28 10:04:27 ubuntu postfix/local[5851]: 24457DF0193: to=<postmaster@ubuntu.xyz.com>, orig_to=<postmaster>, relay=local, delay=0.02, delays=0.01/0.01/0/0, dsn=2.0.0, status=sent (discarded)
Oct 28 10:04:27 ubuntu postfix/qmgr[4899]: 24457DF0193: removed

```


$ cat /etc/postfix/main.cf ```

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
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = ubuntu.xyz.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = ubuntu.xyz.com, localhost.xyz.com, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_eth0,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
home_mailbox = Maildir/

```


B.R.
satimis

---

### Post by MJN on 2007-10-28
Two things:

i) **permit_eth0** is not a valid option for the smptd_recipient_restrictions directive. What was your intention here? You likely want to specify **permit_mynetworks** to effectively trust your LAN clients

ii) Postfix doesn't know where to send mail for postmaster to given you don't have a postmaster user. Add **postmaster: <user>** (where <user> is the user you wish to receive postmaser's mail) to /etc/aliases, run **sudo postalias /etc/aliases** and restart Postfix. Alternatively, add **luser_relay = <user>** to Postfix's main.cf to direct all such 'unknown mail' to <user> - note this will turn your domain into a catch-all domain hence <anything>@yourdomain will get delivered - this can be a spammers dream given they're in the habit of making up addresses (which in your case will get delivered to you instead of being rejected as 'address unknown').

Mathew

---

### Post by satimis on 2007-10-28
> **MJN said:**
> Two things:

i) **permit_eth0** is not a valid option for the smptd_recipient_restrictions directive. What was your intention here? You likely want to specify **permit_mynetworks** to effectively trust your LAN clients

ii) Postfix doesn't know where to send mail for postmaster to given you don't have a postmaster user. Add **postmaster: <user>** (where <user> is the user you wish to receive postmaser's mail) to /etc/aliases, run **sudo postalias /etc/aliases** and restart Postfix. Alternatively, add **luser_relay = <user>** to Postfix's main.cf to direct all such 'unknown mail' to <user> - note this will turn your domain into a catch-all domain hence <anything>@yourdomain will get delivered - this can be a spammers dream given they're in the habit of making up addresses (which in your case will get delivered to you instead of being rejected as 'address unknown').

Mathew
Thanks for your advice.


Problem solved as follows;

Edit /etc/postfix/main.cf
Changing "permit_eth0" to "permit_mynetworks"

$ sudo /etc/init.d/postfix restart```

 * Stopping Postfix Mail Transport Agent postfix                   [ OK ] 
 * Starting Postfix Mail Transport Agent postfix                         [ OK ] 

```


$ sudo iptables -F
$ telnet localhost 25```

Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
220 ubuntu.xyz.com ESMTP Postfix (Ubuntu)
ehlo localhost
250-ubuntu.xyz.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from: rootlocalhost
250 2.1.0 Ok
rcpt to: fmaster@localhost
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
      
Subject: My fist mail on Postfix

Hi
   
This is the 1st mail

Admin
.
250 2.0.0 Ok: queued as 7B2DDDF0168
quit
221 2.0.0 Bye
Connection closed by foreign host.

```


$ su - fmaster
Password: 
$ mail```

Mail version 8.1.2 01/15/2001.  Type ? for help.
"/var/mail/fmaster": 1 message 1 new
>N  1 rootlocalhost@ubu  Sun Oct 28 19:17   20/601   
& Interrupt
& quit
Held 1 message in /var/mail/fmaster
You have mail in /var/mail/fmaster

```

$ nano /var/mail/fmaster 
found the mail


B.R.
satimis

---


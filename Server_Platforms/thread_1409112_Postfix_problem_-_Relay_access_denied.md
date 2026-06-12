---
title: "Postfix problem - Relay access denied"
date: 2010-02-17
forum: Server Platforms
---

### Post by yesrno on 2010-02-17
Hi there,

A couple of days ago I tried to install Postfix and Courier to make a simple mail server on my Ubuntu 9.10 server.
Everything seemed to work fine. However I still can not figure out how to send emails to the outside world. I can however send mails to all other accounts with [EMAIL="name@domain.nl"]name@domain.nl[/EMAIL] (domain.nl is the domain for example) and also receive them. And I can also send them from my Gmail account to [EMAIL="name@domain.nl"]name@domain.nl[/EMAIL].
But the problem is, whenever I try to send them from [EMAIL="name@domain.nl"]name@domain.nl[/EMAIL] to my Gmail. I get an error:
```

The following recipient(s) haven't been reached:

   'email@gmail.com' op 17-Feb-10 1:42 PM
  554 5.7.1 <email@gmail.com>: Relay access denied
  
```I have been stuck on this for a while now and I really have no clue how to fix it, I might be just overlooking some things, no idea what though.
Here is my postfix conf:

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

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = MailServer.domain.nl
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = MailServer.domain.nl, domain.nl, localhost.domain.nl, localhost
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_protocols = all
home_mailbox = Maildir/
mailbox_command =
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
virtual_maps = hash:/etc/postfix/virtusertable
relayhost =
inet_interfaces = all

```And here is the log part when I try to send one outside.
```
Feb 17 14:06:06 MailServer imapd: Connection, ip=[::ffff:192.168.1.1]
Feb 17 14:06:06 MailServer imapd: LOGIN, user=testuser, ip=[::ffff:192.168.1.1], port=[3054], protocol=IMAP
Feb 17 14:06:06 MailServer imapd: Connection, ip=[::ffff:192.168.1.1]
Feb 17 14:06:06 MailServer imapd: LOGIN, user=testuser, ip=[::ffff:192.168.1.1], port=[3055], protocol=IMAP
Feb 17 14:07:25 MailServer imapd: LOGOUT, user=testuser, ip=[::ffff:192.168.1.1], headers=0, body=0, rcvd=218, sent=886, time=79
Feb 17 14:07:28 MailServer postfix/smtpd[4433]: connect from unknown[192.168.1.1]
Feb 17 14:07:28 MailServer postfix/smtpd[4433]: NOQUEUE: reject: RCPT from unknown[192.168.1.1]: 554 5.7.1 <email@gmail.com>: Relay access denied; from=<testuser@domain.nl> to=<email@gmail.com> proto=ESMTP helo=<CompUpstairs>
Feb 17 14:07:31 MailServer postfix/smtpd[4433]: disconnect from unknown[192.168.1.1]

```Dns settings:
Record domain.nl - Type:MX - Prio:100 - to: test.domain.nl
Record test.domain.nl - Type:A - to: server ip
That should be correct right ? Then in my email client as incoming and outgoing mailserver I enter domain.nl. Just checking.

I hope someone here can help me with my problem, I would really appreciate it. If you have any other questions just ask.
Thanks in advance,
Peter

---

### Post by jfparis on 2010-02-17
Is your server located on you DSL line ?

What you can try is to relay to the smtp of your ISP

add the following line to your conf:
```
[relayhost]("http://www.postfix.org/postconf.5.html#relayhost") = smtp.isp.com
```Also be sure that you have the authentication enabled on your email client. 

jf

---

### Post by noway2 on 2010-02-17
> Feb 17 14:07:28 MailServer postfix/smtpd[4433]: connect from unknown[192.168.1.1]
Feb 17 14:07:28 MailServer postfix/smtpd[4433]: NOQUEUE: reject: RCPT from unknown[192.168.1.1]: 554.

This looks like a reverse dns problem.  Apparently 192.168.1.1 is coming up as an unknown user and it I am guessing that isn't registering as part of my network (domain.nl) either.

BTW, if you do an nslookup on this IP address you should get the proper host name returned.

---

### Post by gombadi on 2010-02-17
> 
mynetworks = 127.0.0.0/8
mydestination = MailServer.domain.nl, domain.nl, localhost.domain.nl, localhost


The first line above tells postfix to accept email from the local machine to any where. The second line tells postfix to accept messages from other ip addresses only if it is going to one of the listed domains.
You are sending from 192.168.1.1 to gmail.com so it is being rejected.

Change /etc/postfix/main.cf to -
```

mynetworks = 127.0.0.0/8,192.168.1.0/24

```

and restart postfix and try again.

---

### Post by yesrno on 2010-02-18
Okay thanks a lot guys! I can actually send mails outside now. Really appreciate it!
One little problem tho.
I can send them outside to any other address except hotmail. When I try to send them to an hotmail.com address I get the following mail back.

```

This is the mail system at host mailserver.domain.nl.

I'm sorry to have to inform you that your message could not be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to postmaster.

If you do so, please include this problem report. You can delete your own text from the attached returned message.

                   The mail system

<email@hotmail.com>: host mx4.hotmail.com[65.55.37.72] said:
    550 DY-001 Mail rejected by Windows Live Hotmail for policy reasons. We
    generally do not accept email from dynamic IP's as they are not typically
    used to deliver unauthenticated SMTP e-mail to an Internet mail server.
    http://www.spamhaus.org maintains lists of dynamic and residential IP
    addresses. If you are not an email/network admin please contact your
    E-mail/Internet Service Provider for help. Email/network admins, please
    visit http://postmaster.live.com for email delivery information and support
    (in reply to MAIL FROM command)

```And after some searching I found the following on hotmail

> 
                  Windows Live Hotmail will not allow delivery of e-mail sent from  a domain
 where the Sender ID record was configured by the domain owner  to NOT allow ANY IP 
to send mail from that domain. Sender ID allows a  domain owner to protect domains 
that aren’t intended for sending e-mail  in order to help protect their domain from being 
spoofed. This can be  done by publishing a simple TXT record in DNS like the following 
example  (note: the organization would replace example.com with their own domain 
 and or sub-domain name):     

              example.com IN TXT “v=spf1 -all”
Could any one help me with that ? I'm a bit confused here.
Thanks,
Peter

---

### Post by yesrno on 2010-02-18
Never mind, I fixed it with by using my isp as relayhost.
Thanks again for the help. Really glad I got this finally working!

---


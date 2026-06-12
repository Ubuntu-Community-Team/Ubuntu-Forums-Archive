---
title: "Postfix/Dovecot Mail just stopped working on the 27th"
date: 2012-05-03
forum: Server Platforms
---

### Post by xefialtis on 2012-05-03
Here is the setup...
Ubuntu Server, Lucid, Postfix/Dovecot/Squirrel Mail to handle all the email. Web server, hosting 4 domains. Virtual mail to each of the domains.
Server is in a DMZ off a Linksys Router connected to Comcast...

This was all working perfectly, until the 27th of last month, when everything just stopped working at all. No mail out, no mail in.
Web pages work.
Inside the domain, mail seems to flow... but, once we go outside... boom, nothing.

Telnet: 
```

telnet myDomain.com 25
Trying 67.166.XX.XX...
Connected to myDomain.com.
Escape character is '^]'.
220 www.myDomain.com ESMTP Postfix (Ubuntu)
MAIL FROM:someBody@myDomain.com
250 2.1.0 Ok
RCPT TO:someBody@notMyDomain.com
554 5.7.1 <someBody@notMyDomain.com>: Relay access denied

```

Squirrel Mail allows access.

When I send mail in to myself from Google, I get:
```

THIS IS A WARNING MESSAGE ONLY.

YOU DO NOT NEED TO RESEND YOUR MESSAGE.

Delivery to the following recipient has been delayed:

    someBody@myDomain.com

Message will be retried for 2 more day(s)

Technical details of temporary failure:
The recipient server did not accept our requests to connect. Learn more at http://support.google.com/mail/bin/answer.py?answer=7720
[(0) myDomain.com. [67.166.XX.XX]:25: Connection timed out]
```

The LOG file says:
```

May  2 21:50:51 ds-9 postfix/smtp[12255]: connect to smtp.comcast.net[76.96.XX.XXX]:25: Connection timed out

```

the main.cf file:
```

myorigin = /etc/mailname
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
append_dot_mydomain = no
smtpd_tls_cert_file = /etc/pki/tls/certs/smtpd.crt
smtpd_tls_key_file = /etc/pki/tls/private/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
canonical_maps = hash:/etc/postfix/canonical
virtual_maps = hash:/etc/postfix/virtual
sendmail_path = /usr/sbin/sendmail
newaliases_path = /usr/bin/newaliases
mailq_path = /usr/bin/mailq
myhostname = www.myDomain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = hash:/etc/postfix/mydomains
relayhost = smtp.comcast.net
mynetworks = 127.0.0.0/8, 192.168.1.0/24
mynetworks_style = subnet
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mailbox_command = procmail -a "$EXTENSION"
inet_protocols = all
home_mailbox = Maildir/
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth-client
smtpd_sasl_auth_enable = yes
smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_unauth_destination

```

I would guess there are 2 issues here, that Telnet seems to report OK for connecting, but sending mail into my domain fails.
AND
that I can't send mail out.

I would greatly appreciate the help. This hasn't given me any problem since it was set up over 5 years ago, so I am stumped, and I have tried every solution I could find on the net...
Not to mention, it just stopped working, no "tinkering", no changes, on the 27th of last month...

Help?!

If you need any other files or information, please let me know.

---

### Post by elico on 2012-05-03
the relay access denied is fine..
have you tried from "mynetworks" like locally from the server shell?

did you upgraded anything on the server?

---

### Post by lisati on 2012-05-03
Nothing inherently wrong with the settings that I can see, beyond perhaps a need to allow for IPv6

On my server, mynetworks is defined like this:
> mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.1.0/24

---

### Post by xefialtis on 2012-05-03
> **elico said:**
> the relay access denied is fine..
have you tried from "mynetworks" like locally from the server shell?

did you upgraded anything on the server?

As part of my trouble shooting, yes, on the 27th (or even the 26th) nope.
The server continues to send me emails from things like Fail2Ban, etc. All the server logs, and other things, all from that server, keep sending email... but any time it deals with going outside the network, or coming into the network, it "fails"...
None of us have received email since the 27th, we cannot send mail out either... its frustrating.

---


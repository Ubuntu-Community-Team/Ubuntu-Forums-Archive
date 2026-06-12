---
title: "what happened here?"
date: 2011-05-01
forum: Server Platforms
---

### Post by num on 2011-05-01
I followed this guide:

[http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3)

 and installed everything, I tried sending an email to my test account that I setup and I got this error (sent via gmail)

```
Technical details of permanent failure:
Google tried to deliver your message, but it was rejected by the recipient domain. We recommend contacting the other email provider for further information about the cause of this error. The error that the other server returned was: 530 530 SMTP authentication is required. (state 14).

```

why did this happen? how to fix? please help.

---

### Post by koenn on 2011-05-01
it probably means that the mail server you set up requires authentication, and google mail doesn't know how to authenticate to it.

---

### Post by num on 2011-05-01
well yes that was pretty obvious but how do i fix it? i don't recall ever touching postfix other than to setup the domain and a user through ISPconfig nothing about authentication?

---

### Post by rubylaser on 2011-05-01
I always just use Gmail's SMTP server to bypass my ISP blocking port 25 for home use, and at work use Zimbra.  If you want to use Gmail, you need to configure Postfix to work with it. These directions work well.
[http://www.hierax.org/2009/10/using-gmail-with-postfix-on-ubuntu.html]("http://www.hierax.org/2009/10/using-gmail-with-postfix-on-ubuntu.html")

You will need to change step 2,
Bind Google's CA cert to ours.
Ubuntu already comes with the Thawte Premium Server CA cert that Google uses, so we just have to append it to our CA cert.
```
cat /etc/ssl/certs/Thawte_Premium_Server_CA.pem >> /etc/ssl/certs/cacert.pem
```
To use Equifax instead...
```
cat /etc/ssl/certs/Equifax_Secure_CA.pem >> /etc/postfix/cacert.pem
```

Other that that it should work well, and be having you sending emails through Postfix via Gmail's SMTP in no time.  This doesn't answer your original question, but I can't see anything wrong with the ISPConfig directions that would cause this problem unless something was changed or missed.

---

### Post by num on 2011-05-01
im not trying to send email through gmail's port 25, i am simply sending a message from my gmail account to my test account to see if i can send and receive email properly.

which i cannot and i get the authentication required. google gets me to shut off SASL which doesn't seem right.

I got comcast business with a static IP which they said is in the range were port 25 isn't blocked according to them.

---

### Post by num on 2011-05-01
here is my postconf

```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
body_checks = regexp:/etc/postfix/body_checks
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
content_filter = amavis:[127.0.0.1]:10024
header_checks = regexp:/etc/postfix/header_checks
html_directory = /usr/share/doc/postfix/html
inet_interfaces = all
mailbox_size_limit = 0
message_size_limit = 0
mime_header_checks = regexp:/etc/postfix/mime_header_checks
mydestination = greensevenstudios.com, localhost, localhost.localdomain
myhostname = mail.greensevenstudios.com
mynetworks = 127.0.0.0/8 [::1]/128
myorigin = /etc/mailname
nested_header_checks = regexp:/etc/postfix/nested_header_checks
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
readme_directory = /usr/share/doc/postfix
receive_override_options = no_address_mappings
recipient_delimiter = +
relay_domains = mysql:/etc/postfix/mysql-virtual_relaydomains.cf
relay_recipient_maps = mysql:/etc/postfix/mysql-virtual_relayrecipientmaps.cf
relayhost =
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_client_restrictions = check_client_access mysql:/etc/postfix/mysql-virtual_client.cf
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, check_recipient_access mysql:/etc/postfix/mysql-virtual_recipient.cf, reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sender_restrictions = check_sender_access mysql:/etc/postfix/mysql-virtual_sender.cf
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_alias_domains =
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_gid_maps = static:5000
virtual_mailbox_base = /var/vmail
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_transport = maildrop
virtual_uid_maps = static:5000

```

from my understanding is that postfix is requesting that gmail authenticate itself to send email to the server.

interestingly enough i can email others but cannot receive email nor can i email myself.

---

### Post by koenn on 2011-05-01
> **num said:**
> well yes that was pretty obvious 

since you, literally, asked "what happened here, why did this happen?", it wasn't all too clear that it was already obvious to you.

> **num said:**
> 
but how do i fix it? i don't recall ever touching postfix other than to setup the domain and a user through ISPconfig nothing about authentication?

```
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, check_recipient_access mysql:/etc/postfix/mysql-virtual_recipient.cf, reject_unauth_destination
```

I know swat about postfix, but on first sight, that line is rather restrictive as to what destinations your mail server accepts mail for.
you might want to try any or all of the following:
- check if there are valid destinations in mysql-virtual_recipient.cf and test with those, because all others will require authentication or be rejected.

- comment out that line to (temporarily) accept mail for any destination. If that works, you'll know where the problem comes from. Meanwhile, you'll be an open relay, so it's for testing only


- read postfix end/or ISPconfig documentation on how to manege destinations and authentication.


but, like I said, I do not know postfix. 

also, your SMTP server is inaccessible right now, so it's not going to receive anything. You only have imap.
If your test was to connect to an imap service, it's normal you're asked to authenticate, and everything I said about that smtpd_recipient_restrictions line, is irrelevant.

---

### Post by num on 2011-05-01
i commented it out but the issue persists.

---

### Post by num on 2011-05-02
I created two users [email]test@greensevenstudios.com[/email] and [email]postmaster@greensevenstudios.com[/email]

but after sending some test emails from my gmail account i get this error:

```
This is the mail system at host mail.greensevenstudios.com.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to postmaster.

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                  The mail system

<test@greensevenstudios.com>: unknown user: "test"

Final-Recipient: rfc822; test@greensevenstudios.com
Original-Recipient: rfc822;test@greensevenstudios.com
Action: failed
Status: 5.1.1
Diagnostic-Code: X-Postfix; unknown user: "test"
```

what's going on?

---

### Post by num on 2011-05-02
anyone?

---


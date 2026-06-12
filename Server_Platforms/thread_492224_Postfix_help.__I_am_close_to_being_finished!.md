---
title: "Postfix help.  I am close to being finished!"
date: 2007-07-04
forum: Server Platforms
---

### Post by Uranium235 on 2007-07-04
Here's what I've got going on.  I can log into an email account on Thunderbird, and I can receive email just fine.  Problem is I cannot send email.  It gives an error about the server not accepting SMPT connections.

---

### Post by Uranium235 on 2007-07-04
*bump*  c'mon guys.  I know this has to be something simple I'm not getting, and this is the only thing that's holding me back now. :)

---

### Post by bmathis on 2007-07-04
Have you tried making sure your mail client is authenticating to the smtp server first? are you able to telnet in and send a message? can you post your main.cf file. Also what tutorial are you using?

---

### Post by Uranium235 on 2007-07-04
I can telnet in just fine.  I'll post the output now:

root@ubuntu:~# telnet mail.dpit.biz 25
Trying 24.248.215.166...
Connected to dpit.biz.
Escape character is '^]'.
220 mail.dpit.biz ESMTP Postfix (Ubuntu)
ehlo dpit.biz
250-mail.dpit.biz
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

and here is my main.cf file
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

myhostname = mail.dpit.biz
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.dpit.biz, localhost.localdomain, localhost, dpit.biz
relayhost = 
mynetworks = 127.0.0.0/8, 192.168.1.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
home_mailbox = Maildir/
mailbox_command = 

I'm sure you'll probably point the problem out to me right off. :)

---

### Post by Uranium235 on 2007-07-04
Ok when I try to send mail as an end user type under thunderbird.  It prompts for a password over and over again, until you ultimately hit cancel and then you get this output:

Sending of Message failed:

The message could not be sent because connecting to the SMPT server mail.dpit.biz failed.  The server may be unavailable or refusing SMPT connections, ect.\

As far as I know I am accepting SMPT connections.  i can telnet into that port. :/

---

### Post by Uranium235 on 2007-07-04
and I cannot send a message to the outside from telnet:

root@ubuntu:~# telnet mail.dpit.biz 25
Trying 24.248.215.166...
Connected to dpit.biz.
Escape character is '^]'.
220 mail.dpit.biz ESMTP Postfix (Ubuntu)
mail to: [email]wardbl001@yahoo.com[/email]
501 5.5.4 Syntax: MAIL FROM:<address>
mail from: [email]radar@dpit.biz[/email]\
250 2.1.0 Ok
rcpt to: [email]wardbl001@yahoo.com[/email]
554 5.7.1 <wardbl001@yahoo.com>: Relay access denied

---

### Post by Uranium235 on 2007-07-04
bump

---

### Post by rsermilik on 2007-07-04
From where did you do the telnet? From the mail server or from a host sitting on the same LAN (192.168.1.0/24) as the mail server?

According to RFC1893 5.7.1 is (5) a Permanent Error, (7.1) Delivery not authorized, message refused.
Looks like you are connecting from the outside, just like your telnet shows!!!

Edit.: Looks like you are missing a line like  'smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks'

---

### Post by Uranium235 on 2007-07-04
I have that in there.

perhaps I need to take out the reject_unauth_destinations line???

---

### Post by Uranium235 on 2007-07-04
ok I took out the reject_unauth_destinations line and I went to send mail...

It no longer asks me for the password when I'm sending, but it "hangs up" when I try to send the email.

---

### Post by rsermilik on 2007-07-04
What happens if try to send a mail by telnetting to the mailserver from the mailserver?

What does your message log say?

---

### Post by Uranium235 on 2007-07-04
well in my monkeying around I have screwed something up, I'm afraid.  I can telnet in just fine, but I cannot do anything once telnetted in

---

### Post by rsermilik on 2007-07-04
Hmmm, strange, but what does your maillog says? Many times this is the best source to solve mailproblems!

To use an external client on my mailserver I also had to add
   'smtpd_sasl_authenticated_header = yes' but I can't remember why (and don't have the notes here)

---

### Post by Uranium235 on 2007-07-04
well when I do "ehlo localhost" i get no output  perhaps I need to reconfigure alltogether?

---

### Post by Uranium235 on 2007-07-04
and now for some reason my apache isn't working properly. :/

---

### Post by Uranium235 on 2007-07-04
Well everything is back up now, and I'm receiving email.  I just can't send it just yet.  any ideas?

---

### Post by Uranium235 on 2007-07-04
seems to me that the problems really start when I do the sasl authentication.

---


---
title: "Postfix Relay Access Denied Message"
date: 2006-02-03
forum: Server Platforms
---

### Post by Bigbro69 on 2006-02-03
I followed the guide at [https://wiki.ubuntu.com/Postfix](https://wiki.ubuntu.com/Postfix) to set up a postfix installation on my Ubuntu box. It works fine to receive mail, the IMAP server works etc., but whenever I try to send mail I get <theemailimsendingto@gmail.com> Relay access denied, check your email address in the settings etc.

My main.cf postfix file is as follows...
```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
inet_interfaces = all
mailbox_size_limit = 0
mydestination = mail.bigbro69.net localhost.bigbro69.net bigbro69.net localhost
mydomain = bigbro69.net
myhostname = mail.bigbro69.net
mynetworks = 10.0.0.0/24 127.0.0.0/8
mynetworks_style = subnet
myorigin = /etc/mailname
recipient_delimiter = +
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restricitons = permit_sasl_authenticated,permit_mynetwork
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = 
smtpd_sasl_security_options = noanonymous
smtpd_sender_restrictions = warn_if_reject, reject_unknown_sender_domain, permit
smtpd_tls_auth_only = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_tls_loglevel = 1
smtp_tls_note_starttls_offer = yes
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
smtp_use_tls = yes
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
```

What I want to ultimately achieve is having the mail server mail.bigbro69.net so I can access my email via IMAP whereever I am (LAN, school, etc.) and send and receive mail, although the sending isn't working... =/

---

### Post by robert_pectol on 2006-02-03
Your mailserver is protecting itself from being an open-relay and being abused.  If it were to allow you to send e-mail from any location, then what's to stop a spammer from using it as well, to propagate his spam?  A properly configured mailserver will only accept mail from local users, and incoming external mail for which it is the final destination.  If you want to be able to send mail via your mailserver from external/untrusted networks, your options for dealing with this include pop before smtp, smtp auth, Webmail interface, and various VPN or tunneling techniques.  I'd suggest a nice Webmail interface such as Squirrelmail.  We've been using it for years now and it has served us nicely.  Another approach I've used is to use ssh to establish an encrypted tunnel over which you can send your e-mails, as if you were a local user.  That has always worked out nicely as well.  Anyway, good luck with it.

---

### Post by Bigbro69 on 2006-02-03
I know I could set up something like Squirrelmail, but I'd prefer to send stuff through Thunderbird. What settings would I have to tweak to make it like my ISPs server, like, so I can send mail out if I'm authenticated as matt at my mail server?

---

### Post by robert_pectol on 2006-02-03
Again, unless you are local to the mailserver (on the same local network segment), then you won't be "trusted" by the mailserver.  The problem lies in the fact that SMTP doesn't employ username/password authentication.  POP and IMAP do, hence the ability to retrieve e-mail from "untrusted" locations.  From the mailserver's point of view, the POP or IMAP and the SMTP processes are unrelated and don't share authentication mechanisms.  It's easy for a user to think that he's authenticated to mail transfer agent (such as Postfix) by providing his username/password for mail retrieval via POP, IMAP, etc.  But they are quite unrelated.  Again, you can't authenticate yourself via username/password, to your MTA.  They don't work like that.  If you aren't local, you are untrusted and your mail will not be relayed by the MTA.  Hope that helps.

---

### Post by grupotux on 2007-02-08
Our postfix MTA has suddenly begun to deny access to internal users. The message received by users is: « 554 Relay access denied ».

Does anyone have a clue?

---

### Post by MJN on 2007-02-08
> **robert_pectol said:**
> Again, you can't authenticate yourself via username/password, to your MTA.  They don't work like that.  If you aren't local, you are untrusted and your mail will not be relayed by the MTA.  Hope that helps.

Unless you use SMTP AUTH like you mentioned.

If the OP has no joy hunting down a HowTo, or if someone else doesn't chirp in, I'll go through the process of setting this up but at the moment I'm a bit busy! :sad:

Mathew

---

### Post by kvonb on 2007-10-14
I see this is an old thread, but I will add to it just in case it helps someone else.

I was having the dreaded "relay access denied", I found that I had put the wrong "mynetworks" settings into main.cf

I had: 

```
mynetworks = 192.168.0.1, 127.0.0.1, 192.168.1.1
```It should be:

```
mynetworks = 192.168.0.0/28, 127.0.0.0/8, 192.168.1.0/28
```All works well now :)

---

### Post by MJN on 2007-10-14
Your subnet masks seem a little odd - why /28? (It's not beyond possibility but a tad unusual)

Mathew

---

### Post by kvonb on 2007-10-14
> **MJN said:**
> Your subnet masks seem a little odd - why /28? (It's not beyond possibility but a tad unusual)

Mathew

hahaha, no idea, but that's what it suggested in the error messages, so I just went with the flow and it worked :D

---

### Post by MJN on 2007-10-14
Ah, okay (at least you're honest! :))

You may as well use the following:

```
mynetworks = 127.0.0.0/8, 192.168.0.0/16
```

This identifies all loopback addresses (127.* effectively) and your entire local LAN (192.168.*).

Mathew

---

### Post by kvonb on 2007-10-15
I don't fully understand the /n notation, I seem to get it each time I read it, but then promptly forget it again :rolleyes:.

And I can't be bothered looking it up each time, so I tend to guess.

I can see the logic in your last post though, It makes sense :).

Here's how I understand the numbers correlate:

/32    /24   /16   /8
192. 168.    0.    0

I can bookmark this thread and use it as a reference each time I need it, which is not very often.

I'll tell you what, it was a blessing to get the exact solution in the mail log though, it got it spot on, no cryptic nonsense.

Well done the postfix team :guitar:

---


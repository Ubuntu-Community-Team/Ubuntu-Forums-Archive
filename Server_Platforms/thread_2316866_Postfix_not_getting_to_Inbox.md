---
title: "Postfix not getting to Inbox"
date: 2016-03-11
forum: Server Platforms
---

### Post by gonzaloP on 2016-03-11
Hi,

I set up a server with postfix and dovecot, the services work without error, but I cannot get into @gmail, @hotmail and other domains. 
From gmail I get this error:

> 
Mar 11 13:16:58 myDomain.com postfix/smtp[19843]: 652B220B5D: to=<destination@destinationDomain>, orig_to=<info@myDomain.com>, relay=alt1.aspmx.l.google.com[74.125.130.27]:25, delay=8995, delays=8992/0.03/1.9/0.51, dsn=4.2.1, status=deferred (host alt1.aspmx.l.google.com[74.125.130.27] said: 450-4.2.1 The user you are trying to contact is receiving mail at a rate that 450-4.2.1 prevents additional messages from being delivered. Please resend your 450-4.2.1 message at a later time. If the user is able to receive mail at that 450-4.2.1 time, your message will be delivered. For more information, please 450-4.2.1 visit 450 4.2.1  [https://support.google.com/mail/answer/6592](https://support.google.com/mail/answer/6592) ko9si15249735pab.187 - gsmtp (in reply to RCPT TO command))


When I try with other users I don't get to inbox and in hotmail I don't even get to spam.

I added DKIM to postfix, and the SVF record to the DNS. I also emailed [EMAIL="verifier-feedback@port25.com"]verifier-feedback@port25.com>[/EMAIL] and everything seems to be fine.

This is my postfix's configuration:

```

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
inet_interfaces = all
inet_protocols = ipv4
mailbox_size_limit = 0
milter_default_action = accept
milter_protocol = 2
mydestination = localhost
myhostname = mail.myServer.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
non_smtpd_milters = inet:localhost:12301
readme_directory = no
recipient_delimiter = +
relayhost =
smtpd_banner = $myhostname ESMTP
smtpd_milters = inet:localhost:12301
smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_path = private/auth
smtpd_sasl_type = dovecot
smtpd_tls_auth_only = yes
smtpd_tls_cert_file = /etc/ssl/certs/postfix.pem
smtpd_tls_key_file = /etc/ssl/private/postfix.key
smtpd_use_tls = yes
virtual_alias_maps = mysql:/etc/postfix/mysql-virtual-alias-maps.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual-mailbox-domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual-mailbox-maps.cf
virtual_transport = lmtp:unix:private/dovecot-lmtp

```

Any idea what it could be generating the problem that prevents the emails to be delivered to inbox?

Thanks

---

### Post by Seb_Boffen on 2016-03-11
virtual_mailbox_base = /home/directory you want to receive email in

---

### Post by gonzaloP on 2016-03-12
It is not that, I get the emails just fine, the problem is when I send them to other server. Any ideas?

---

### Post by lisati on 2016-03-12
Did you look at the [web page]("https://support.google.com/mail/answer/6592") suggested by gmail? 

By default, Postfix won't delete your outgoing mail when it receives a 4xx code, but will try sending the message later.

---

### Post by gonzaloP on 2016-03-12
Yes I read all the documentation.
The problem is that not only I am getting that problem with Gmail, I am getting it with hotmail and other servers I am tagged as spam, but I am not in any black list.
There must be something wrong with the configuration.
Any ideas?

Thanks

---

### Post by lisati on 2016-03-12
> **gonzaloP said:**
> Yes I read all the documentation.
<snip> I am tagged as spam <snip>
The gmail message you quoted doesn't mean that you are tagged as spam. It indicates that the recipient of your email is receiving a lot of email, and rather quickly. Unless you are sending them lots of message, it's probably *not* anything to do with something you have (or haven't) done. 

The best thing you can do is to make sure that you haven't changed anything in Postfix's settings that make it retry sending the message too soon.

---


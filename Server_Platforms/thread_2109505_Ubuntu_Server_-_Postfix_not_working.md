---
title: "Ubuntu Server - Postfix not working"
date: 2013-01-27
forum: Server Platforms
---

### Post by cipcaps on 2013-01-27
Hi.

For last two days I have wen't through the web searching for this problem, I have toyed lot of solutions, bet non made this proble go away.


The problem is - I(server) can't receive any mail... 

I'm able to login but when I request EXAMINE INBOX, I get `UNABLE TO OPEN THIS MAILBOX`, as I understand this error comes from the fact that folder structure has not been created for mailbox, and it will be done, once the first mail arrives. But when I try to send mail to this mailbox, I get this:

GMail:

Jan 28 01:35:47 exampleserver postfix/smtpd[3816]: connect from mail-ia0-f176.google.com[209.85.210.176]
Jan 28 01:35:48 exampleserver postfix/smtpd[3816]: NOQUEUE: reject: RCPT from mail-ia0-f176.google.com[209.85.210.176]: 554 5.7.1 <mymail@gmail.com>: Sender address rejected: Access denied; from=<mymail@gmail.com> to=<target@example.com> proto=ESMTP helo=<mail-ia0-f176.google.com>
Jan 28 01:35:48 exampleserver postfix/smtpd[3816]: disconnect from mail-ia0-f176.google.com[209.85.210.176]


Hotmail:

Jan 28 01:23:48 exampleserver postfix/smtpd[2750]: connect from dub0-omc2-s36.dub0.hotmail.com[157.55.1.175]
Jan 28 01:23:48 exampleserver postfix/smtpd[2750]: NOQUEUE: reject: RCPT from dub0-omc2-s36.dub0.hotmail.com[157.55.1.175]: 554 5.7.1 <mymail@hotmail.com>: Sender address rejected: Access denied; from=<mymail@hotmail.com> to=<target@example.com> proto=ESMTP helo=<dub0-omc2-s36.dub0.hotmail.com>
Jan 28 01:23:48 exampleserver postfix/smtpd[2750]: disconnect from dub0-omc2-s36.dub0.hotmail.com[157.55.1.175]


iCloud:

Jan 28 00:42:45 exampleserver postfix/smtpd[4344]: connect from st11p05mm-asmtp002.mac.com[17.172.108.237]
Jan 28 00:42:45 exampleserver postfix/smtpd[4344]: NOQUEUE: reject: RCPT from st11p05mm-asmtp002.mac.com[17.172.108.237]: 554 5.7.1 <mymail@icloud.com>: Sender address rejected: Access denied; from=<mymail@icloud.com> to=<target@example.com> proto=ESMTP helo=<st11p05mm-asmtp002.mac.com>
Jan 28 00:42:46 exampleserver postfix/smtpd[4344]: disconnect from st11p05mm-asmtp002.mac.com[17.172.108.237]



**postconf -n**

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
content_filter = amavis:[127.0.0.1]:10024
disable_vrfy_command = yes
inet_interfaces = all
mailbox_size_limit = 0
message_size_limit = 0
mydestination =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mynetworks_style = host
myorigin = /etc/mailname
readme_directory = no
receive_override_options = no_address_mappings
recipient_delimiter = +
relayhost =
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name
smtpd_delay_reject = yes
smtpd_helo_required = yes
smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks, reject
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject
smtpd_tls_cert_file = /etc/ssl/private/mailcert.crt
smtpd_tls_key_file = /etc/ssl/private/mailcert.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
virtual_alias_maps = mysql:/etc/postfix/maps/alias.cf
virtual_gid_maps = static:5000
virtual_mailbox_base = /virtual/mail
virtual_mailbox_domains = mysql:/etc/postfix/maps/domain.cf
virtual_mailbox_limit = 0
virtual_mailbox_maps = mysql:/etc/postfix/maps/user.cf
virtual_uid_maps = static:5000

If some can help I will truly appreciate it.

Thanks!

---

### Post by cesar98026 on 2013-01-27
I think it has something to do with smpd_recipient_restrictions.... On my fully working server, I have this:
```
 
smtpd_recipient_restrictions =
permit_sasl_authenticated,
reject_unauth_pipelining,
permit_mynetworks,
reject_non_fqdn_recipient,
reject_unknown_recipient_domain,
reject_unauth_destination,
permit

```
;)
Or you could maybe remove smtpd_recipient_restrictions and see what happens

---

### Post by cipcaps on 2013-01-28
Hi.

Yea!! It works, but only when I add You line(thank you very much) remove the `smtpd_sender_restrictions`, can You give me any advice on this setting too?

---


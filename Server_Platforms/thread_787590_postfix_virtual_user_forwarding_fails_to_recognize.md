---
title: "postfix virtual user forwarding fails to recognize users"
date: 2008-05-09
forum: Server Platforms
---

### Post by SuperCzar on 2008-05-09
I have a personal email server configured on Hardy, and it works fine for real users both sending and receiving email.

But I have several addresses that I intend to use as forwards to other emails and forwarding is completely broken. 

I have configured my system according to this guide (with small modifications):
[http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10](http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10)

Here is my /etc/postfix/main.cf
```
myorigin = /etc/mailname
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
append_dot_mydomain = no
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
myhostname = mail.thirdrate.info
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhost, localhost.localdomain
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_helo_restrictions = permit_mynetworks, permit_sasl_authenticated
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_create_maildirsize = yes
virtual_mailbox_extended = yes
virtual_mailbox_limit_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = "The user you are trying to reach is over quota."
virtual_overquota_bounce = yes
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
receive_override_options = no_address_mappings
readme_directory = /usr/share/doc/postfix
html_directory = /usr/share/doc/postfix/html

```

and here is the mysql-virtual_forwardings.cf that is referred to:
```
user = [mail_admin]
password = [password]
dbname = mail
query = SELECT destination FROM forwardings WHERE source='%s'
hosts = 127.0.0.1

```

The sql username and password are correct in the file, and the table is populated correctly but when I send an email to the address I get the following error:
```
postfix/virtual[4816]: F132150078: to=<admin@[example.com]>, relay=virtual, delay=0.12, delays=0.1/0/0/0.02, dsn=5.1.1, status=undeliverable (unknown user: "admin@[example.com]")

```

Note: items in square brackets [] have been intentionally changed for posting.

---

### Post by SuperCzar on 2008-05-27
here's the error logs if that would help anyone.

```
May 27 22:18:50 [hostname] postfix/virtual[14250]: DABA8500CD: to=<abuse@[mydomain.com]>, relay=virtual, delay=0.77, delays=0.6/0/0/0.17, dsn=5.1.1, status=bounced (unknown user: "abuse@[mydomain.com]")
May 27 22:18:50 [hostname] postfix/cleanup[14245]: 48C605008C: message-id=<20080527221850.48C605008C@mail.[mydomain.com]>
May 27 22:18:50 [hostname] postfix/bounce[14251]: DABA8500CD: sender non-delivery notification: 48C605008C

```

---

### Post by SuperCzar on 2008-05-28
On a whim I tried changing the source and destination email addresses to see if I was misinterpreting the meaning of "source" and "destination". 

I got different errors.

When I have the email address I am sending the email to in the "source" column, and the email address I want the message forwarded to in the "destination" column, I get the following bounce message:
```
<abuse@thirdrate.info>: unknown user: "abuse@thirdrate.info"
Reporting-MTA: dns; thirdrate.info
```

and the following error in mail.log:
```
May 28 20:47:28 thirdrate postfix/virtual[19188]: 0D081500CE: to=<abuse@thirdrate.info>, relay=virtual, delay=0.39, delays=0.18/0.01/0/0.2, dsn=5.1.1, status=bounced (unknown user: "abuse@thirdrate.info")
```

When I have them reversed I get the following bounce message:
```
<abuse@thirdrate.info>: host mail.thirdrate.info[208.75.84.164] said: 550 5.1.1
   <abuse@thirdrate.info>: Recipient address rejected: User unknown in virtual
   mailbox table (in reply to RCPT TO command)
```

and the following error in mail.log:
```
May 28 20:46:30 thirdrate postfix/smtpd[19177]: NOQUEUE: reject: RCPT from [external smtp server]: 550 5.1.1 <abuse@thirdrate.info>: Recipient address rejected: User unknown in virtual mailbox table; from=<[external email address]> to=<abuse@thirdrate.info> proto=ESMTP helo=<[external smtp server]>
```

Does this information help?

---

### Post by SuperCzar on 2008-05-29
The problem was simple.

In /etc/postfix/main.cf I had the following line:
```
receive_override_options = no_address_mappings
```

I commented that out, and all is now well. I'm not certain how that line got in there, if it was part of the default install, or if I made a mistake and added it based on the multiple tutorials I was reviewing.

---

### Post by MJN on 2008-05-29
If it's any help for the future you can run **postconf -d** to show the Postfix defaults (and **-n** gives you just the directives that you've changed from default).

Mathew

---

### Post by acqu13sce on 2009-05-26
I was experiencing the same issue on a Debian 4 server and your suggestion solved it for me too.

I can only imagine that the line was merged into the main.cf file during an update since it's not something that I would add myself, I should probably pay more attention to the diffs when updating, oops.

Thanks

---


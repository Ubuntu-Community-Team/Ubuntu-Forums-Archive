---
title: "Postfix loops back to myself"
date: 2011-10-11
forum: Server Platforms
---

### Post by balagosa on 2011-10-11
below is my postconf -n```
alias_maps = hash:/etc/aliases
command_directory = /usr/sbin
config_directory = /etc/postfix
daemon_directory = /usr/libexec/postfix
debug_peer_level = 2
disable_dns_lookups = no
disable_vrfy_command = yes
header_checks = regexp:/etc/postfix/header_checks
html_directory = no
inet_interfaces = all
mail_owner = postfix
mailbox_size_limit = 500000000
mailq_path = /usr/bin/mailq.postfix
manpage_directory = /usr/share/man
message_size_limit = 50000000
mydestination = localhost.$mydomain, localhost.localdomain, localhost
mydomain = jinisyssoftware.com
mynetworks = 10.0.10.200, 192.168.100.0/24, 127.0.0.1
newaliases_path = /usr/bin/newaliases.postfix
queue_directory = /var/spool/postfix
readme_directory = /usr/share/doc/postfix-2.3.3/README_FILES
relay_domains = jinisyssoftware.com
relay_recipient_maps = hash:/etc/postfix/recipients
sample_directory = /usr/share/doc/postfix-2.3.3/samples
sendmail_path = /usr/sbin/sendmail.postfix
setgid_group = postdrop
smtp_host_lookup = dns, native
smtp_sasl_auth_enable = no
smtpd_delay_reject = yes
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, reject_invalid_hostname, regexp:/etc/postfix/helo.regexp, permit
smtpd_recipient_restrictions = check_client_access hash:/etc/postfix/helo_client_exceptions    check_sender_access hash:/etc/postfix/recipients,   check_sender_access hash:/etc/postfix/restricted_senders,   reject_unknown_sender_domain,   reject_unknown_recipient_domain,   permit_mynetworks,   reject_unauth_destination,   check_client_access hash:/etc/postfix/rbl_client_exceptions,   reject_rbl_client cbl.abuseat.org,   reject_rbl_client sbl-xbl.spamhaus.org,   reject_rbl_client bl.spamcop.net,   reject_rhsbl_sender dsn.rfc-ignorant.org,   permit
smtpd_restriction_classes = local_only
smtpd_sasl_auth_enable = no
strict_rfc821_envelopes = yes
transport_maps = hash:/etc/postfix/transport
unknown_address_reject_code = 554
unknown_local_recipient_reject_code = 550

```

Below is my maillog ```
[COLOR="Red"]Oct 12 11:31:28 mail postfix/smtp[27060]: C5AECF0483: to=<dbalagosa@jinisyssoftware.com>, relay=cbuchidc00.jinisyssoftware.com[222.127.117.234]:25, delay=0.02, delays=0.01/0/0.01/0, dsn=5.4.6, status=bounced (mail for cbuchidc00.jinisyssoftware.com loops back to myself)[/color]
Oct 12 11:31:28 mail postfix/qmgr[26945]: C5AECF0483: removed
Oct 12 11:31:28 mail postfix/smtpd[27040]: disconnect from unknown[10.0.10.254]
Oct 12 11:31:29 mail postfix/smtp[27059]: 370C3F0480: to=<daniel_gelie@yahoo.com>, relay=mta7.am0.yahoodns.net[66.94.237.139]:25, delay=5.6, delays=2.5/0.01/0.8/2.2, dsn=2.0.0, status=sent (250 ok dirdel)
Oct 12 11:31:29 mail postfix/qmgr[26945]: 370C3F0480: removed
Oct 12 11:31:41 mail postfix/master[26518]: warning: process /usr/libexec/postfix/pickup pid 27064 killed by signal 11
Oct 12 11:31:41 mail postfix/master[26518]: warning: /usr/libexec/postfix/pickup: bad command startup -- throttling

```

Below is my /etc/hosts
```
10.0.10.200     mail.jinisyssoftware.com mail jinisyssoftware.com
127.0.0.1       mail.jinisyssoftware.com mail localhost.localdomain     localhost
[COLOR="Red"]192.168.100.221         cbuchidc00.jinisyssoftware.com cbuchidc00[/color]

```

---

### Post by balagosa on 2011-10-12
items I highlight in Red are important factors; methinks.

As you can see in my maillogs, it is looking for cbuchidc00 with IP address 222.127.117.234 BUT the IP address is wrong. As declared in my /etc/hosts/ the cbuchidc00 should have an IP address of 192.168.100.221

---

### Post by lisati on 2011-10-12
The IP address 222.127.117.234 appears to be your public IP address, and 192.168.100.221 is the IP address internal to your network.

One solution will be to include cbuchidc00.jinisyssoftware.com in the list defined for postfix's "mydestination", so that Postfix knows that the email is intended for local delivery.

---

### Post by balagosa on 2011-10-12
[color="Red"]mydestination = localhost.$mydomain, localhost.localdomain, localhost[/color]

As listed in my postconf -n, it is intended for localhost. mydestination does not list any public IP. Is it important to indicate the EXACT hostname of my mail server?

Additional NOTE:

This was working before but I changed my DNS configuration specifically my MX records and then this happened.

A and MX records below
mail.jinisyssoftware.com 	86400 	IN 	A 	222.127.117.234

jinisyssoftware.com 	86400 	IN 	MX 	10 mail.jinisyssoftware.com

---

### Post by lisati on 2011-10-12
The only time I have had the exact same error message in Postfix is when I have omitted the exact hostname from the mydestination list.

---

### Post by balagosa on 2011-10-12
> **lisati said:**
> The only time I have had the exact same error message in Postfix is when I have omitted the exact hostname from the mydestination list.

will try that one. Appending the hostname at the end of my destinations

Edit:
still nothing. I dont understand why from my maillog [color="red"]relay=Public IP with same hostname[/color]

---

### Post by lisati on 2011-10-12
Did you remember to restart Postfix?

---

### Post by balagosa on 2011-10-12
> **lisati said:**
> Did you remember to restart Postfix?

ofcourse I did. I always do. Another error surfaced with that change though

```
 NOQUEUE: reject: RCPT from nm40-vm0.bullet.mail.ne1.yahoo.com[98.138.229.176]: 554 5.7.1 <dbalagosa@jinisyssoftware.com>: Relay access denied; from=<daniel_gelie@yahoo.com> to=<dbalagosa@jinisyssoftware.com> proto=SMTP helo=<nm40-vm0.bullet.mail.ne1.yahoo.com>

```

---

### Post by balagosa on 2011-10-12
Update:

when adding ```
disable_dns_lookups = yes
```

the above error of loops back are eliminated BUT yahoomail is bouncing my emails as a result.

Which leads to my 2nd question of is "relayhost" option important?

Because My in is suppose to be relay also my out. But as a consequence of using disable dns, my email are bouncing. So I thought of not using a relay going outside.

---

### Post by balagosa on 2011-10-12
up up

Any help appreciated guys.

---

### Post by balagosa on 2011-10-13
no hope? :confused:

---

### Post by cloudkicker on 2012-11-25
[http://forum.linode.com/viewtopic.php?t=8400](http://forum.linode.com/viewtopic.php?t=8400)

kind of late... but anyways, for those that have the same problem, this helped me!

---


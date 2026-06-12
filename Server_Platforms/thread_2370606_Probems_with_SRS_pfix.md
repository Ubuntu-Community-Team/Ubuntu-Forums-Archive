---
title: "Probems with SRS pfix"
date: 2017-09-05
forum: Server Platforms
---

### Post by dalbjerg on 2017-09-05
Hi
I have installed ubuntu, and the package mailutils, following this guide:
[https://www.ameir.net/blog/archives/71-installing-srs-extensions-on-postfix-ubuntudebian.html](https://www.ameir.net/blog/archives/71-installing-srs-extensions-on-postfix-ubuntudebian.html)

to setup SRS on postfix.

But something is wrong.
When i send a mail that is forwarded, i can see in the log that SRS is handling the mail, but when it arrive in my mailbox on the other system, there are nothing about the SRS email address.

Config:
**main.cf**
virtual_alias_domains = f-f-f.dk fff-mail01.cust.itafdelingen.net
virtual_alias_maps = hash:/etc/postfix/virtual
recipient_canonical_maps = hash:/etc/postfix/pfix-no-srs.cf, tcp:127.0.0.1:10002
recipient_canonical_classes = envelope_recipient
sender_canonical_maps = hash:/etc/postfix/pfix-no-srs.cf, tcp:127.0.0.1:10001
sender_canonical_classes = envelope_sender

**/etc/default/postsrsd**
# Default settings for postsrsd

# Local domain name.
# Addresses are rewritten to originate from this domain. The default value
# is taken from `postconf -h mydomain` and probably okay.
#
SRS_DOMAIN=srs.fff-mail01.cust.dalbjerg.nu

# Exclude additional domains.
# You may list domains which shall not be subjected to address rewriting.
# If a domain name starts with a dot, it matches all subdomains, but not
# the domain itself. Separate multiple domains by space or comma.
#
#SRS_EXCLUDE_DOMAINS=.example.com,example.org

# Secret key to sign rewritten addresses.
# When postsrsd is installed for the first time, a random secret is generated
# and stored in /etc/postsrsd.secret. For most installations, that's just fine.
#
SRS_SECRET=/etc/postsrsd.secret

# Local ports for TCP list.
# These ports are used to bind the TCP list for postfix. If you change
# these, you have to modify the postfix settings accordingly. The ports
# are bound to the loopback interface, and should never be exposed on
# the internet.
#
SRS_FORWARD_PORT=10001
SRS_REVERSE_PORT=10002

# Drop root privileges and run as another user after initialization.
# This is highly recommended as postsrsd handles untrusted input.
#
RUN_AS=nobody

# Jail daemon in chroot environment
CHROOT=/var/lib/postsrsd

**/etc/postfix/virtual**
[email]bestyrelsen@fff-mail01.cust.dalbjerg.nu[/email] [email]XXXX@XXXX.dk[/email]

In postfix log:
Sep  5 15:06:56 F-F-F-Mail01 postfix/smtpd[18111]: connect from smtp150.smtp.dalbjerg.nu[178.XXX.XXX.XXX]
Sep  5 15:06:56 F-F-F-Mail01 postfix/smtpd[18111]: EF7D7FFCE1: client=smtp150.smtp.dalbjerg.nu[178.XXX.XXX.XXX]
Sep  5 15:06:56 F-F-F-Mail01 postfix/cleanup[18114]: EF7D7FFCE1: message-id=<b4e85d5c8ac348cd9ae73c56507d543e@ITA-EXCH02.XXXXX.local>
Sep  5 15:06:57 F-F-F-Mail01 postfix/qmgr[18093]: EF7D7FFCE1: from=<SRS0=XXXX=AG=dalbjerg.nu=XXX@fff-mail01.cust.dalbjerg.nu>, size=102848, nrcpt=1 (queue active)
Sep  5 15:06:57 F-F-F-Mail01 postfix/smtpd[18111]: disconnect from smtp150.smtp.dalbjerg.nu[178.XXX.XXX.XXX] helo=1 mail=1 rcpt=1 data=1 quit=1 commands=5
Sep  5 15:06:57 F-F-F-Mail01 postfix/smtp[18115]: EF7D7FFCE1: enabling PIX workarounds: disable_esmtp delay_dotcrlf for mx01.dalbjerg.nu[178.XXX.XXX.XXX]:25
Sep  5 15:06:57 F-F-F-Mail01 postfix/smtp[18115]: EF7D7FFCE1: to=<XXXX@XXXX.dk>, orig_to=<bestyrelsen@fff-mail01.cust.dalbjerg.nu>, relay=mx01.dalbjerg.nu[178.XXX.XXX.XXX]:25, delay=0.37, delays=0.05/0.01/0.05/0.26, dsn=$
Sep  5 15:06:57 F-F-F-Mail01 postfix/qmgr[18093]: EF7D7FFCE1: removed
Sep  5 15:10:17 F-F-F-Mail01 postfix/anvil[18105]: statistics: max connection rate 1/60s for (smtp:178.XXX.XXX.XXX) at Sep  5 15:03:07
Sep  5 15:10:17 F-F-F-Mail01 postfix/anvil[18105]: statistics: max connection count 1 for (smtp:178.XXX.XXX.XXX) at Sep  5 15:03:07
Sep  5 15:10:17 F-F-F-Mail01 postfix/anvil[18105]: statistics: max cache size 2 at Sep  5 15:03:42

But when the email arrive at [email]XXXX@XXXX.dk[/email], it is comming from the orginal mail address.

can anyone help me with what i'm doing wrong

---


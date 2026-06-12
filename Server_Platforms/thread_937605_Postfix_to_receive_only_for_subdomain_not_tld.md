---
title: "Postfix to receive only for subdomain not tld"
date: 2008-10-04
forum: Server Platforms
---

### Post by boothefoxx on 2008-10-04
I'm running Ubuntu 8.04 on my server and the problem is that it tries to receive mail not only for subdomain (i.e. test.domain.org) but also for the top level domain (i.e. domain.org) 

The config file looks like this:
--------------
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = $mydomain
mydestination = $myhostname localhost localhost.$mydomain $mydomain
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
virtual_alias_maps = hash:/etc/postfix/virtual
smtpd_recipient_restrictions = permit_mynetworks,permit_sasl_authenticated,reject_unauth_destination
smtpd_helo_required = yes
mailbox_command = /usr/bin/procmail
smtpd_client_restrictions = permit_mynetworks  permit 
...
myhostname = smtp.domain.org
--------------

i recon it's somehow related to the $mydomain parameter because when i remove it from mydestination it sends mail for the tld to the right machine, but then again it doesn't receive mail for other tlds (virtual domains) on this machine.

What have i missed ?

---


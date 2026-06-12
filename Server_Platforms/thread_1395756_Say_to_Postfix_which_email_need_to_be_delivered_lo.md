---
title: "Say to Postfix which email need to be delivered locally based on the email address"
date: 2010-02-01
forum: Server Platforms
---

### Post by voltron81 on 2010-02-01
Hello to everybody,

I'm configuring a postfix server connected on internet with a slow dial-up connection. (I've followed this howto: [http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-debian-lenny](http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-debian-lenny))
Basically I want to hold all emails to be sent (I'll send them manually when I want), plus I want to relay all the emails to different smtp servers (depends of the email).
The configuration that I've is like that:

virtual_alias_domains =
virtual_alias_maps =
proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf,
mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
sender_dependent_relayhost_maps = hash:/etc/postfix/bysenderrelay

With this configuration I'm able to say to the system which email is internal (so delivered locally). With bysenderrelay I can setup the smtp server for every email.
The problem is that if, for example, I've a gmail account as local email and I want to send an email to another gmail account(external), postfix match in mail_domain that gmail.com is a local domain and try to send that email locally...

How to say to postfix which email must be delivered locally based on the full email name and not just based on the domain?

I guess I will need something like relay_domains, but for the user. So that, if it not a local email, the bysenderrelay will tell to postfix where to relay the email...

Any suggestion?

---


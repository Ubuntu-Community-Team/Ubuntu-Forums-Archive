---
title: "two postfix-servers working together?"
date: 2011-08-25
forum: Server Platforms
---

### Post by onineko on 2011-08-25
Hello!

I´m trying to set up postfix to work in the following szenario:
two servers, one called cleany, one called maily.
cleany is supposed to scan the mails delivered from the internet via greylisting, spamassassin, amavis..., it should also check if the adress to which the mail should be delivered exists (via mysql).
Then cleany should send the mails to maily, where the postfix accepts only mails from cleany and then delivers them to e.g. dovecot.

Users interact only with maily, so when they want to send a mail, they do that on maily, who then sends the mails to cleany, who checks them as well, before sending them off into the internet.

viewed from the internet, the mails are sent directly to and from cleany (it has a dns-name).

do i have to use multiple instances of postfix or can this work with one postfix-instance on each server?

I used this tutorial [http://www.postfix.org/MULTI_INSTANCE_README.html](http://www.postfix.org/MULTI_INSTANCE_README.html) but got stuck somewhere in the postfix-out configuration, because I wasn´t sure, how to change it to work with my 2-server modell. Also, i changed the "default"-instance , in order to get it to deliver the local mails (local as in on the machine).

the main.cf of the default-instance is currently:
-----------------------------------
myhostname = cleany
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases

myorigin = /etc/mailname
mydestination = localhost.localdomain, localhost, cleany, cleany.mydomain.org
relayhost =

mynetworks = 127.0.0.1
mynetworks_style = host

mail_spool_directory = /var/mail/
mailbox_size_limit = 0

recipient_delimiter = +
inet_interfaces = loopback-only
default_transport = error: Local delivery only!
----------------------------

that would quite certainly also work on maily. But I am somewhat stumped if i really need multiple instances on both servers and either way, exactly how I should configure them. I´m guessing, that maily might need only one instance, as its only supposed to interact with cleany (and itself for local mails)? Any help would be much appreciated.

The point of this setup is, that there is often very much spam and virus-mails incoming, which then eats up performance on the mailserver, occasionally actually leading to a system-freeze..=/

---


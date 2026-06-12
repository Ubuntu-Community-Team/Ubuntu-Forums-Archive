---
title: "Postfix drama"
date: 2011-07-30
forum: Server Platforms
---

### Post by Aquachip on 2011-07-30
I run a Windows based e-mail server and looking at moving my new server to Ubuntu, however, this following problem might stop that, so I am hoping someone can help me out - I cannot receive mail.


I have installed 'postfix' via Synaptic Package Manager.
During installation, I was to choose a general type of mail configuration. I select "Internet Site" as this is what it is.
I was then asked to input a system mail name. I used my IPv4 address (I will be hosting multiple domains).

In accordance with official documentation at [http://www.postfix.org/VIRTUAL_README.html#virtual_mailbox](http://www.postfix.org/VIRTUAL_README.html#virtual_mailbox), I performed the following:

Added to /etc/postfix/main.cf:
> virtual_mailbox_domains = domain1.com
virtual_mailbox_base = /var/mail/vhosts
virtual_mailbox_maps = hash:/etc/postfix/vmailbox
virtual_minimum_uid = 100
virtual_uid_maps = static:5000
virtual_gui_maps = static:5000
virtual_alias_maps = hash:/etc/postfix/virtual

Added to /etc/postfix/vmailbox:
> [email]name1@domain1.com[/email] domain1.com/name1
[email]name2@domain2.com[/email] domain2.com/name2

Added to /etc/postfix/virtual
> [email]postmaster@domain1.com[/email] postmaster

Executed at shell:
> postmap /etc/postfix/virtual
postmap /etc/postfix/vmailbox
postfix reload

I then sent myself an e-mail from an external server but did not receive the mail and was reported the following issues in log files:

mail.info:
> Jul 30 04:13:35 n-desktop postfix/smtpd[1767]: connect from bay0-omc3-s6.bay0.hotmail.com[65.54.190.144]
Jul 30 04:13:36 n-desktop postfix/smtpd[1767]: 4301120099C: client=bay0-omc3-s6.bay0.hotmail.com[65.54.190.144]
Jul 30 04:13:36 n-desktop postfix/cleanup[1785]: 4301120099C: message-id=<BAY152-W44EC028D90D70E4B45669AC9370@phx.gbl>
Jul 30 04:13:36 n-desktop postfix/qmgr[1757]: 4301120099C: from=<someone1243@hotmail.com>, size=1373, nrcpt=1 (queue active)
Jul 30 04:13:36 n-desktop postfix/virtual[1786]: warning: recipient [email]name1@domain1.com[/email]: not found in virtual_gid_maps
Jul 30 04:13:36 n-desktop postfix/virtual[1786]: 4301120099C: to=<name1@domain1.com>, relay=virtual, delay=0.9, delays=0.81/0/0/0.09, dsn=4.3.5, status=deferred (mail system configuration error)
Jul 30 04:13:37 n-desktop postfix/smtpd[1767]: disconnect from bay0-omc3-s6.bay0.hotmail.com[65.54.190.144]

mail.log:
> Jul 30 04:13:35 n-desktop postfix/smtpd[1767]: connect from bay0-omc3-s6.bay0.hotmail.com[65.54.190.144]
Jul 30 04:13:36 n-desktop postfix/smtpd[1767]: 4301120099C: client=bay0-omc3-s6.bay0.hotmail.com[65.54.190.144]
Jul 30 04:13:36 n-desktop postfix/cleanup[1785]: 4301120099C: message-id=<BAY152-W44EC028D90D70E4B45669AC9370@phx.gbl>
Jul 30 04:13:36 n-desktop postfix/qmgr[1757]: 4301120099C: from=<someone1243@hotmail.com>, size=1373, nrcpt=1 (queue active)
Jul 30 04:13:36 n-desktop postfix/virtual[1786]: warning: recipient [email]name1@domain1.com[/email]: not found in virtual_gid_maps
Jul 30 04:13:36 n-desktop postfix/virtual[1786]: 4301120099C: to=<name1@domain1.com>, relay=virtual, delay=0.9, delays=0.81/0/0/0.09, dsn=4.3.5, status=deferred (mail system configuration error)
Jul 30 04:13:37 n-desktop postfix/smtpd[1767]: disconnect from bay0-omc3-s6.bay0.hotmail.com[65.54.190.144]

mail.warn:
> Jul 30 04:13:36 n-desktop postfix/virtual[1786]: warning: recipient [email]name1@domain1.com[/email]: not found in virtual_gid_maps


I followed all official instructons, but dramas. What could the issue be? Whats virtual_gid_maps? Any help would be appreciated!

Kind regards.

---

### Post by kwamaking on 2011-07-30
I hope this helps some, I'm still pretty new with Linux Email, I more or less get lucky but fortunately Ubuntu has great documentation:

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

I use Dovecot as well for SASL/PAM authentication.  I recommend using Maildir's for small amounts of users, but anything bigger and you may want to seek alternative methods as your home folder would become quite cumbersome. :P

---


---
title: "mails sent from mails server running postfix are not recieved"
date: 2016-03-15
forum: Server Platforms
---

### Post by lukas34 on 2016-03-15
Hi!
I installed & configured roundcube on my server running Ubuntu 14.04. 
When I send an eMail, "sent succesfully" pops up but I dont recieve it with my other mail-account, not hosted on that server.
mail.log:```
Mar 15 11:36:42 Ubuntu-1404-trusty-64-minimal dovecot: imap-login: Login: user=<lukas.mueller@marketstrategy.de>, method=PLAIN, rip=136.243.54.13, lip=136.243.54.13, mpid=9595, secured, session=<kQcf+RMu1QCI8zYN>
Mar 15 11:36:42 Ubuntu-1404-trusty-64-minimal dovecot: imap(lukas.mueller@marketstrategy.de): Disconnected: Logged out in=32 out=449
Mar 15 11:36:42 Ubuntu-1404-trusty-64-minimal dovecot: imap-login: Login: user=<lukas.mueller@marketstrategy.de>, method=PLAIN, rip=136.243.54.13, lip=136.243.54.13, mpid=9597, secured, session=<DRAk+RMu1wCI8zYN>
Mar 15 11:36:42 Ubuntu-1404-trusty-64-minimal dovecot: imap(lukas.mueller@marketstrategy.de): Disconnected: Logged out in=44 out=573
Mar 15 11:36:50 Ubuntu-1404-trusty-64-minimal postfix/pickup[9590]: F020E46097C: uid=33 from=<lukas.mueller@marketstrategy.de>
Mar 15 11:36:50 Ubuntu-1404-trusty-64-minimal postfix/cleanup[9601]: F020E46097C: message-id=<84b4607b6ea581bffb0f935b8f2f3ba8@marketstrategy.de>
Mar 15 11:36:51 Ubuntu-1404-trusty-64-minimal dovecot: imap-login: Login: user=<lukas.mueller@marketstrategy.de>, method=PLAIN, rip=136.243.54.13, lip=136.243.54.13, mpid=9605, secured, session=<e5Si+RMu2ACI8zYN>
Mar 15 11:36:51 Ubuntu-1404-trusty-64-minimal postfix/qmgr[9591]: F020E46097C: from=<lukas.mueller@marketstrategy.de>, size=560, nrcpt=1 (queue active)
Mar 15 11:36:51 Ubuntu-1404-trusty-64-minimal postfix/smtp[9607]: F020E46097C: to=<luggie@gmx.net>, relay=mx00.emig.gmx.net[212.227.15.9]:25, delay=0.17, delays=0.1/0.01/0.05/0, dsn=5.0.0, status=bounced (host mx00.emig.gmx.net[212.227.15.9] refused to talk to me: 550-Requested action not taken: mailbox unavailable 550-Reject due to policy restrictions. 550 For explanation visit http://postmaster.gmx.com/en/error-messages?ip=136.243.54.13&c=poli)
Mar 15 11:36:51 Ubuntu-1404-trusty-64-minimal postfix/cleanup[9601]: 2DE5B46097A: message-id=<20160315103651.2DE5B46097A@Ubuntu-1404-trusty-64-minimal.localdomain>
Mar 15 11:36:51 Ubuntu-1404-trusty-64-minimal dovecot: imap(lukas.mueller@marketstrategy.de): Disconnected: Logged out in=466 out=568
Mar 15 11:36:51 Ubuntu-1404-trusty-64-minimal postfix/bounce[9608]: F020E46097C: sender non-delivery notification: 2DE5B46097A
Mar 15 11:36:51 Ubuntu-1404-trusty-64-minimal postfix/qmgr[9591]: 2DE5B46097A: from=<>, size=2992, nrcpt=1 (queue active)
Mar 15 11:36:51 Ubuntu-1404-trusty-64-minimal postfix/qmgr[9591]: F020E46097C: removed
Mar 15 11:36:51 Ubuntu-1404-trusty-64-minimal dovecot: lmtp(9610): Connect from local
Mar 15 11:36:51 Ubuntu-1404-trusty-64-minimal dovecot: lmtp(9610, lukas.mueller@marketstrategy.de): mLjfD8Pl51aKJQAA4rfF6Q: msgid=<20160315103651.2DE5B46097A@Ubuntu-1404-trusty-64-minimal.localdomain>: saved mail to INBOX
Mar 15 11:36:51 Ubuntu-1404-trusty-64-minimal postfix/lmtp[9609]: 2DE5B46097A: to=<lukas.mueller@marketstrategy.de>, relay=Ubuntu-1404-trusty-64-minimal.localdomain[private/dovecot-lmtp], delay=0.17, delays=0.06/0.01/0.01/0.09, dsn=2.0.0, status=sent (250 2.0.0 <lukas.mueller@marketstrategy.de> mLjfD8Pl51aKJQAA4rfF6Q Saved)
Mar 15 11:36:51 Ubuntu-1404-trusty-64-minimal dovecot: lmtp(9610): Disconnect from local: Successful quit
Mar 15 11:36:51 Ubuntu-1404-trusty-64-minimal postfix/qmgr[9591]: 2DE5B46097A: removed
Mar 15 11:36:51 Ubuntu-1404-trusty-64-minimal dovecot: imap-login: Login: user=<lukas.mueller@marketstrategy.de>, method=PLAIN, rip=136.243.54.13, lip=136.243.54.13, mpid=9613, secured, session=<zAGw+RMu3gCI8zYN>
Mar 15 11:36:52 Ubuntu-1404-trusty-64-minimal dovecot: imap(lukas.mueller@marketstrategy.de): Disconnected: Logged out in=44 out=573
Mar 15 11:36:52 Ubuntu-1404-trusty-64-minimal dovecot: imap-login: Login: user=<lukas.mueller@marketstrategy.de>, method=PLAIN, rip=136.243.54.13, lip=136.243.54.13, mpid=9617, secured, session=<iem5+RMu3wCI8zYN>
Mar 15 11:36:52 Ubuntu-1404-trusty-64-minimal dovecot: imap-login: Login: user=<lukas.mueller@marketstrategy.de>, method=PLAIN, rip=136.243.54.13, lip=136.243.54.13, mpid=9619, secured, session=<JxK6+RMu4ACI8zYN>
Mar 15 11:36:52 Ubuntu-1404-trusty-64-minimal dovecot: imap(lukas.mueller@marketstrategy.de): Disconnected: Logged out in=119 out=704
Mar 15 11:36:52 Ubuntu-1404-trusty-64-minimal dovecot: imap(lukas.mueller@marketstrategy.de): Disconnected: Logged out in=304 out=3701
```

status=bounced (host ... refused to talk to me: 550-Requested action not  taken: mailbox unavailable 550-Reject due to policy restrictions. 
Means that:
1) Mail address is uknown to host/misspelled which isn't the case (as I'm replying to a mail I recieved) or:
2) Policies of the host are not respected. Any Ideas what exactly could be meant by that?

---

### Post by SeijiSensei on 2016-03-16
Where is the server located?  If you're on a residential connection, many email services will refuse to take your mail to avoid being attacked by spambots.  Also your ISP may have a "no-servers" clause in your Terms of Service.  The only reliable method to send mail is to either have a business-class Internet connection or rent a virtual machine at some place like [Linode](http://www.linode.com/).

---

### Post by lisati on 2016-03-16
You might want to check that your rDNS and DNS match. If the rDNS for the IP address used by your server gives a domain name that doesn't point back to the same IP address, it can cause some email servers to throw a hissy fit and reject your email.

---


---
title: "Recommended mail server packages"
date: 2011-10-03
forum: Server Platforms
---

### Post by viperce on 2011-10-03
Hi Everyone,

I have been trying for awhile now to get a mail server up and running using Ubuntu Server.

Could someone please give me directions or links to mail servers for dummies or something, I have read a few and TBH i am even more confused now.

I would like to start off with the basics.
this is what i would like to start with.

Retrieve mail from ISP, deliver mail to virtual mailbox (/home/vmail/Maildir), mail then gets sorted and delivered to the correct mailbox /home/vmail/%d/%n

Could someone please recommend some packages that i could use.
i was thinking about using postfix fetchmail dovecot but i am not sure how to set them up correctly or if i need an additional package to sort the mails.

So far i have managed to get fetchmail to recieve the mails and deliver them to the vmail user, but the mails just sit there.

Please can someone help with this I have been trying for months now with no luck.

---

### Post by nyu2007 on 2011-10-03
Hi,

I think you should be use postfix dovecot for mail gateway and relay.
Other way: Zimbra opensource.

---


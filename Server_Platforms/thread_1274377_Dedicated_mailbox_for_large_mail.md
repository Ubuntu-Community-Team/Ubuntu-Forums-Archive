---
title: "Dedicated mailbox for large mail"
date: 2009-09-24
forum: Server Platforms
---

### Post by Ubunt2u on 2009-09-24
Setup:
8.04 Desktop
Mail Server
Postfix/Courier/Squirrelmail/Spamassassin/Amavis


Hello I was wondering if it would be possible, and if so how, to create a mailbox to receive mail from all accounts on our network above a certain size threshold?

---

### Post by HermanAB on 2009-09-24
Hmm, it may be a better idea to install a mail server with a decent database backend for all your mail.  For example Citadel or Zimbra.  These systems will only save one copy of a message sent to multiple addressees, so the savings in disk space can be very large.

---

### Post by Ubunt2u on 2009-09-24
Thanks for your reply.  Let me explain what I'm after...The reason I'm asking this is because we get alot of large graphics files that are sent to different salespeople here.  I was just wondering if, when a mail is at least a certain size, it would just go directly to the graphics email address instead of the salespeople?

---


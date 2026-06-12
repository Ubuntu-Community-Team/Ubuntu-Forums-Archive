---
title: "How to chose mail server?"
date: 2012-09-20
forum: Server Platforms
---

### Post by samansad on 2012-09-20
Dear all

I am planning to run an Ubuntu server as a mail server for our office. Our goal is to have an email server that connect to our web mail server and pull all the emails from server.
Our employee don't have access to internet but we need all of them use email. So we want to have a local mail server.
Everybody will connect to local mail server and our local mail server will connect to our web mail server.
Now my question is that which mail server do you suggest to use?

Thank you so much

---

### Post by volkswagner on 2012-09-21
Will the employees be using a mail client, or do you prefer your internal mail server to have it's own web based mail for clients to connect?  This could leave all mail on the server and not on the workstations.

If you want feature rich mail server with additional features such as chat and calendar, Citadel is fairly simple to setup.

If you want a lightweight setup Exim4 is the standard MTA in Ubuntu.  Postfix is also widely used and well supported MTA.

---

### Post by LHammonds on 2012-09-21
I went with Zimbra Open Source Edition.  It will be used for our internal and external messages but you could just as well have it work internally only.

It has a lot of features.  You can use its own client which works on all major OS's or the web client or anything that uses standard protocols such as Thunderbird or Outlook and even phones like the iPhone.

I have a "how-to" link in my sig but that is for the prior version.  I'm currently working on updating it for the new 8.0 version that released on the new Ubuntu 12.04 server.

LHammonds

---

### Post by samansad on 2012-09-24
Hi guys

Thank you for replying. I started to work with SOGo but honestly it was kinda confusing to configure. I will go through your suggestion one by one to find the most suitable for my case.

volkswagner: I am thinking of something that can give me both possibility.

Thank you so much for your reply

---

### Post by xdracco on 2012-09-24
I suggest Postfix + Courier-IMAP....

Postfix is super easy to configure. Courier-IMAP supports both POP and IMAP. For spam filtering, I suggest DSPAM and use SQL to store rules. If you plan on allowing users to filter their incoming mail, I suggest Maildrop (bundled with Courier-IMAP)... Procmail is dated and somewhat confusing.

Personally, I'm not a fan of Sendmail or SpamAssassin.

---


---
title: "Postfix: priority to inbound messages"
date: 2008-09-16
forum: Server Platforms
---

### Post by Homer on 2008-09-16
Hello,

We often need to send many emails that fill the postfix queue for a while.  This is not a problem, because we don't care about the time needed to send these messages.

While postfix send theses messages, we may receive replies to messages we already sent to our contacts.  I would like postfix prioritize the delivery of inbounds messages when they are received by the mail server.  Inbounds messages should be high priority while outbounds messages have to be low priority.

I would like to avoid to run a second postfix for my inbounds messages.  It's not the solution I'm looking for.

I made some google search, without success.  There is a Postfix guru on this forum? :)

Thanks in advance!

---


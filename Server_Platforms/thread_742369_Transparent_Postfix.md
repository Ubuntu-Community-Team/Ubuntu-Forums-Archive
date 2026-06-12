---
title: "Transparent Postfix"
date: 2008-04-01
forum: Server Platforms
---

### Post by scot1967-1 on 2008-04-01
Is there any way to make Postfix transparent so the client address is not seen as the postfix relay server's address?

I have setup a Postfix server as a mail relay for our network.  It is currently in the DMZ filtering for valid recipients.  Currently all of the mail relayed to the internal mail server appears to have come from the DMZ server instead of the original location.  This is normal.  However...

I have a spam filter on the internal network that can do tarpitting.  I could do this on the Postfix server but my internal spam filter has a nice reporting systems and a gui interface to manage things and I would like to use the tarpitting option.  Since all mail now comes from the Postfix relay, tarpitting will not work.


Thanks!

Scott H.

---

### Post by MJN on 2008-04-02
Tarpitting will not work in your situation at all as your Postfix server has already accepted the message i.e. it is too late to delay the original connecting server.

Mathew

---


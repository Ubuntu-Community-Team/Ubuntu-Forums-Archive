---
title: "Cyrus and Mailbox subfolders not visible"
date: 2010-12-08
forum: Server Platforms
---

### Post by movies1978 on 2010-12-08
Hello,
I am new to mailserver administration and I havee an Cyrus Imapd running. I already see mails in my outlook client but there are no subfolders only Inbox.
I can see those folders in cyradm. I gave the user all rights in cyradm. I can create folders below Inbox within outlook.

```

lm 
user.mathias (\HasChildren)
user.mathias.Deleted Messages (\HasNoChildren)
user.mathias.Drafts (\HasNoChildren)
user.mathias.Sent (\HasNoChildren)
user.mathias.Trash (\HasNoChildren)
user.mathias.local (\HasNoChildren)

```

Can anybody help me with this. Do I need a prefix for the outlook or something? I can provide config if needed.

Greetings 
movies

---


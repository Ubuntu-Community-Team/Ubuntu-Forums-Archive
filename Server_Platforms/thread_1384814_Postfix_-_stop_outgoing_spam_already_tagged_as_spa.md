---
title: "Postfix - stop outgoing spam already tagged as spam"
date: 2010-01-18
forum: Server Platforms
---

### Post by ooobooontooo on 2010-01-18
Hi,

I manage a mail server, and I've installed Postfix, Amavis, and Spamassassin on it, among other things. Postfix receives outside mail and passes it on to Amavis which has Spamassassin rate it and tags, it if it is spam ,and returns it back to Postfix. Then the mail is distributed to the various users and their procmailrc's take care of what they want to do with the spam. This all works very well, but we also have emails with foreign domains in our virtual aliases list. Because these people don't have procmailrc's to stop the spam, we just forward the tagged spam to the foreign servers. Often times their servers reject our forwarded spam, and we often get "Undelivered Mail Returned to Sender" messages, please note that this is not a backscatter problem. So, I'm asking is there any way to stop outgoing mail already tagged as spam? Thanks in advance.

---


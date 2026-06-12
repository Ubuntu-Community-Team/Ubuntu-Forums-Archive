---
title: "smtp server config while retaining google apps"
date: 2013-04-09
forum: Server Platforms
---

### Post by 4dam on 2013-04-09
I've spent a couple of days researching and reading but haven't found a solution to exactly what I'm looking to do and would seriously appreciate any help.

Basically we have all mail currently handled by google apps for our domain, say domain.com.  They have a limit of 500 email per day though and we often send a mail list to clients and use a mail merge to individualize each email and this has been hitting the limit lately as we have more clients to send to.  We'd like to keep all mailboxes and mx records pointing to google but have a separate smtp.domain.com server that we can use to send out with for those lists.  We want to use a [EMAIL="user@domain.com"]user@domain.com[/EMAIL] email with an existing mailbox on google to send out those specific emails through our own stmp server so that any responses come back into the google apps mailbox.  Basically no mailboxes needed on the smtp machine.  I know we have to set up spf and dkim and reverse dns for the smtp domain but I can't find how to config the stmp server or even what this would be called, relay, gateway, smarthost?

So far I have the server set up (12.04LTS) and locked down but I'm now trying to look at exim and postfix to see which is best for what I'm trying to do and more importantly how to set it up.

Any ideas would be greatly appreciated!!

---


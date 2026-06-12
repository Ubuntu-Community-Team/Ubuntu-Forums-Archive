---
title: "Keeping a backup email server"
date: 2008-04-29
forum: Server Platforms
---

### Post by Faw on 2008-04-29
I have looked and asked around but I've found no answer for this.

I have 2 mail servers (main,backup). Only main is visible from outside, backup is internal. All I want to do is have main receive and deliver the message to the local accounts, but also send the email to the backup server to be processed. 

I don't want to use rsync, I want the backup server to process the email the same way main would.

Does anyone have any idea on how to do something like that? 

Thanks in advance...

PS:Using 8.04/postfix/dovecot (debian testing version, ubuntu's doesn't have managesieve)

---


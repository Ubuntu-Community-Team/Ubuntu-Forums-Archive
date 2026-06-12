---
title: "Looking for a solution for server based mailbox caching"
date: 2011-10-18
forum: Server Platforms
---

### Post by wild hedgehog on 2011-10-18
I'm stuck looking for a solution for an office in rural Asia, with a shaky internet connection. I'm looking for a way to download and maintain local copies of mailboxes ("cache") of several users, allowing them to access the local server to get/send mails and not having to bother, if the internet connection is currently up or down.
So far so easy - e.g. Zimbra on an Ubuntu server might do the job.

Now for the tricky part: When the users are outside the remote office and have internet access, they are unable to access the cache server in the local office and have to use the "main" mailserver in the internet. How can I ensure that mails sent while in the local office appear in the the sent mail folder of the account on the main mail server?

Any hints are highly appreciated

---

### Post by vasile002 on 2011-10-18
If the sent mail is saved on the mail servers then you can just sync the .Sent folders for all mail accounts using lsyncd

---


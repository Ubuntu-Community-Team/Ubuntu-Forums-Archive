---
title: "Importing emails from microsoft exchange to postfix-courier"
date: 2009-02-18
forum: Server Platforms
---

### Post by trileru808 on 2009-02-18
Hello people. I have an Ubuntu Server 8.10 setup with postfix and courier-imap. I just built this server as an alternative to Microsoft Exchange which holds the current user accounts with their emails. Is there a way that I can export the emails from Microsoft Exchange for each user and import them into the newly created accounts in postfix?

I must add that I found a way to do this but it is very challenging for my patience. I configured postfix with another domain (user@anotherdomain.com) witch I can configure on each Outlook interface for every user, then copy-paste their emails into the postfix account, then rename the domain after all 25-30 or so accounts are imported. Is there another way for this? There has to be...

Thank you very much and have a nice day :)

---

### Post by cdenley on 2009-02-18
Exchange supports IMAP, right? I've used imapcopy to copy mail from one IMAP server to another in bulk, and it worked pretty well. Some messages or folders failed to copy, but I suspect that was because of the old mail server.
```

sudo apt-get install imapcopy

```

---


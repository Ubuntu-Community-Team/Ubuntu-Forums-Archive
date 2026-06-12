---
title: "Spamassassin Non-Trusted Networks"
date: 2011-06-22
forum: Server Platforms
---

### Post by Jay89 on 2011-06-22
Is there a way to NOT trust the localhost? I read from the spamassassin website that it is implicitly trusted. Is there a way arround that? I want spamassassin to check EVERY email regardless of where it comes in from. The way it's working now isn't doing it. Even IF it assigns the message a score thats above the "spam score" it is NOT flagged as such the way it is now.

Thanks.

---

### Post by Jay89 on 2011-06-22
I even commented out TRUSTED_NETWORKS in local.cf and it still does it.

---


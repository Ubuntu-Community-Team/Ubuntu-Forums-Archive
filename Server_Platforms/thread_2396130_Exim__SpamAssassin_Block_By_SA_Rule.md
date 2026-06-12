---
title: "Exim \ SpamAssassin Block By SA Rule"
date: 2018-07-11
forum: Server Platforms
---

### Post by Kirk Schnable on 2018-07-11
Hi everyone,

Quick question here concerning my email server which is running Exim and SpamAssassin, hoping that someone can help.

I have a user who is receiving a high volume of spam emails, and I found that the emails often are triggering these SpamAssassin rules:
```
  1.9 URIBL_ABUSE_SURBL      Contains an URL listed in the ABUSE SURBL blocklist
  2.5 URIBL_DBL_SPAM         Contains a spam URL listed in the Spamhaus DBL blocklist
```

I have no desire or need to receive emails which contain URLs listed in the SpamHaus DBL blocklist.  I'm less sure about ABUSE SURBL but I will give it a test run too.

How can I configure SpamAssassin or Exim in such a way that an email triggering one of these SA rules is immediately rejected instead of just adding a few points to the score?

Thank you!
Kirk

---


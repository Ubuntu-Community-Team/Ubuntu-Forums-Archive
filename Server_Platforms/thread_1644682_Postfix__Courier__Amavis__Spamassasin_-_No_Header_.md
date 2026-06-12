---
title: "Postfix / Courier / Amavis / Spamassasin - No Header Modification"
date: 2010-12-13
forum: Server Platforms
---

### Post by IOWAHC on 2010-12-13
Hello there!

I have setup a Ubuntu 8.04 LTS Server with postfix and Courier with amavis and spamassassin. But incoming email won't get the headers modified.

When receiving emails, they don't have a X-SPAM-* Header.

I followed basically the tutorial on howtoforge.com and from the community tutorials.

Well, can't figure out, why.

Mail.log tells me, that the mail is getting scanned, Spam is being logged with Passed SPAM and Ham is logged with Passed CLEAN. I set the SPAM in main.cf to D_PASS, to get it to my mail Account.

Anyone can help me?

---


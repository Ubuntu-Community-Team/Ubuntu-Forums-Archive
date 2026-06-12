---
title: "Serious issue coming with latest upgrades"
date: 2007-02-11
forum: Server Platforms
---

### Post by fcosentino on 2007-02-11
Everyone,

one of the latest updates has broken really badly SMTP on port 25.

Using Ubuntu 6.10 desktop - and Sambar Pro 6.4 web/mail server - everything was working fine until I accepted some updates.

Now port 25 transactions are badly broken. The server responds on port 25, but then it hangs in the middle of the transaction (until it times out). I didn't enable any firewall.

To prove that it is an Ubuntu issue, I did move the mail server to a Windows XP machine (temporarily), using Windows version of Sambar 6.4. Everything works again.

Please help - this is really bad - before I will spend half a day reinstalling the entire server (and rejecting updates for the next 10 years), let me know what I should be looking for.

---


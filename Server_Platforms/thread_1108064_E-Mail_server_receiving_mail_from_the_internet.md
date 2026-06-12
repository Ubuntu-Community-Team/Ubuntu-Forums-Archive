---
title: "E-Mail server: receiving mail from the internet?"
date: 2009-03-27
forum: Server Platforms
---

### Post by tkhobbes on 2009-03-27
Hi all

I am just setting up a new small home server. I had one with Gentoo, and decided to switch over to Ubuntu server edition.
On Gentoo, I used postfix and courier; on the Ubuntu server, I now just installed postfix and dovecot, works flawlessly. :)

However, I need the server to regularly fetch e-mail from my internet e-mail accounts (it's only an INTERNAL home server...); on the Gentoo box, I installed fetchmail for this purpose and had a cron job running that was fetching mail every 10 minutes or so.

Is this the preferred solution - or is there something more... fancy? :) I also would appreciate any guide or howto on this regard; I found a lot on Postfix and spamfiltering and all this kind of stuff, but actually fetching e-mail from the Internet was nowhere described... maybe I missed it?

Thanks
tkhobbes

---

### Post by dipeshmehta on 2009-03-27
please check following:

[http://www.howtoforge.com/debian_etch_fetchmail](http://www.howtoforge.com/debian_etch_fetchmail)

and

[http://www.howtoforge.com/debian_etch_getmail](http://www.howtoforge.com/debian_etch_getmail)

---

### Post by tkhobbes on 2009-04-03
Great, thanks a lot; did not know about getmail, that looks great :)

---

### Post by tkhobbes on 2009-04-23
getmail works flawlessly - thanks for the tip!

---


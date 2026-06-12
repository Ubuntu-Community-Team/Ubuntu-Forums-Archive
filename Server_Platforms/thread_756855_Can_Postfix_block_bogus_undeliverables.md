---
title: "Can Postfix block bogus undeliverables?"
date: 2008-04-16
forum: Server Platforms
---

### Post by scot1967-1 on 2008-04-16
Periodically my users will get several un-deliverable notices for e-mail they did not send.  It seems that thier e-mail address may have been forged on the souce of the e-mail and the servers are sending the non-delivery notices to us instead of the real source.

Can anything be done in postfix to block this?

Thanks!

---

### Post by ronald.higgins on 2008-04-16
Do you use Greylisting on your mail server ?

i imagine legitimate mta's would then resubmit the bounce after the initial block.

EDIT: Leaving the office now but google "backscatter" and see what technique's others are using.

---

### Post by MJN on 2008-04-16
There is no real panacea to this problem, but you can gain some insight on what steps might help at [http://www.postfix.org/BACKSCATTER_README.html](http://www.postfix.org/BACKSCATTER_README.html)

Mathew

---


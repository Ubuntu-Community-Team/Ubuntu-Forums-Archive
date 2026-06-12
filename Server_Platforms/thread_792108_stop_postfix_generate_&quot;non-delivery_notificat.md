---
title: "stop postfix generate &quot;non-delivery notification&quot; messages"
date: 2008-05-12
forum: Server Platforms
---

### Post by frankabel on 2008-05-12
I need stop my central MTA (postfix) generate "non-delivery notification" messages when ones of the internal server refuse get an email permanently, see what I mean in the following log lines. Is that possible?

I research and can't found a way, so what I think is filter those "non-delivery notification". I really preffer that they (dozens of thousand daily) don't get generated, because they load my system.


May 12 10:03:06 newton postfix/qmgr[20897]: 5E6F71D631A: from=<huadjai1958@amvac-chemical.com>, size=1698, nrcpt=1 (queue active)


May 12 10:03:11 newton postfix/smtp[22898]: 5E6F71D631A: to=<aa29430066@XXX>, relay=XXX[10.8.1.34]:25, delay=37148, delays=37145/0.03/0.05/3.1, dsn=5.0.0, status=bounced (host XXX[10.8.1.34] said: 554 Sorry, message looks like SPAM to me (in reply to end of DATA command))


May 12 10:03:12 newton postfix/bounce[27960]: 5E6F71D631A: sender non-delivery notification: 3F6D21D5BCF


May 12 10:03:12 newton postfix/qmgr[20897]: 5E6F71D631A: removed

---


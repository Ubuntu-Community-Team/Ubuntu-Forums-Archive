---
title: "Postfix sending mystery mail every five mins"
date: 2009-03-04
forum: Server Platforms
---

### Post by GlennB on 2009-03-04
Hi All,

An Ubuntu 8.04 LAMP system here is sending mystery email once every five minutes, and I'm tearing my hair out trying to find out what's sending the mail, and where it's going! Any help on troubleshooting this would be very welcome.

Here's an example section from mail.log:

```
Mar  4 18:35:01 doris postfix/pickup[20467]: 28C2E12BC7D0: uid=0 from=<root>
Mar  4 18:35:01 doris postfix/cleanup[20699]: 28C2E12BC7D0: message-id=<20090304183501.28C2E12BC7D0@doris.mydomain.co.uk>
Mar  4 18:35:01 doris postfix/qmgr[5918]: 28C2E12BC7D0: from=<root@mydomain.co.uk>, size=670, nrcpt=1 (queue active)
Mar  4 18:35:01 doris postfix/smtp[20701]: 28C2E12BC7D0: to=<root@mydomain.co.uk>, orig_to=<root>, relay=mailhost.myisp.co.uk[21x.2xx.x.x8]:25, delay=0.27, delays=0.03/0/0.1/0.14, dsn=2.0.0, status=sent (250 OK id=1Levw3-0007fD-VY)
Mar  4 18:35:01 doris postfix/qmgr[5918]: 28C2E12BC7D0: removed
```

A similar message appears once every five minutes - 18:35:01, 18:40:01 etc. I have nullmailer installed on this machine, which sends to my isp as a smarthost, but I'm not aware of ever configuring Postfix to use a smarthost. 'myisp' and 'mydomain' are obviously not the real domains.

Can anyone suggest how I might go about locating which application is sending this mail? The only 'scheduled' mail from this machine is a daily report from logwatch, which is the reason I installed nullmailer. 

I've checked the likely crontabs and tried hunting through config files, but there must be a clever way to do this!

Thanks,

Glenn.

---

### Post by terazen on 2009-03-04
If there is a file /var/mail/root you could read it using mail, more, cat, tail etc.

---

### Post by GlennB on 2009-03-05
> **terazen said:**
> If there is a file /var/mail/root you could read it using mail, more, cat, tail etc.

Thanks, I checked for that but /var/mail is completely empty. I think what I need is to stop postfix from emptying the queue after delivering the email, so I can take a look at what it's sending. Sadly, I have no idea how to do that!

Regards,

Glenn.

---

### Post by GlennB on 2009-03-05
I finally found the culprit!

I trawled syslog, comparing timestamps with the mail logs, and found that gsmsmsrequeue (part of gsm-utils) was making entries in syslog at the same times that the emails were being generated. 

I have no idea why I have gsm-utils installed, since I don't own a gsm modem. I guess it was pulled in by some other package (maybe ejabberd??). Anyway, I have uninstalled gsm-utils, and the mails have stopped.

My fears that somebody was using my server for nefarious purposes were unfounded!

Regards,

Glenn.

---


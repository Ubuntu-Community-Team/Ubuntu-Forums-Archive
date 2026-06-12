---
title: "postfix mail server-senting mail to hotmail issue"
date: 2010-09-01
forum: Server Platforms
---

### Post by duceduc on 2010-09-01
After setting up my mail server using flurdy's how to, it has been working fine for the past month. At some point in time, I noticed that I can not sent mails to hotmail account. I am able to sent to gmail and yahoo. Those are the only two services I can test so far.

I am relaying the outgoing mail via my isp. Could it be that hotmail blocked my isp? Below is my mail log showing two emails being sent. One to gmail and the other to hotmail. If I am not mistaken, it looks like both emails were successfully sent. Where the hotmail gone to, I don't know. I got the gmail one. 

I have spent a several hours on this and I am stomped at this point. Can someone please offer me suggestions. Thank you. 
> Sep  2 11:01:59 web-server imapd-ssl: Connection, ip=[::1]
Sep  2 11:01:59 web-server authdaemond: received auth request, service=imap, authtype=login
Sep  2 11:01:59 web-server authdaemond: authmysql: trying this module
Sep  2 11:01:59 web-server authdaemond: SQL query: SELECT id, crypt, "", uid, gid, home, concat(home,'/',maildir), "", name, "" FROM users WHERE id = 'xxxx@ducsu.com'  AND (enabled=1)
Sep  2 11:01:59 web-server authdaemond: password matches successfully
Sep  2 11:01:59 web-server authdaemond: authmysql: sysusername=<null>, sysuserid=5000, sysgroupid=5000, homedir=/var/spool/mail/virtual, address=xxxx@ducsu.com, fullname=junk, maildir=/var/spool/mail/virtual/noreply/, quota=<null>, options=<null>
Sep  2 11:01:59 web-server authdaemond: authmysql: clearpasswd=<null>, passwd=xxxxxxx
Sep  2 11:01:59 web-server authdaemond: Authenticated: sysusername=<null>, sysuserid=5000, sysgroupid=5000, homedir=/var/spool/mail/virtual, address=xxxx@ducsu.com, fullname=junk, maildir=/var/spool/mail/virtual/noreply/, quota=<null>, options=<null>
Sep  2 11:01:59 web-server authdaemond: Authenticated: clearpasswd=xxxxxx, passwd=xxxxxxx
Sep  2 11:01:59 web-server imapd-ssl: LOGIN, user=xxxx@ducsu.com, ip=[::1], port=[48801], protocol=IMAP
Sep  2 11:01:59 web-server imapd-ssl: LOGOUT, user=xxx@ducsu.com, ip=[::1], headers=167, body=0, rcvd=296, sent=1382, time=0, starttls=1
Sep  2 11:01:59 web-server postfix/pickup[9797]: 4CCE32612A9: uid=1002 from=<xxx@ducsu.com>
Sep  2 11:01:59 web-server postfix/cleanup[10284]: 4CCE32612A9: message-id=<d9dcfcf084e6cf3db0e90b9044169122.squirrel@xxxx.ducsu.com>
Sep  2 11:01:59 web-server postfix/pipe[10286]: A12E226086B: to=<xxxxx@ducsu.com>, relay=spamfilter, delay=0.68, delays=0.14/0.01/0/0.53, dsn=2.0.0, status=sent (delivered via spamfilter service)
Sep  2 11:01:59 web-server postfix/pipe[10286]: A12E226086B: to=<xxxx@hotmail.com>, relay=spamfilter, delay=0.68, delays=0.14/0.01/0/0.53, dsn=2.0.0, status=sent (delivered via spamfilter service)
Sep  2 11:01:59 web-server postfix/qmgr[9798]: A12E226086B: removed
Sep  2 11:01:59 web-server postfix/qmgr[9798]: 4CCE32612A9: from=<xxx@ducsu.com>, size=1060, nrcpt=2 (queue active)
Sep  2 11:01:59 web-server amavis[8627]: (08627-05) ESMTP::10024 /var/lib/amavis/tmp/amavis-20100902T103458-08627: <xxxx@ducsu.com> -> <xxxx@gmail.com>,<xxxx@hotmail.com> SIZE=1060 BODY=8BITMIME Received: from mail.ducsu.com ([127.0.0.1]) by localhost (mail.ducsu.com [127.0.0.1]) (amavisd-new, port 10024) with ESMTP; Thu,  2 Sep 2010 11:01:59 +0900 (JST)
Sep  2 11:01:59 web-server amavis[8627]: (08627-05) Checking: M1hHhbAW4XmW [127.0.0.1] <xxx@ducsu.com> -> <xxxxx@gmail.com>,<xxxx@hotmail.com>
Sep  2 11:02:00 web-server postfix/smtpd[10302]: connect from localhost.localdomain[127.0.0.1]
Sep  2 11:02:00 web-server postfix/smtpd[10302]: 197F726086B: client=localhost.localdomain[127.0.0.1]
Sep  2 11:02:00 web-server postfix/cleanup[10284]: 197F726086B: message-id=<d9dcfcf084e6cf3db0e90b9044169122.squirrel@xxxxx.ducsu.com>
Sep  2 11:02:00 web-server postfix/qmgr[9798]: 197F726086B: from=<xxx@ducsu.com>, size=1247, nrcpt=2 (queue active)
Sep  2 11:02:00 web-server postfix/smtpd[10302]: disconnect from localhost.localdomain[127.0.0.1]
Sep  2 11:02:00 web-server amavis[8627]: (08627-05) FWD via SMTP: <xxx@ducsu.com> -> <xxxx@gmail.com>,<xxxxx@hotmail.com>,BODY=7BIT 250 2.0.0 Ok, id=08627-05, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 197F726086B
Sep  2 11:02:00 web-server amavis[8627]: (08627-05) Passed CLEAN, [127.0.0.1] <xxx@ducsu.com> -> <xxxxx@gmail.com>,<xxxxx@hotmail.com>, Message-ID: <d9dcfcf084e6cf3db0e90b9044169122.squirrel@xxxxx.ducsu.com>, mail_id: M1hHhbAW4XmW, Hits: -2.899, size: 1060, queued_as: 197F726086B, 859 ms
Sep  2 11:02:00 web-server postfix/smtp[10299]: 4CCE32612A9: to=<xxxx@gmail.com>, orig_to=<xxxxxx@ducsu.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=1.1, delays=0.17/0.01/0/0.88, dsn=2.0.0, status=sent (250 2.0.0 Ok, id=08627-05, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 197F726086B)
Sep  2 11:02:00 web-server postfix/smtp[10299]: 4CCE32612A9: to=<xxxx@hotmail.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=1.1, delays=0.17/0.01/0/0.88, dsn=2.0.0, status=sent (250 2.0.0 Ok, id=08627-05, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 197F726086B)
Sep  2 11:02:00 web-server postfix/qmgr[9798]: 4CCE32612A9: removed
Sep  2 11:02:00 web-server postfix/smtp[10258]: 197F726086B: to=<xxxx@gmail.com>, relay=smtp.xxxxx.ocn[125.206.148.148]:25, delay=0.38, delays=0.1/0.03/0.06/0.19, dsn=2.0.0, status=sent (250 Ok: queued as 469852360)
Sep  2 11:02:00 web-server postfix/smtp[10258]: 197F726086B: to=<xxxx@hotmail.com>, relay=smtp.xxxxx.ocn[125.206.148.148]:25, delay=0.38, delays=0.1/0.03/0.06/0.19, dsn=2.0.0, status=sent (250 Ok: queued as 469852360)
Sep  2 11:02:00 web-server postfix/qmgr[9798]: 197F726086B: removed

---

### Post by Bachstelze on 2010-09-01
Hotmail is stupid, nothing you can do. I generally use my ISP's SMTP server when I need to send email to Hotmail people. You can automate that with Sendmail, not sure about Postfix.

---

### Post by duceduc on 2010-09-02
Thanks for the info. 

To top it off. I can receive from hotmail and reply back to hotmail. I just can't sent a new mail directly to hotmail.

---


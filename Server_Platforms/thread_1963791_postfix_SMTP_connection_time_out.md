---
title: "postfix SMTP connection time out"
date: 2012-04-22
forum: Server Platforms
---

### Post by shahansudu on 2012-04-22
I have a server I use to run a mailing list... and I use the same server for local accounts in the domain. Configured Postfix with IMAP and I can receive mail without any issues. But I cannot send out mail when I try my client complains that it timed out.. have not issues with the port being blocked because I can telnet to it fine. I'm using port 465 with TLS/SSL. Here is what I see in my log, 
```

Apr 23 02:30:20 domU-12-31-39-0A-14-58 imapd-ssl: TIMEOUT, user=testuser, ip=[::ffff:71.163.32.200], headers=0, body=0, rcvd=108, sent=525, time=2029, starttls=1
Apr 23 02:38:20 domU-12-31-39-0A-14-58 imapd-ssl: TIMEOUT, user=testuser2, ip=[::ffff:71.163.32.200], headers=232, body=1368, rcvd=6925, sent=5129, time=8623, starttls=1

```

Anyone have an idea what might be the issue? Thanx

---

### Post by smtp on 2012-04-23
Sending mails should not have nothing common with imap, it is looks that there is a problem with Postfix configuration. Could you please provide a litle more information how you tested sending messages out? 
It could be that sending IP is not allowed to relay or Postfix listening only on local interface.

---


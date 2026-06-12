---
title: "Postfix not sending mails zu outside"
date: 2013-10-03
forum: Server Platforms
---

### Post by paul59 on 2013-10-03
Hello,   I already read the various post on this topic, but my problem was not resolved using them.   I just set up an ubuntu server with the included mail server. The problem is I cannot send mails to the outside however I can receive mails from outside and also I can send mails within my mail server.  I already looked on the firewall to see if there is any communication on port 25, but there is none.  Could you please provide me with pointers to solve this problem?   Thanks in advance Paul

---

### Post by sanderj on 2013-10-03
Your ISP might be blocking outgoing SMTP traffic. Easy check: on your server type

```
telnet gmail-smtp-in.l.google.com. smtp
```

... what do you get?

```
sander@flappie:~$ telnet gmail-smtp-in.l.google.com. smtp
Trying 74.125.136.26...
Connected to gmail-smtp-in.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP l4si6661005eew.341 - gsmtp
ehlo asdfadsfasdf
250-mx.google.com at your service, [83.128.180.93]
250-SIZE 35882577
250-8BITMIME
250-STARTTLS
250-ENHANCEDSTATUSCODES
250 CHUNKING
quit
221 2.0.0 closing connection l4si6661005eew.341 - gsmtp
Connection closed by foreign host.
sander@flappie:~$
```

---

### Post by houstonbofh on 2013-10-03
Try using telnet to send an e-mail directly to someone on the outside.  If that works, look at the post fix relay options, as you may be being blocked from relay.

---


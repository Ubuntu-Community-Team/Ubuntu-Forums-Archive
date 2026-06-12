---
title: "Postfix mail occasionally bouncing from google"
date: 2010-02-08
forum: Server Platforms
---

### Post by cidz0r on 2010-02-08
I've recently set up my mail server to send mail directly through postfix instead of using a relay.  Most of the time this is working without any problems, but I am having an occasional issue where the mail is bouncing from google.  Here is an example log:

Feb  9 03:51:01 server postfix/smtp[20513]: connect to aspmx.l.google.com[209.85.221.52]:25: Connection refused
Feb  9 03:51:01 server postfix/smtp[20513]: 6488448AA0: to=<xxxx@xxxx.com>, relay=none, delay=0.08, delays=0.05/0.01/0.03/0, dsn=4.4.1, status=deferred (connect to aspmx.l.google.com[209.85.221.52]:25: Connection refused)

In this case the server it appears to be connecting to at google is mail-qy0-f52.google.com.  If I attempt to connect to this server using telnet on port 25 I similarly get a refused connection.  Oddly I am able to ping it.  The message will be deferred and will typically send in ~5-10 minutes when I get a different IP address returned from google.  Is there a way around this issue, or is google just occasionally pointing me to mail servers of theirs which are not active?  

Here is an example log from a successful send:

Feb  9 04:00:39 server postfix/smtp[20576]: 6A4EB48DD4: to=<xxxx@xxxx.com>, relay=aspmx.l.google.com[74.125.113.27]:25, delay=578, delays=577/0.01/0.15/0.55, dsn=2.0.0, status=sent (250 2.0.0 OK 1265688039 24si15076331vws.32

Thanks in advance!

---

### Post by FuturePilot on 2010-02-08
Is the server on a dynamic IP? Most of the time big email providers will block anything coming directly from a dynamic IP.

---

### Post by cidz0r on 2010-02-09
No, the server is on a static IP.  Note that most of the time the process works fine, that the mail server that google is pointing me to when it fails is in fact a valid google mail server, but that the server refuses any connections on port 25.

---

### Post by noway2 on 2010-02-09
I read once that some servers subscribe to a white list of valid email domains and if you are not on that white list that you may get bounced.  Since you have a static IP address it will be possible for you to get white listed, which is not the case for dynamic IP addresses.  If I recall, I read this on a FAQ page on dyndns.com.

---


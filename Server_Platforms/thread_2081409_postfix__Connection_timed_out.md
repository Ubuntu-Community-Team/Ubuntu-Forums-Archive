---
title: "postfix:  Connection timed out"
date: 2012-11-06
forum: Server Platforms
---

### Post by m3asmi on 2012-11-06
hello

I'm trying to configure my server postfix
when I test with telnet localhost 25 
in the log file I see:

```

Nov  7 00:45:52 ELGHAZI postfix/smtp[24525]: connect to mx4.hotmail.com[65.55.37.72]:25: Connection timed out
Nov  7 00:46:22 ELGHAZI postfix/smtp[24525]: connect to mx2.hotmail.com[65.55.92.184]:25: Connection timed out
Nov  7 00:46:52 ELGHAZI postfix/smtp[24525]: connect to mx2.hotmail.com[65.55.92.136]:25: Connection timed out
Nov  7 00:47:22 ELGHAZI postfix/smtp[24525]: connect to mx3.hotmail.com[65.55.37.88]:25: Connection timed out
Nov  7 00:47:52 ELGHAZI postfix/smtp[24525]: connect to mx1.hotmail.com[65.55.92.168]:25: Connection timed out
Nov  7 00:47:52 ELGHAZI postfix/smtp[24525]: 461223F0E4: to=<XXXXX@hotmail.com>, relay=none, delay=696, delays=544/0.34/152/0, dsn=4.4.1, status=deferred (connect to mx1.hotmail.com[65.55.92.168]:25: Connection timed out)

```
I fallowed  the doc from [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

there are some geniuses?

---

### Post by smtp on 2012-11-09
Please check if outbound connections to port 25 are allowed.

---


---
title: "apt-get install dovecot-postfix"
date: 2010-12-07
forum: Server Platforms
---

### Post by tryinghard on 2010-12-07
I installed the new dovecot-postfix(apt-get install dovecot-postfix) which it was said to be configured to be integrated and configured for security but when I tested it with  telnet localhost 25 thi s what I got:
telnet localhost 25
Trying ::1...
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 SORRY WEB ACCESS ONLY!!!!!!!
ehlo localhost
250-erific.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
auth login
503 5.5.1 Error: authentication not enabled

I must be off base   somewhere  Ineed it to  be configured. can someone please tell me how to get it to do SMTP authentication and to do tls? I'm still new at this but I can't be that far off or am I?
Miles Sakaguchi  A.K.A. tryinghard

---


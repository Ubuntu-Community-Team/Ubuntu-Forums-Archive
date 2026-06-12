---
title: "Email server can receive but not send"
date: 2009-01-22
forum: Server Platforms
---

### Post by joshsmoore on 2009-01-22
Hi,  I am a complete beginner and I have worked through a tutorial to setup an email server.  I am using ubuntu 8.10 and I have setup an email server using postfix and courier.  I have setup my DNS so that mail.codingforrent.com points to both my SMTP and pop3 server (the same machine).  I have set up Thunderbird for this account and I can receive email no problem.  The problem is when I go to send email I get this error message (from Thunderbird) "The message could not be sent because connecting to SMTP server mail.codingforrent.com failed.  The server may be unavailable or is refusing SMTP connections."  I can use telnet to access mail.codingforrent.com (on port 25).  But, I am not sure why Thunderbird cannot.  In addition when I check the logs I do not see any messages of an attempt to send.  Does anybody have any ideas of what might be going on?

---


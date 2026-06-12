---
title: "Postfix says: &quot;queue file write error&quot;"
date: 2008-06-11
forum: Server Platforms
---

### Post by qrwe on 2008-06-11
Hi,

As a postmaster for the mail server I administrate, I have gotten a message about an undeliverable mail in the mail queue. It says: 

> 
Out: 220 reciever.foo.com ESMTP Postfix
 In:  EHLO sender.bar.com
 Out: 250-reciever.foo.com
 Out: 250-PIPELINING
 Out: 250-SIZE 20480000
 Out: 250-VRFY
 Out: 250-ETRN
 Out: 250-STARTTLS
 Out: 250-AUTH LOGIN PLAIN
 Out: 250-AUTH=LOGIN PLAIN
 Out: 250-ENHANCEDSTATUSCODES
 Out: 250-8BITMIME
 Out: 250 DSN
 In:  MAIL FROM:<user.one@foo.com> SIZE=12804
 Out: 250 2.1.0 Ok
 In:  RCPT TO:<user.two@bar.com> ORCPT=rfc822;user.two@bar.com
     NOTIFY=SUCCESS,FAILURE,DELAY
 Out: 250 2.1.5 Ok
 In:  DATA
 Out: 354 End data with <CR><LF>.<CR><LF>
 Out: 451 4.3.0 Error: queue file write error
 In:  QUIT
 Out: 221 2.0.0 Bye


I can't figure out what's wrong. Has anyone seen this before?
Thanks for any help.

---

### Post by MJN on 2008-06-11
You really need to look at the Postfix logs rather than the SMTP transcript. Post the relevent section of /var/log/mail.log as it may hold some clues about exactly which queue is not being written to. Do you have any virus scanning or other service that gets piped messages?

Mathew

---


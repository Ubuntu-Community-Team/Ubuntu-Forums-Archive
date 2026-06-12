---
title: "postfix inaccessible from outside"
date: 2014-03-02
forum: Server Platforms
---

### Post by shawn11 on 2014-03-02
I cannot access postfix on my internet-facing box running dns alongside the imap/pop ports from dovecot from the outside.
I have another internet provider so I am using that as an outside source to telnet/connect with no luck.
However, I can actually send mail from gmail into my mailserver and receive it.
It is strange I can do that yet telnet connection times out for any other host and/or when attempting to send mail using IMAP/POP client authenticating over SMTP-auth to the users defined in the virtual tables [I set up mysql tables], it does not communicate with my mailserver. 
An outside nmap scan reveals the port is filtered and iptables is not blocking it. I contacted my ISP and they claim they aren't blocking it, which I believe is true since gmail actually was able to deliver an email.
What could this be?

---


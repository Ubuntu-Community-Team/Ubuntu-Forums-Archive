---
title: "How to verify whether TLS is working or not. in EXIM4 mailserver"
date: 2008-06-13
forum: Server Platforms
---

### Post by sp.mahapatra on 2008-06-13
How to verify whether TLS is working or not. 

Hello i have install exim4 in my ubuntu m/c.
i i gone through a document.and configured the TLS.
so i could findout weather its working or not.

i m getting this output 

root@testing:~# swaks -a -tls -q HELO -s localhost -au jasonb -ap '<>'
=== Trying localhost:25...
=== Connected to localhost.
<-  220 testing.com ESMTP Exim 4.69 Thu, 12 Jun 2008 21:42:05 +0530
 -> EHLO testing.com
<-  250-testing.com Hello localhost [127.0.0.1]
<-  250-SIZE 52428800
<-  250-PIPELINING
<-  250 HELP
*** STARTTLS not supported
 -> QUIT
<-  221 testing.com closing connection
=== Connection closed with remote host


can anybosy tell me weather my TLS is working or not,If yes then how can i know and if no then what is the solution

Thanks in advance

---

### Post by MJN on 2008-06-13
I can tell you it is not working ('STARTTLS not supported') however as I don't use Exim I'm afraid I won't be able to tell you why. Post your config then someone else can take a look.
 
Mathew

---


---
title: "How to set up open relay for email"
date: 2008-09-04
forum: Server Platforms
---

### Post by jtruesdell on 2008-09-04
Okay, I thought I had a problem with an open relay (I need one) and I'm not sure exactly what the missing link is that I need so I'll explain the situation and perhaps someone can point me in the right direction...

I have a scanner which can only scan to email (Xerox M118i). It can only send email through an open relay - no authentication whatsoever. I have set up an 8.04 box to perform this function. I just found out that the Xerox won't accept a local address to which it sends email (I can't send email to "me" it requires "me@domain.com")

Now, I can do an SMTP session over telnet and it will take anything as the mail from: address. Great. I can send that test email to "me". Perfect...comes right to my email. Unfortunately I get a 554 5.7.1 Relay access when I try to send to "me@domain.local" (or .com, or @server.domain.(local/com) or @server), despite the server being server.domain.local. 

So therein lies my problem - The Xerox will only send to an @foo address, and the mail server won't accept/relay an @foo address. Since I can't change the Xerox, is there something I'm missing about the to: field I should know?

Thanks for reading all the way to the bottom,
Jordan

P.S. - the server is behind two cascaded firewalls and operates only on our internal network. It doesn't, as far as I know, even run anything which accesses the internet beyond.

---

### Post by HermanAB on 2008-09-04
If the scanner is controlled by Sane, then you should be able to scan to anything and run Sane as a server for access from other machines.  So, you could ignore the dumbass Xerox functions and use Sane.

Otherwise, you should be able to do the address translations with Postfix - you are on the right track, but you will likely have to spend a long time reading the manual on the Postfix web site.

Oh, well, hope that helps.

Herman

---


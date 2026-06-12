---
title: "Postfix STARTTLS EHLO"
date: 2009-09-28
forum: Server Platforms
---

### Post by dubbelodub on 2009-09-28
Hi there.

I don't know if it's just me doing something wrong but I'm trying to use AUTH from terminal with a Postfix Mail Server. I use a PHP script with PEAR to automate this.

My problem is that I can't recreate what PEAR does by hand and I can't understand why. When I turn the debug parameter on in PEAR it gives me this.

--------------------------------------------------------------------------

DEBUG: Recv: 220 mail.******************.co.za ESMTP Postfix 
DEBUG: Send: EHLO localhost 
DEBUG: Recv: 250-mail.******************.co.za 
DEBUG: Recv: 250-PIPELINING 
DEBUG: Recv: 250-SIZE 12288000 
DEBUG: Recv: 250-VRFY 
DEBUG: Recv: 250-ETRN 
DEBUG: Recv: 250-STARTTLS 
DEBUG: Recv: 250-ENHANCEDSTATUSCODES 
DEBUG: Recv: 250-8BITMIME 
DEBUG: Recv: 250 DSN 
DEBUG: Send: STARTTLS 
DEBUG: Recv: 220 2.0.0 Ready to start TLS 
DEBUG: Send: EHLO localhost

-----> Manual Problem Here

DEBUG: Recv: 250-mail.*****************.co.za 
DEBUG: Recv: 250-PIPELINING 
DEBUG: Recv: 250-SIZE 12288000 
DEBUG: Recv: 250-VRFY 
DEBUG: Recv: 250-ETRN 
DEBUG: Recv: 250-AUTH LOGIN PLAIN 
DEBUG: Recv: 250-AUTH=LOGIN PLAIN 
DEBUG: Recv: 250-ENHANCEDSTATUSCODES 
DEBUG: Recv: 250-8BITMIME 
DEBUG: Recv: 250 DSN 
DEBUG: Send: AUTH PLAIN 
DEBUG: Recv: 334 
DEBUG: Send: ***********************************************= 
DEBUG: Recv: 235 2.0.0 Authentication successful 
DEBUG: Send: MAIL FROM: DEBUG: Recv: 250 2.1.0 Ok 
DEBUG: Send: RCPT TO: DEBUG: Recv: 250 2.1.5 Ok 
DEBUG: Send: DATA DEBUG: Recv: 354 End data with . 
DEBUG: Send: MIME-Version: 1.0 From: ****@********.net Subject: noSubject To: [email]alex@*******.com[/email] Content-Transfer-Encoding: quoted-printable Content-Type: text/html; charset="ISO-8859-1" 
DEBUG: Send: QUIT DEBUG: Recv: 221 2.0.0 Bye

--------------------------------------------------------------------------

Everything works fine here except when I try to do this manually from a terminal with telnet on port 25 after STARTTLS, I try to issue 
EHLO localhost but then Postfix quits on me.

I'm not sure what's happening here.

---


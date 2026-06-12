---
title: "Postfix (html translate problem)"
date: 2011-10-11
forum: Server Platforms
---

### Post by ulrikp on 2011-10-11
Hello,
 
I have a Ubuntu LAMP server, where I also have installed postfix.
 
But I have a problem with, it does not "translate" the HTML code, when I send a email to a single email domain (eg. @test.com). So the user can see the html code as content.
 
For all other email domain (eg. @gmail.com, @hotmail.com etc), it is html translated correct.
 
At first I thought it was that single email domain, there was something wrong with, but I've tested it with a Windows SMTP server and there it works.
 
Have any of you an idea of what it could be, mabye in the configuration file? 
 
Thank you.
 
Best regards,
Ulrik

---

### Post by ulrikp on 2011-10-12
I have found out that it probably is not a problem with the html translate, but a problem with the mail header.

If I send an e-mail for example to [EMAIL="test@domain.com"]test@domain.com[/EMAIL], so it will appear like this in the mailbox:
"
Content-type: text/html; charset=iso-8859-1
From: Ulrik <[EMAIL="ulrik@ulrik.dk"]ulrik@ulrik.dk[/EMAIL]>
Message-Id: <[EMAIL="20111012111806.960768196C@lamp.ulrik.dk"]20111012111806.960768196C@lamp.ulrik.dk[/EMAIL]>
Date: Wed, 12 Oct 2011 13:18:06 +0200 (CEST)
test test ...
test test ...
"

---


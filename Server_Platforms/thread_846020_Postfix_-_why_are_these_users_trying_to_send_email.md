---
title: "Postfix - why are these users trying to send email"
date: 2008-07-01
forum: Server Platforms
---

### Post by cwmoser on 2008-07-01
About a month ago I setup Ubuntu 7.10 Server and Postfix mail server.

I get a lot of email reported like below.  
It looks like various people are trying to send email to my server.
What is it?  Spam?  Mail Relay - BTW, what exactly is mail relay?  From some huge email list?

Thanks

Carl

Example email I get from my MAILER-DAEMON account:

EXAMPLE-1:
Transcript of session follows.

 Out: 220 mail.cerant.com ESMTP Postfix (Ubuntu)
 In:  EHLO [221.7.229.148]
 Out: 250-mail.cerant.com
 Out: 250-PIPELINING
 Out: 250-SIZE 10240000
 Out: 250-VRFY
 Out: 250-ETRN
 Out: 250-STARTTLS
 Out: 250-AUTH LOGIN PLAIN
 Out: 250-AUTH=LOGIN PLAIN
 Out: 250-ENHANCEDSTATUSCODES
 Out: 250-8BITMIME
 Out: 250 DSN
 In:  MAIL FROM:<upland@queue-systems.com>
 Out: 250 2.1.0 Ok
 In:  RCPT TO: <d54ffe8d@cerant.com>
 Out: 550 5.1.1 <d54ffe8d@cerant.com>: Recipient address rejected: User unknown
     in local recipient table
 In:  DATA
 Out: 554 5.5.1 Error: no valid recipients

Session aborted, reason: lost connection




EXAMPLE-2:
Transcript of session follows.

 Out: 220 mail.cerant.com ESMTP Postfix (Ubuntu)
 In:  EHLO [124.228.22.69]
 Out: 250-mail.cerant.com
 Out: 250-PIPELINING
 Out: 250-SIZE 10240000
 Out: 250-VRFY
 Out: 250-ETRN
 Out: 250-STARTTLS
 Out: 250-AUTH LOGIN PLAIN
 Out: 250-AUTH=LOGIN PLAIN
 Out: 250-ENHANCEDSTATUSCODES
 Out: 250-8BITMIME
 Out: 250 DSN
 In:  MAIL FROM:<fareda60@setiadi.net>
 Out: 250 2.1.0 Ok
 In:  RCPT TO: <sportscasts@cerant.com>
 Out: 550 5.1.1 <sportscasts@cerant.com>: Recipient address rejected: User
     unknown in local recipient table
 In:  DATA
 Out: 554 5.5.1 Error: no valid recipients
 In:  QUIT
 Out: 221 2.0.0 Bye

---

### Post by windependence on 2008-07-01
You may have an open relay on your server. they are trying to send spam through your server so that it looks like you are doing it. 

Go here to check if you have an open relay:

[http://www.abuse.net/relay.html](http://www.abuse.net/relay.html)

-Tim

---

### Post by MJN on 2008-07-01
It's just spam and you have, sensibly, not enabled a catch-all acceptance of e-mail for your domain.
 
Spammers will routinely attempt to send to randomly generated addresses as not only might they occasionally get a 'hit' (i.e. a valid e-mail address) but also many domains are configured to accept mail for anyone at that domain and, if not known, forward it to a specific account.
 
It's not an attempt at using you as a relay (i.e. using your server to send e-mail elsewhere) as cerant.com is your domain hence you are the final destination for mail destined to it.
 
Mathew

---

### Post by windependence on 2008-07-01
I agree with you, however, everyone running a mail server really should check for an open relay just to make sure it isn't open by accident.

-Tim

---


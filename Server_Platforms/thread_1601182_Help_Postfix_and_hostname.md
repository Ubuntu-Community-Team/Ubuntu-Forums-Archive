---
title: "Help: Postfix and hostname?"
date: 2010-10-19
forum: Server Platforms
---

### Post by leesiulung on 2010-10-19
I'm setting up an _outgoing only mail server_ for use with several websites hosted with apache on the very same server. Each site needs to send emails, and they need to originate from their respective site i.e. if the user hits reply it needs to to reply to an email address with the correct domain associated with that site.

I understand that somehow the hostname (found by typing hostname -f) is used in the header, but since I can only specify one hostname what should I do to ensure that the email originates from the correct site?

---

### Post by James78 on 2010-10-19
myorigin and mydestination

E.g.
myorigin = $mydomain
mydestination = $myhostname, localhost.$mydomain, $mydomain

... Unless you're using a VirtualDomain configuration, in which case I have it setup to use the regular hostname in myorigin, and mydestination is just...
mydestination = $myhostname, localhost.$mydomain
.. And everything works perfectly for me.

---

### Post by leesiulung on 2010-10-20
> **James78 said:**
> myorigin and mydestination

E.g.
myorigin = $mydomain
mydestination = $myhostname, localhost.$mydomain, $mydomain

... Unless you're using a VirtualDomain configuration, in which case I have it setup to use the regular hostname in myorigin, and mydestination is just...
mydestination = $myhostname, localhost.$mydomain
.. And everything works perfectly for me.

I'm sorry, but that just sounds all greek to me. I have no clue what you are talking about. I'm very new to this so don't be suprised. ;)

However, I am on a virtual domain i.e. hosting multiple domains on one ip using Apache and there in lies the problem. I don't want domain1.com to send an email from [email]support@domain2.com[/email].

---

### Post by leesiulung on 2010-10-20
So I did some research and I want to clarify a few things:


[LIST]
[*]I want to use virtual domain with postfix i.e. my multiple websites must be able to send an email from each their respective domains i.e. [email]email1@domain1.com[/email] is sent from my domain1.com website and [email]email2@domain2.com[/email] is sent from domain2.com website
[*]This is an outgoing mail server only i.e. I don't want any returned (or otherwise) email sent to my postfix server.
[*]Incoming mail is handled by Google Apps.
[/LIST]
I'm really confused on what to do, but attempted to follow a few tutorials. It now sends mail, but I have no clue if it is setup correctly.

---

### Post by SeijiSensei on 2010-10-20
How are the outbound messages composed and sent?  PHP?  Perl? A bash script? Something else?

In PHP, for instance, you can include a "From:" header as the last parameter in the mail() function.  So domain1 could send mail as "From: [email]info@domain1.com[/email]", domain2 sends as "From: [email]info@domain2.com[/email]", etc.

The "envelope sender" (the address that appears in the Return-Path header at the top of every email message) in all these cases will be something like [email]www-data@yourhost.example.com[/email], since Apache runs as user "www-data".  If you need the envelope sender to match the From: address you'll need to do some tricky configurations. I don't use Postfix, so I'm afraid I can't help you with those.

From experience, I can tell you that getting mail configured properly on a web server running multiple virtual hosts in different domains is not an easy task.  It requires support both in the email generation process and the SMTP server process as well.

---

### Post by leesiulung on 2010-10-20
> **SeijiSensei said:**
> How are the outbound messages composed and sent?  PHP?  Perl? A bash script? Something else?

In PHP, for instance, you can include a "From:" header as the last parameter in the mail() function.  So domain1 could send mail as "From: [EMAIL="info@domain1.com"]info@domain1.com[/EMAIL]", domain2 sends as "From: [EMAIL="info@domain2.com"]info@domain2.com[/EMAIL]", etc.

The "envelope sender" (the address that appears in the Return-Path header at the top of every email message) in all these cases will be something like [EMAIL="www-data@yourhost.example.com"]www-data@yourhost.example.com[/EMAIL], since Apache runs as user "www-data".  If you need the envelope sender to match the From: address you'll need to do some tricky configurations. I don't use Postfix, so I'm afraid I can't help you with those.

From experience, I can tell you that getting mail configured properly on a web server running multiple virtual hosts in different domains is not an easy task.  It requires support both in the email generation process and the SMTP server process as well.

I want the envelope sender to match the from address i.e. if I send it from [email]email1@domain1.com[/email], the return-path should be [email]email1@domain1.com[/email] and if I send it from [email]email2@domain2.com[/email], then similarly the return-path should be [email]email2@domain2.com[/email].

I really don't see why that should be hard? 

It must be a user interface issue that it is hard, if it is possible to do....

In terms of how I send it, most likely a PHP script or Java Servlet/JSP that sends the email.

---

### Post by James78 on 2010-10-20
> **leesiulung said:**
> I'm sorry, but that just sounds all greek to me. I have no clue what you are talking about. I'm very new to this so don't be suprised. ;)

However, I am on a virtual domain i.e. hosting multiple domains on one ip using Apache and there in lies the problem. I don't want domain1.com to send an email from [email]support@domain2.com[/email].
Those options go into main.cf.

Just press ctrl+f and do a search for both.
[http://www.postfix.org/postconf.5.html](http://www.postfix.org/postconf.5.html)

---


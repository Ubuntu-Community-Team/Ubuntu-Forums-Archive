---
title: "Which email server and how?"
date: 2009-05-09
forum: Server Platforms
---

### Post by michaelcole on 2009-05-09
Hi, I'm hosting simple websites (and DNS) for a long list of domains.

I want to allow a user to configure email forwarding for their domain from a custom PHP web page.  E.g.

*@blah.com -> [email]blah@gmail.com[/email]

It would be very easy to program if I could have this all in one config file that the email server used:  

*@blah.com -> [email]blah@gmail.com[/email]
*@foo.org -> [email]foo@hotmail.com[/email]
*@bar.net -> [email]bar.net@fastmail.fm[/email]
(everything else -> trash)

I won't host any IMAP/POP/SMTP for email clients.  It's forwarding only, and no local users.  

Each website has a email distribution list, but this isn't related.

What is the simplest possible setup you would recommend?  Postfix and exim4 seemed like overkill.  

Am I missing something?

Mike

---

### Post by HermanAB on 2009-05-10
There is nothing simpler than this:
[http://untroubled.org/nullmailer/](http://untroubled.org/nullmailer/)

---

### Post by trentscott4 on 2009-05-10
+1 for nullmailer

---

### Post by ejschaefer on 2009-05-10
Hello, 

Configuring Postfix with a MySQL back-end is a fairly easy task. With may actually be your best options, especially when automation is considered. You will need to configure Postfix to look at a MySQL DB for the transport map (which again is pretty easy). Documentation for this type of setup is widely available.

This will allow you to add/edit/delete your transport records through basic PHP/MySQL scripts.

mysql_table - Postfix MySQL client configuration
[http://www.postfix.org/mysql_table.5.html](http://www.postfix.org/mysql_table.5.html)

Postfix and Courier Installation using MySQL
[http://linux.justinhartman.com/Postfix_and_Courier_Installation_using_MySQL](http://linux.justinhartman.com/Postfix_and_Courier_Installation_using_MySQL)

Just my 2 cents :)

---


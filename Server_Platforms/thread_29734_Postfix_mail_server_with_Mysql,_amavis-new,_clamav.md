---
title: "Postfix mail server with Mysql, amavis-new, clamav, spamassassin, etc"
date: 2005-04-25
forum: Server Platforms
---

### Post by Eningo Montoya on 2005-04-25
Anyone have any suggestions/links on how to setup a mail server using postfix.  I tried using qmailrocks.org, but ran into dependency errors when I tried uninstalling postfix.

---

### Post by alastair on 2005-04-25
[http://www.postfix.org](http://www.postfix.org)
+
postfix users list archives
+
Google

Postfix is a great mail server with some great people behind it - including many useful docs. Good luck and come back if you get stuck.

---

### Post by Eningo Montoya on 2005-04-26
Well, I am stuck.  I have read all kinds of documentation about installing and configuring postfix, but none are as straightforward as the qmail documentation in qmailrocks.org.  Also, with qmail, I could just launch a web based application qmailadmin and add users to my domains, or vqadmin to add domains.  I don't see that ease of use for postfix.  Maybe I'm wrong (hope so).  Can anyone provide me with a link to a site that has postfix setup in such a way that you don't have to add a user to a database, then create the user directory - all manually?  It might be asking a lot, I don't know.

---

### Post by alastair on 2005-04-26
Sorry you are having problems. But a mail server is still something you need to think about a bit - it is best to understand the basic (text based) config. And Postfix is generally very straightforward.

I have heard that Postfix has a "webmin" based setup interface. Perhaps that would help?

---


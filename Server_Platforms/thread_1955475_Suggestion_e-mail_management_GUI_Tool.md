---
title: "Suggestion e-mail management GUI Tool"
date: 2012-04-09
forum: Server Platforms
---

### Post by fobus on 2012-04-09
Hello,

I'm using ubuntu on dedicated server, and managing it with webmin.
I was using a third party e-mail server but now I want to set up my own e-mail server.

I'm using postfix for smtp and Dovecot IMAP/POP3 Server. I don't want to create a linux user for each e-mail account, I want to store user accounts on MYSQL database.

Are there a web based GUI tool for managing e-mail accounts?

Thanks all.

---

### Post by CharlesA on 2012-04-09
Webmin would probably word, but I don't know if it will do what you want.

---

### Post by fobus on 2012-04-10
Yes, I can add/delete user accounts as e-mail accounts via webmin, but those accounts are native linux user accounts.

I want to store e-mail accounts in MYSQL and manage them with an GUI.

---

### Post by SeijiSensei on 2012-04-10
I took a quick look at [Citadel]("http://www.citadel.org"). It uses Berkeley db databases, not a relational one like MySQL.  But it does maintain its own set of user accounts independently from the operating system.

---

### Post by fobus on 2012-04-11
I found it, postfix admin can add domain,e-mail account, redirects etc..

[http://sourceforge.net/projects/postfixadmin/](http://sourceforge.net/projects/postfixadmin/)

---

### Post by HermanAB on 2012-04-11
The problem with Postfix is that the email is stored in the file system.  So if your HR manager sends the same 10MB MS Word file to all 25000 employees, then you need to run out to buy a new disk drive.

Citadel saves everything in a database, so in the above scenario, only one copy of the email is saved.

---

### Post by kevdog on 2012-04-11
I've got to take a look at this citadel mail server.  I've heard it mentioned several times.  Are there any limitations to this server as compared to postfix/dovecot?

---


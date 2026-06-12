---
title: "eMail Server"
date: 2011-03-15
forum: Server Platforms
---

### Post by WhiteElephant on 2011-03-15
I am looking to setup an email server but would like some suggestions as to which software to use.
 
I need:
POP
Secure POP
IMAP
Secure IMAP
SMTP
 
AntiVirus
AntiSpam
 
With the option to add user filters at a later date.
 
Webmail isn't needed as this is already hosted somewhere else.

---

### Post by HermanAB on 2011-03-16
Howdy,

Citadel does all that.  Either run the Easy Install script on the web site or install it from the repositories.

---

### Post by falko on 2011-03-16
You might also want to check out this guide: [Virtual Users And Domains With Postfix, Courier, MySQL And SquirrelMail (Ubuntu 10.10)]("http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-10.10")

---

### Post by HermanAB on 2011-03-16
Howdy,

Just bear in mind a fundamental difference between an enterprise grade mail server (Exchange, Citadel, Zimbra) and simple mail servers (Postfix or Exim):
If the HR manager sends an email to everyone in a company with 10,000 employees, then a Postfix or Exim server will store 10,000 copies of that message and you may need to run out and buy more disk drives.  
An enterprise type server will only save one copy of that email, since it uses a database for the mail.

---


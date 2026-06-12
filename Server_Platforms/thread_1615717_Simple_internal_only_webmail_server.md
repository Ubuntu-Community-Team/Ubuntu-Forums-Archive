---
title: "Simple internal only webmail server"
date: 2010-11-07
forum: Server Platforms
---

### Post by LittleLebowski on 2010-11-07
What is the fastest setup to do this? All I want is an internally authenticated webmail server that other servers can send mail to for collection of test emails. Don't need LDAP or anything fancy, just a internal LAN only webmail server. I've got Squirrelmail setup on Ubuntu Server and can't get authentication setup with Squirrelmail and every tutorial I read is way over complicated or has nothing on how to authenticate Squirrelmail with internal, system users.

  I am very short on time.....

---

### Post by HermanAB on 2010-11-07
Citadel of course. [http://www.citadel.org](http://www.citadel.org)

The easy install script takes about 20 minutes, after which you have a fully functional mail server than can handle hundreds of users and terabytes of mail, yet it is so small that had it running on an Eee PC 701 as a demo.

---

### Post by SeijiSensei on 2010-11-08
Do the users have accounts on the server?  Where are users authenticated now?

Usually the easiest solution is to create user accounts on the server running the IMAP daemon (e.g., dovecot).  

Do you need to authenticate SMTP transfers for some reason?  If the server is internal-only, it's easier just to grant blanket permission to the IP addresses or network block from which the messages will be sent.

---


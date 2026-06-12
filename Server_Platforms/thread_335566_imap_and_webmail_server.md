---
title: "imap and webmail server"
date: 2007-01-10
forum: Server Platforms
---

### Post by badjohny on 2007-01-10
I am looking for a Imap email server that also offers a web based interface.  I support a office of around 100 users, and 95% of the email use will be with a standard imap connection.  But some of my users have to work out of the office from time to time and need to access the email through a web browser.  I currently have openexchange 4.1 running, but it is showing its age.

I don't need calandars or group contacts.  Just email and webmail.  Any information would be greatly helpful.  

Bryan

---

### Post by mjm115 on 2007-01-10
> **badjohny said:**
> I am looking for a Imap email server that also offers a web based interface.  I support a office of around 100 users, and 95% of the email use will be with a standard imap connection.  But some of my users have to work out of the office from time to time and need to access the email through a web browser.  I currently have openexchange 4.1 running, but it is showing its age.

I don't need calandars or group contacts.  Just email and webmail.  Any information would be greatly helpful.  

Bryan

Well, Open-Xchange is at version 5.0, and it is a very good product.  Also, you can have a look at [http://www.howtoforge.com/ubuntu6.10_firewall_gateway](http://www.howtoforge.com/ubuntu6.10_firewall_gateway).  You can ignore the other sections that don't speak about e-mail.

Also, [ClarkConnect]("http://www.clarkconnect.com/info/features.php?type=apps") offers e-mail server capabilities.

Hope this helps you.

---

### Post by Brazen on 2007-01-10
On paper, I like eGroupware.  It is the best one I've seen that is completely free and opensource (no "commercial version" for added features, you get all the added features for free).

For the Commercial/Open combination suites, Zimbra looks to be the best by far (it did, after all, with the Sourceforge Community Choice Award).  Zimbra has a free/opensource version and then you can purchase support and additional components.

---

### Post by MJN on 2007-01-11
I would recommend taking a look at Dovecot for the IMAP server, and SquirrelMail for the webmail access to it.
 
Mathew

---

### Post by eric_stewart on 2007-01-11
I'm using Courier-MTA and SQWebmail.  Great, powerful combination.  Courier-MTA w/ SQWebmail is in the official Ubuntu package repositories too.  If you decide to go this route (there were excellent alternative suggestions, too!), make sure you install the web-based configuration menu, CourierWebAdmin.

/Eric
Read about my Ubuntu fun at the Breezy! Site:  [www.breezy.ca](www.breezy.ca)8)

---


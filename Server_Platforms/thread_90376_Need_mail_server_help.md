---
title: "Need mail server help"
date: 2005-11-14
forum: Server Platforms
---

### Post by nagual on 2005-11-14
I want to set up and email, and web server using ubuntu.  I have the base system installed, and am looking for recommendations on something that would be easy to set up.  I am going apache for the web server, but need mail server recommendations.

---

### Post by soce_32 on 2005-11-14
Postfix is the standard smtp server with Ubuntu.  Compared to Sendmail, it is very easy to setup.  It should work fairly well out of the box for a simple setup, but can be tweaked to include many other features if need be.

---

### Post by nagual on 2005-11-14
will postfix work for sending and recieving mail?

---

### Post by invalid on 2005-11-14
[http://home.kivu.nl/imap_setup.html](http://home.kivu.nl/imap_setup.html)

This is a good tutorial for a mail setup, written for a Ubuntu system - there are others, but this is the one I used.

Cheers,
Cb

---

### Post by nagual on 2005-11-15
Ok.  I have got to the fetchmail part, but when i issue the fetchmail -v command i get 

fetchmail: no mailservers have been specified.

Any suggestions?

---

### Post by nagual on 2005-11-15
Update.  I have got it setup, and can send mail just fine but cannot recieve it.  Any suggestions?  When trying to check mail i get an error scanning imap folders.  Connection timed out.

---

### Post by Jimzilla on 2005-12-08
I used postfix for smtp and courier for imap/pop3 mysql and phpmyadmin to administer virtual users and domains, works like a charm.

---


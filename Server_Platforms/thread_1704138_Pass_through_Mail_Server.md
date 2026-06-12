---
title: "Pass through Mail Server"
date: 2011-03-10
forum: Server Platforms
---

### Post by JoGm on 2011-03-10
Hi guys,


How do I make a local mail server that itself is a client to a WAN mail server.

I want the local mail server to query new mail every 30 minutes from the WAN server.



Kr,Aileen

---

### Post by mciverza on 2011-03-10
Fetchmail will be what is used to poll the remote WAN server.
You will (probably) also need postfix installed in order to send outgoing email
and you will definitely want Dovecot-IMAP installed so that clients can connect to your internal mailserver to read their emails.

---

### Post by mciverza on 2011-03-10
By the way if you're looking for a great Ubuntu-based server for your office that can already do the above.... check out Zentyal at [http://www.zentyal.org]("http://www.zentyal.org")

---

### Post by JoGm on 2011-03-10
Tnx in advance.... :)


Aileen

---

### Post by HermanAB on 2011-03-10
Fetchmail and Smarthost are the two features you need.  All self respecting mail servers can do that.

---

### Post by JoGm on 2011-03-11
TNx guys,


Do I need to use some scripting there? To connect fetchmail and smart host?



Kr,Aileen

---

### Post by HermanAB on 2011-03-11
Howdy, 

If you install Citadel, then you just configure fetchmail and smarthost in the web GUI webcit.  With Citadel, email is super easy.

[http://citadel.org](http://citadel.org)

Citadel has been around since some time before the dinosaurs, circa 1980.  It Just Works (TM).

---


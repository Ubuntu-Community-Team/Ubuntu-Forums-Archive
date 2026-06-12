---
title: "postfix config"
date: 2008-09-29
forum: Server Platforms
---

### Post by xxxYURAxxx on 2008-09-29
hi.

please help me.
when i do that on my localhost:
mail username@server
and fill fields, i am have new mail on server.

how do turn off receive messages from localhosts

---

### Post by alastair on 2008-09-29
Do you mean you do not want to receive mail locally? i.e. all mail is sent to an external email?

Add something to your alias file :

/etc/aliases 

e.g.

yourname:  [email]yourname@email.addr[/email]ess

and then run : sudo newaliases

If this is not what you mean, please explain.

Alastair

---

### Post by xxxYURAxxx on 2008-09-30
no, i was sent message from pc, which stays is in another network

---

### Post by xxxYURAxxx on 2008-09-30
i was search it on [http://www.postfix.org/postconf.5.html](http://www.postfix.org/postconf.5.html)

smtpd_client_restrictions = permit_mynetworks,permit_sasl_authenticated,reject_unknown_client_hostname

thanks

---


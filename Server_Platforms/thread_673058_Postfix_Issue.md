---
title: "Postfix Issue"
date: 2008-01-20
forum: Server Platforms
---

### Post by turtle02 on 2008-01-20
I am running 6.06 with dovecot imap pop3 server and postfix mail server installed. I am also administering all of this with webmin. I can receive emails just fine. when i log into webmin and click postfix and click user mailboxes and click on a user i see the email i have been sent, when i hit compose or reply the from address is user@mail (mail is the name of my server) if i backspace user@mail to say [email]user@mydomain.com[/email] i can send mail just fine. How can i change postfix to automatically put my domain name in instead of my server name?

---

### Post by MJN on 2008-01-20
You need to set the **myorigin** directive (e.g. **myorigin = mydomain.com**) as the default setting for this directive is $myhostname.

Any help?

Mathew

---

### Post by HermanAB on 2008-01-20
You can also configure a little file in the /etc/webmin directory to do the mapping - can't remember the details - google will find it.

Cheers,

Herman

---

### Post by turtle02 on 2008-01-20
I have changed the myorigin setting it is set correctly.

---

### Post by MJN on 2008-01-20
And does it now work?

If not, it sounds like a Webmin peculiarity so go with HermanAB's tip.

Mathew

---


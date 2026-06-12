---
title: "What to use for a mail server?"
date: 2007-04-08
forum: Server Platforms
---

### Post by Scooter7 on 2007-04-08
Hi, I'd like to set up a mail server on my Ubuntu Edgy install.   Something that would allow me to use my current domain t create a new email address would be preferable (i.e [email]mailuser@mydomain.com[/email]).   Also, perhaps one that's easy to set up?   If it allows multiple domains, that would be nice too.

Thanks,

   ~Scooter

---

### Post by bmathis on 2007-04-08
Postfix would work perfectly and its easy to setup once you get the hang of it. There are also tons of tutorials on this forum and the net!

---

### Post by grogoreo on 2007-04-09
I used this to setup Postfix and extras: [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) I find the MySQL integration the most useful of them since you can just create a script to add new users to the database.

---

### Post by huygens on 2007-04-10
[Ubuntu official documentation for the server edition]("https://help.ubuntu.com/6.10/ubuntu/serverguide/C/index.html") propose two possible mail server: postfix or exim.
Postfix was looking easier to install, IMHO. So I choose that one :-)
You can find the article directly here: [E-mail services]("https://help.ubuntu.com/6.10/ubuntu/serverguide/C/email-services.html")

---

### Post by gjtoth on 2007-04-12
> **Scooter7 said:**
> Hi, I'd like to set up a mail server on my Ubuntu Edgy install.   Something that would allow me to use my current domain t create a new email address would be preferable (i.e [email]mailuser@mydomain.com[/email]).   Also, perhaps one that's easy to set up?   If it allows multiple domains, that would be nice too.

Thanks,

   ~Scooter

This is a bit late but, have you looked at Axigen?  Full-featured and free for a home/small-office.  [http://www.axigen.com](http://www.axigen.com)

---

### Post by jimwillsher on 2007-04-12
Definitely Postfix. Very easy to set up, loads of resources on the web, and highly configurable IF YOU WANT IT TO BE. Very flexible.

I'm very happy with it, using it for about 50 email aliases for 4 people.

jim

---

### Post by salaberrios on 2008-01-12
Axigen is way easy for linux-stupid folks like myself. Could only get Postfix to start in CLI but thats about it...I get stuck at the MYSQL stuff.

---

### Post by HermanAB on 2008-01-12
If you want it all working yesterday, then use Citadel.  I've been using Postfix for many years and it really is good, but Citadel totally blows its socks off.

---


---
title: "ssl certs"
date: 2015-02-10
forum: Server Platforms
---

### Post by phs2004 on 2015-02-10
I tested enable ssl in apache2 and made a ssl cert. But in chrome that warning comes up "The Connection is not private"
Do need to buy ssl certs or is there a way to make one thats dosent show that warning? 

I have serached but there are så many hits on ssl certs for apache2.

---

### Post by Habitual on 2015-02-10
The connection is not private, or not secure?
You can make your own certs, but on public facing sites, some users won't trust them.
They are perfectly valid however.

Self-signed certs will show a Warning in the browser and ask the user if they wish to accept (grant an Exception) or sometimes "Get me out of here" (depends on the browser).
There is no way around the prompt for user intervention for self-signed certs.

---

### Post by phs2004 on 2015-02-10
> **Habitual said:**
> The connection is not private, or not secure?
l

Private, hmm going to test some more. But I wont buy a cert for my little server :) Just wanted to use encrypted ssl for exampel owncload and stuff, whit out that google chome warning.

---

### Post by Habitual on 2015-02-10
Owncloud has an ssl module, I believe.
[StartSSL]("http://www.startssl.com/?app=1") offers a free 1 year ssl

---

### Post by volkswagner on 2015-02-10
+1 for StartSSL

You'll need use a subdomain, but they do add the root domain as a secondary DNS to the cert.

---

### Post by phs2004 on 2015-02-10
Tanks! I´m going to test StartSSL i need ssl for both owncloud and roundcube. Hade it whit selfsign certs before the big crash, but then I used squirrelmail (from 2007) and owncloud 4 or somthing. Time to update everything. :)

---


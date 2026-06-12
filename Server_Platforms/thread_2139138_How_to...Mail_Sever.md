---
title: "How to...Mail Sever?"
date: 2013-04-26
forum: Server Platforms
---

### Post by totoy on 2013-04-26
Hey to all out there...
Can anyone here point me to the right direction or help me, I want to create my own mail server.
My current set up is, I am running Ubuntu server 12.04, with php5, apache2, mysql...etc and a bunch of security stuff for it is also running as  my
web server. Bought a domain name a couple weeks ago and hosted it with my own successfully. Now I want to create an email account using my own domain
eg. [email]me@mydomain.com[/email] and be able to store, send, receive, scan...all the stuff a mail server do.
I've scoured all over the net and found hundreds of tutorials but as I read up on a bunch of them...I got confused.
I just need a simple, easy and secure step by step guide.

Thanks

---

### Post by newbie-user on 2013-05-03
You need two things: 
1. a mail transfer agent (MTA), usually [postfix]("https://help.ubuntu.com/community/Postfix")
2. a mail delivery agent (MDA), [dovecot]("https://help.ubuntu.com/community/Dovecot") is an easy one

Optional third thing:
3. a web-based login such as [roundcube]("https://help.ubuntu.com/community/Roundcube") or [squirrelmail]("https://help.ubuntu.com/community/Squirrelmail")

---

### Post by CharlesA on 2013-05-03
newbie-user pretty much nailed it. Check the Ubuntu Server documentation or use something like iRedMail if you need to have a mail server up and running as soon as possible.

I checked out iRedMail on my VPS, but it was way too resource heavy for my needs.

---


---
title: "mail server that talks to MS active directory"
date: 2005-07-22
forum: Server Platforms
---

### Post by mtupker on 2005-07-22
Basically I'm trying to find a way to setup a email server but manage the user accounts through MS active directoty. I found this walkthrough [http://flurdy.com/docs/postfix/index.html#appB](http://flurdy.com/docs/postfix/index.html#appB) for setting up an email server with a web interface which is what I would like to do. I just would prefere not having to maitain two password databases if I can some how manage it all through AD. Any ideas, or am I just going to have to bite the bullet? Thanks in advance.

---

### Post by LordHunter317 on 2005-07-22
Look at setting up LDAP for authentication, which can be used to talk to active directory.

I know postfix can do it, but I don't know how to make it do it, sorry.

---

### Post by mtupker on 2005-07-22
Thanks for the reply. I'll look into it. :)

---


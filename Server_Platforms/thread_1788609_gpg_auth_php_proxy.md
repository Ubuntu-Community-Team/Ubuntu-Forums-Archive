---
title: "gpg auth php proxy"
date: 2011-06-22
forum: Server Platforms
---

### Post by mune on 2011-06-22
Hi all

I start with a description of my idea.

I want that everyone on the Internet when connecting at [http://sitename:sameportno](http://sitename:sameportno) gets a auth page that use the gpg keys like the description on the [page]("http://gpgauth.org/").

This component act as a proxy but all the communication are to a web application who accept only connections via localhost (from 127.0.0.1).

In this way *all* the web application can use the gpg auth.

As they already provide a php auth demo page, it seems to me trivial to add it in php proxy.

Does anybody know a simple one?

Thanks

Fede

---


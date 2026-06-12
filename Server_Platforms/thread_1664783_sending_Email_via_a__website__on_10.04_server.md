---
title: "sending Email via a  website  on 10.04 server ?"
date: 2011-01-11
forum: Server Platforms
---

### Post by toby53 on 2011-01-11
I setup ubuntu 10.04 / LAMP on a self managed cloud server (oh boy) and now I'm wondering what package(s) I should use for sending Email via an apache/php website ?

I hear postfix is good but don't know many of the tradeoffs and what packages are required. The volume is low. Any advice would be appreciated !

---

### Post by Thirtysixway on 2011-01-11
> **toby53 said:**
> I setup ubuntu 10.04 / LAMP on a self managed cloud server (oh boy) and now I'm wondering what package(s) I should use for sending Email via an apache/php website ?

I hear postfix is good but don't know many of the tradeoffs and what packages are required. The volume is low. Any advice would be appreciated !

You can run sudo tasksel -s (or maybe it's sudo tasksel -server? ) or just tasksel and select mail server.  Then when it asks, select Internet Site.  Then apache/php sites can send emails :)

---


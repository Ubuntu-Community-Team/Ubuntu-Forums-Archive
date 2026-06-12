---
title: "Need a &quot;stub&quot; package"
date: 2006-10-26
forum: Server Platforms
---

### Post by jacobmarble on 2006-10-26
Hey all-
  I am using Dapper Server on a headless x86 box as an SMTP server.  My MTA is postfix, but not the apt package; I prefer to download the postfix source and compile myself.  Now I want to install cyrus-imapd and cyrus-pop3d from apt, but postfix is a required package to cyrus.
  How do I tell apt 'hey, just ignore the postfix dependency!'.  Is there some kind of a 'stub' package that can satisfy this sort of problem?
  I've read the apt howto and a small handful of manpages, but I can't figure it out.

---

### Post by jacobmarble on 2006-10-26
*ahem*
[http://www.debian.org/doc/manuals/apt-howto/ch-helpers.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-helpers.en.html)

---


---
title: "Authentication Server on 10.04"
date: 2010-06-29
forum: Server Platforms
---

### Post by azan00 on 2010-06-29
Hello, I am currently setting up a small computer lab at my school. I am having trouble with it though, I attempted to get LDAP working, but there was too much to configure and it seemed like overkill for what we need. I also attempted to get ebox working, and I think I have an ebox ldap server working (I can browse the server using an ldap browser called luma). However I can't get clients to authenticate against it (they have trouble finding the server for some reason, yet I can perform an ldapsearch which works).

Someone had suggested I try NIS as it is simpler and more straightforward, but it would seem that the documentation on it is really outdated.

Does anyone have any recommendations? I don't need much, I just need to mount a users home directory on their clients from the server after they login. Clients will be using 10.04 as well. I have been looking for an easy to follow guide for NIS or LDAP, but nothing seems to work.

---

### Post by dragon_reborn on 2010-06-30
Try Webmin useful guide can be found here [http://woodel.com/](http://woodel.com/)

---


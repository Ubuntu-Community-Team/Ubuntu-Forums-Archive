---
title: "Using rsync + ssh instead of NIS?"
date: 2007-04-25
forum: Server Platforms
---

### Post by antigona on 2007-04-25
Hi

I have recently come across this setup. I just wanted to widely ask if there are any disadvantages using this mehod compared to NIS.

awating for your replays.

cheers.

---

### Post by Brazen on 2007-04-25
Well it depends.  If you are wanting Directory services, use NIS.  However it would probably be better to replace the directory services of NIS with LDAP and the name resolution services with DNS.

Rsync and ssh are for securing and tranfering files (ssh for encryption, rsync for transfer).  SSH will need some method of authentication which could be local users or NIS, etc.

---


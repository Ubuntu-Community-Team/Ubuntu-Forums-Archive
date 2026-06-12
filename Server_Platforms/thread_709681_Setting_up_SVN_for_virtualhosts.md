---
title: "Setting up SVN for virtualhosts"
date: 2008-02-27
forum: Server Platforms
---

### Post by moos3 on 2008-02-27
I have server with a single IP and have virtualhosts running for apache2. I need to setup a SVN server for each domain with each domain with ability set who can login to commit. Ideas on this? We have like 8 or 10 domains setup on the box right now and we would like to set up svn for 2 or 3 of them, for each development team of each repo.

---

### Post by Brazen on 2008-02-29
It should be pretty easy.  Check this out:  [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/version-control-system.html#access-via-webdav](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/version-control-system.html#access-via-webdav)

You should be able to put those Apache settings inside a virtual host.  Then you'll just want to specify a different AuthUserFile and SVNPath for each virtual host.

---


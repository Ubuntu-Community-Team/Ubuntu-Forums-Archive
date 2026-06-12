---
title: "SFTP Cluster"
date: 2007-12-08
forum: Server Platforms
---

### Post by DCM36 on 2007-12-08
Are there any guides out there on how to setup a Ubuntu (or Linux in general) cluster focused on being an SFTP server? I've googled and have yet to find anything of substance except for Windows Server 2003 stuff, and I'm not terribly interested in that..

Thanks for the help.

---

### Post by HermanAB on 2007-12-09
Hmm, it is too simple for anybody to write a book about.

Set up multiple identical SFTP servers.  Configure BIND to do round-robin DNS over the SFTP servers.

La Voila!

Herman

---


---
title: "Pure-ftp-mysql with with users not chrooted"
date: 2007-02-28
forum: Server Platforms
---

### Post by pietrob71 on 2007-02-28
I've have installed via apt-get pure-ftp-mysql on my Ubuntu Edgy and I manage the users in MySQL with "[User manager for PureFTPd]("http://machiel.generaal.net/index.php?subject=user_manager_pureftpd")"; all works fine.

I've have installed in the same way in an existent server with Ubuntu Dapper and all works fine, but when I enter via FTP in the server, I'm not chrooted in the user dir and I can see the entire filesystem. I've tried to reinstall the package, change the configurations in various ways, change permissions, but the problem is always the same.

---


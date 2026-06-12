---
title: "Server Edition and XFCE GUI"
date: 2008-01-03
forum: Server Platforms
---

### Post by jgcamp99 on 2008-01-03
OK, I've read and even accomplished installing the server edition (7.10) first and then the sudo apt-get install xfce desktop command to get the gui. 

My question is, for MySQL, the server edition installs for large table support beyond 4 GB. My understanding of the desktop installs, is that MySQL is limited to 4 GB. So when the XFCE desktop was installed later it obviously didn't do anything to MySQL at that time, or at least I hope it didn't, as the screen went pitch black 1/2 way thru the XFCE installation, but successfully installed blindly on it's own. But regarding updates, whenever an update that involves MySQL post XFCE installation, will the MySQL program update as it would for the server edition or desktop edition ? Certainly wouldn't want updates restricting database to 4 GB.

Why the > 4 GB, I'm trying to emulate a larger production database environment and I'm wondering if there's a simple way to verify large table support after the XFCE went on for MySQL ?

---

### Post by crouton on 2008-01-03
I wasn't aware there was a difference in the MySQL package, although it's likely that it is configured differently for server/desktop editions.  An old blog link [here]("http://jeremy.zawodny.com/blog/archives/000796.html") should give you some pointers on how to determine table size/limitations.  You may want to get on a MySQL IRC channel or cruise their forums for more information.

---

### Post by jgcamp99 on 2008-01-04
I saw that too on-line thru google searches. As for server vs desktop, there is a server kernel and desktop kernel, that much indicates a difference including that the only sofware on the server edition is server related applications. I recall reading that the MySQL that is freely distributable at the MySQL website has a limitation on how big databases can get. And I'm not sure where I read it in the past few days, but I recall specifically seeing that in the server edition "large table support" was configured for MySQL. To me it makes no sense for a database for a desktop be over 4 GB, but for a production level server, well at work we have one that's close to 160GB amongst others in SQL Server 2K5 Enterprise.

Anyway, maybe someone with Canonical can shed some light on the subject ?

---


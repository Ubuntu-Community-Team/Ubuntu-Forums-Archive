---
title: "MySQL 4.0.23 to MySQL 4.1.10 upgrade help?"
date: 2005-06-16
forum: Server Platforms
---

### Post by dudinatrix on 2005-06-16
I've got Ubuntu's MySQL 4.0.23 installed with data on my system.  I need to upgrade to MySQL 4.1.10, but I'm unsure how to go about it.

I see it in Synaptics (universe), but how do I upgrade to it while keeping my data?   There's no "upgrade" option since it's a different package.

How do I upgrade?  What happens to my MySQL 4.0.23 installation?

---

### Post by LordHunter317 on 2005-06-16
I haven't looked at the package setup in a while, but the two installations should be laid out next to each other, using the same data files.

I don't remember if a backup/restore will be required (take a backup anyway).  

It ought to be as easy as install mysql-4.1, point it at the right data location, and run it.  I may be forgetting something though, check the MySQL documentation on doing the upgrade.

---

### Post by relix42 on 2005-06-17
The authentication types changed as well.  So, make sure you myslqdump all your databases as well as the mysql database (authentication information).

I've done the upgrade a few times (different distributions as well as binary packages) and always found something that didn't quite transfer correctly.  So, backup and plan extra time.

In addition, if your connecting to your MySQL server with another application (PHP. C app, etc) you may have trouble accessing the MySQL server.  A quick fix is to update the users using the OLD_PASSWORD SQL command or compile/install a newer version of you application that is linked to the 4.1 libraries.

Best of luck.

---


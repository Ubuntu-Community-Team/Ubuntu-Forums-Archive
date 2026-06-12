---
title: "Sharing database tables between projects"
date: 2010-01-05
forum: Server Platforms
---

### Post by Vegan on 2010-01-05
If any real hassle using a database between web sites. Not obviously phpBB but rather various projects that need a common read access to maintain a relation.

Anyone try this?

---

### Post by BkkBonanza on 2010-01-05
Do you mean using mysql for multiple sites, or do you mean using some particular database for multiple sites? There shouldn't be a problem with either but there are some constraints dependent on the storage engine in use. MyIsam does table file locking during writes and if multiple sites were using the same tables then it could be adverse to performance. In most applications writes are far less common than reads so this isn't generally a problem. If using the InnoDB storage engine then it does record level locking and this is more efficient for apps that do a lot of concurrent updating.

Unless different web sites need to update the same data most apps will have their own database and so several web sites would not share their databases. There is no problem with this under MySql. In fact, that's what it's designed to do. Some shared servers run hundreds of databases under one instance of MySql.

---


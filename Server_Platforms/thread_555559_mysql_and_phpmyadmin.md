---
title: "mysql and phpmyadmin"
date: 2007-09-20
forum: Server Platforms
---

### Post by nebi on 2007-09-20
When you login with phpmyadmin with any user you can se all database on the server , how do i fix so you only can see your own database ?

---

### Post by Brazen on 2007-09-20
Go to the user's privileges, be sure to uncheck all for the server privileges and then add database privileges for just their database.

---


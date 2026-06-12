---
title: "Backup database"
date: 2008-06-29
forum: Server Platforms
---

### Post by leewilson78 on 2008-06-29
Hi all, 

I am doing a backup of my Ubuntu server, I have taken a copy of the home directory, I now need to take a copy of all client databses, how can I do this.

I have looked around, noticed there are ways to transfer between server, however, I just need a zip of the databases on the same server.

Thanks
Lee

---

### Post by HalPomeranz on 2008-06-29
You don't say what kind of database, but if it's MySQL you want to use the mysqldump command.

---

### Post by leewilson78 on 2008-06-29
Apologies, they are indeed MySql databases. I have no idea where they are stored on a ubuntu server though.

Hope you can help.

Thanks
Lee

---

### Post by mrpeenut24 on 2008-06-29
On the server do the following:

```

mysqldump --all-databases -u *username* -p > out.sql

```
Then when you want to restore it, do the following:

```

mysql -u *username* -p -e "source out.sql"

```
Be sure to use the username of a mysql user with all privileges.

---

### Post by leewilson78 on 2008-06-29
I entered the following:

mysqldump --all-databases -u root -p > out.sql

I was then prompted for a password, which I entered, I then got the following:

mysqldump: Got error: 1045: Access denied for user 'root'@'localhost' (using password: YES) when trying to connect

Hope you can help.

Thanks

---

### Post by mrpeenut24 on 2008-06-29
Did you ever set up the root password?

Try this:

```

mysqladmin -u root password NEWPASSWORD

```

---


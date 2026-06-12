---
title: "Help recovering mysql database"
date: 2010-07-26
forum: Server Platforms
---

### Post by computx on 2010-07-26
My server's hard drive crashed the other day. I wasn't able to recover enough to make the system bootable but I did get a copy of my /var/lib/mysql directory and the /var/www directory.
I installed 10.04 to a new drive and am in the process of putting things back together. The question I have is, what is the proper way of putting the mysql databases back in place? I tried just copying the folders back to /var/lib/mysql but mysql still didn't think the databases exist. Unfortunately I can't do the standard restore from backup.

---

### Post by Ryan Dwyer on 2010-07-26
Don't copy the "mysql" or information_schema databases. They get generated automatically. Copy everything else to /var/lib/mysql, then change the owner of those files to mysql. The mysql user should also own the /var/lib/mysql directory itself.

---

### Post by computx on 2010-08-02
Thanks, I am currently trying to get a backup i found of the ubuntu installed working. Good info though!

---


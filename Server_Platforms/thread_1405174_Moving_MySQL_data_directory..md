---
title: "Moving MySQL data directory."
date: 2010-02-12
forum: Server Platforms
---

### Post by jargs on 2010-02-12
Hello,

I am running debian and am trying to move the mysql data directory. 

I went into the my.cnf and changed it from "/var/lib/mysql/" to "/home/mysql/". I copied the contents of the old data directory over, then gave the mysql user owner of the new directory using "chown -R mysql /home/mysql/*". 

When I restart mysql, it fails to start up for some reason and does not give me any error message, just says "starting mysql........failed". 

I also read on some tutorials that i needed to only copy certain files (the database files) from the old dir to the new one, other tutorials told me to copy the whole folder, I tried both and that doesn't change anything.

Thanks for your time.

---

### Post by noway2 on 2010-02-12
I haven't tried it, but I understand that the way to copy a MySQL database is to use the dump command to create an archive and then restore it.  I don't know the command syntax, otherwise I would give you an example.

---

### Post by jargs on 2010-02-12
no i am not trying to export it, i need to move the actually database files themselves.

---


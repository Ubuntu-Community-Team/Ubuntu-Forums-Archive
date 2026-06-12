---
title: "recreating database from MYD, MYI .. files"
date: 2008-04-07
forum: Server Platforms
---

### Post by shahansudu on 2008-04-07
Hi, 
    I'm not very familiar with MySQL. A database I've been using has been moved from one server to another. I have the MYI, MYD, frm, opt files for each database I had. But I dont know how to create the database from those files. Can any one help me?. Thank you

---

### Post by curtishall on 2008-04-07
Technically if you just copied the entire mysql directory you can start mysql on the new box if it's properly configured.  This isn't the correct way to do this and you should dump and backup each database.  You will need to verify, test, and optimize each database once you can successfully start mysql



> **shahansudu said:**
> Hi, 
    I'm not very familiar with MySQL. A database I've been using has been moved from one server to another. I have the MYI, MYD, frm, opt files for each database I had. But I dont know how to create the database from those files. Can any one help me?. Thank you

---


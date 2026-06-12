---
title: "MySQL Character issue"
date: 2007-02-26
forum: Server Platforms
---

### Post by el_rata on 2007-02-26
i'm building a server to host a website for the company i'm working for, for that i used Edgy Server with LAMP. I'm having problems reading the MySQL database, it reads and writes perfectly, but when i show the data it doesn't show spanish characters. I tried changing the character using phpMyAdmin (editing the field in the table) it and it shows good for the user but not for the admin. Example:

Before the change:
User reads: (square char)
Admin reads: á

After the change:
User reads: á
Admin reads: Á!

!!!!!!!!

i don't know what to do with this, i don't even know where the problem is or where to correct this, and i have to have the server running soon.

---

### Post by userundefine on 2007-02-26
Make sure your DB is utf-8;
Make sure content-type is utf-8 in headers;
Make sure any POST data is in utf-8.

---

### Post by el_rata on 2007-02-26
i had it working about an hour later after this post ... thanx anyway ... and my trouble was the default charset in the apache2.conf ... 

THNX!!

---


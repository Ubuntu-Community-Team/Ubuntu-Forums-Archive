---
title: "mysql root password reset hangs?"
date: 2011-07-16
forum: Server Platforms
---

### Post by Tijmens on 2011-07-16
I forgot my root password for mysql, and after some searching I found several solutions to fix it. But none of them seem to work. 

I tried this article [http://ubuntu.flowconsult.at/en/mysql-set-change-reset-root-password/](http://ubuntu.flowconsult.at/en/mysql-set-change-reset-root-password/) with starting mysql with the --skip-grant-tables option. The problem is that nothing happens, it just hangs. 

Also tried the the --init-file option, that one runs fine, at least it returned to the command line. But the sql query in the file to which it point doesnt seem to do anything. The password wasn't changed to the one I specified in the sql file.

Any idea what could be going on here, and how I could fix it?

---

### Post by Wim Sturkenboom on 2011-07-17
I don't think it just hangs; if I recall correctly, you don't see the command prompt if you manually start the mysql server. Press <enter> and you should get your command prompt back (and the mysql server keeps on running in the background).

PS
Did you try to connect (e.g. using the mysql client in another terminal) while it is hanging?

---

### Post by Tijmens on 2011-07-17
Opening another terminal did the trick, thanks :)

---

### Post by Wim Sturkenboom on 2011-07-17
Graag gedaan ;)

Great; I know it's confusing that you don't get the command prompt back.

Please mark your thread as solved using the threadtools just above the first post.

---


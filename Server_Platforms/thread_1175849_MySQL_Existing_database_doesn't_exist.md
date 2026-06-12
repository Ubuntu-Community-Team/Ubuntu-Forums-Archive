---
title: "MySQL Existing database doesn't exist"
date: 2009-06-01
forum: Server Platforms
---

### Post by TyPR124 on 2009-06-01
This seemed like the best place to post this, but if I'm in the wrong section please move this. I'm not actually using server edition, but it is server related.

Right now, MySQL is telling me that a database exists and doesn't exist at the same time...

"Can't drop database 'localServer'; database doesn't exist"
"Can't create database 'localServer'; database exists"

I can't add any tables, and it says all the table that used to be in it are gone. I can't delete it, and I can't create it. I'm not particularly worried about the database itself as it was only for some testing, but the problem is the fact that MySQL says its there and not there at the same time.

I'm guessing there is probly some file somewhere where records are kept. So if I could find that file and delete the localServer database entry, would that solve the problem (and if so, where would that file be?) Is there anything else I could try to fix it?

BTW, if it helps, the last thing I was optimize it, though I didn't notice it until somewhat later.

---

### Post by bluefrog on 2009-06-02
/var/lib/mysql/

---


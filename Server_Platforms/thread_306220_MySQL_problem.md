---
title: "MySQL problem"
date: 2006-11-24
forum: Server Platforms
---

### Post by jms1989 on 2006-11-24
I deleted my mysql database and I have a backup in the sql form, but I can't restore it. I'm trying to downgrade it to 4.1 from 5.0 to be compatible with vhcs. How can I restore it? Help, in crisis.

---

### Post by elst on 2006-11-24
Could you post the error message that you get? If the backup is in SQL form then it should be OK, although you might have to do a couple of edits.

---

### Post by jms1989 on 2006-11-25
> **elst said:**
> Could you post the error message that you get? If the backup is in SQL form then it should be OK, although you might have to do a couple of edits.

I restored my pc from a backup, so when it did occur it world tell me "Unknown database "MySQL"" when I tried to do anything to MySQL. The problem has been fixed by doing a restore. Now I just trying to work out the vhcs2 bugs.

---


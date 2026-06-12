---
title: "[SOLVED] MySQL Import / Export"
date: 2008-11-25
forum: Server Platforms
---

### Post by CrusaderAD on 2008-11-25
Is there an Import / Export feature in MySql Administrator? I only see backup / restore.

---

### Post by divinequran on 2008-11-25
You can use mysqldump to take backup or export database.

---

### Post by CrusaderAD on 2008-11-25
When I try and restore the backup up database, I get an error:

Error: Invalid character set selected for file.

I selected utf8. I think the source is MyISAM but there isn't a selection for that type.

---

### Post by CrusaderAD on 2008-11-25
In reference to my last post, I selected latin1 and it restored the backup.

---

### Post by Thirtysixway on 2008-11-25
PhpMyAdmin has an export/import feature.

---

### Post by CrusaderAD on 2008-11-26
Thanks! Problem Solved.

---


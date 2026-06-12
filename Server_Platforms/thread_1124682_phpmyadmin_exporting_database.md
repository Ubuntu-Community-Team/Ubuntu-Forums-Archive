---
title: "phpmyadmin exporting database"
date: 2009-04-13
forum: Server Platforms
---

### Post by jeff00z28 on 2009-04-13
When i export the data as a .sql file and save it to a windows machine, i open it up and it is just corrupted. anyone know how to fix this? i rly need to back up my data

---

### Post by mrsteveman1 on 2009-04-13
It is recommended that you use the mysqldump tool to export databases, especially if they are large. We have a few that aren't HUGE by any measure, but they are way too big for exporting with phpmyadmin.

As for corruption issues, it's hard to say what the problem is, but i would remove the phpmyadmin tool from the equation and see if you can simply get a clean sql file with the commandline tools. Sometimes there are issues with transferring files as binary or ASCII mode but i don't think a browser would suffer from that issue.

---

### Post by hyper_ch on 2009-04-14
because of the character scheme.... linux=utf8, windows=iso-(something). So if you dump it on linux on open it on windwos you'll first need to convert the characters.

---

### Post by jeff00z28 on 2009-04-14
any way to convert this in Windows? i would like to just back up the database to my desktop pc. this is a ticket database for IT tickets

---

### Post by mrsteveman1 on 2009-04-15
Do you actually need to open it in windows or just keep a backup? The file should be fine even if the encoding is different.

---

### Post by Thirtysixway on 2009-04-16
You can export to other formats.  Text, pdf, cvs, or spreadsheet are good if you need to just look at information on the windows machine.

If you're just looking to keep a backup, like mrsteveman1 said just don't open the file as there is no need to.  It will still import properly into phpmyadmin.

---


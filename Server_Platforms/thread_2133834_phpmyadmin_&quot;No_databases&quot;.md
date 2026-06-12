---
title: "phpmyadmin &quot;No databases&quot;"
date: 2013-04-09
forum: Server Platforms
---

### Post by hadiaj168 on 2013-04-09
Hi!
after i changed my default mysql datebase directory, phpmyadmin show this message in left side:
 "No databases"
i cant find any setting in config file to solve it.
excuse me for my bad english!

---

### Post by SeijiSensei on 2013-04-09
Isn't the simplest solution to this problem simply moving the database back to /var/lib/mysql?  Why move it at all?

If you want to put the database on a separate drive or some other filesystem, mount that device to /var/lib/mysql.

---


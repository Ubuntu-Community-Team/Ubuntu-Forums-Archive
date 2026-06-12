---
title: "Apache Errors"
date: 2007-01-24
forum: Server Platforms
---

### Post by SVFUSiON on 2007-01-24
Warning: Unknown(/var/www/index.php): failed to open stream: Permission denied in Unknown on line 0

I am getting these errors when tring to install phpbb2.

Warning: (null)(): Failed opening '/var/www/index.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

Any ideas?

---

### Post by jtc on 2007-01-24
Do you have open_basedir set? If that's not the cause, I'd guess on the file (index.php) not having enough generous rights.

---

### Post by SVFUSiON on 2007-01-24
what rights/command would I need to give it that would be safe.

---

### Post by jtc on 2007-01-24
Assuming you run PHP as mod_php I'd say...

```
chmod 0644 /var/www/index.php
```

(owner: read & write, group: read, others: read)

---


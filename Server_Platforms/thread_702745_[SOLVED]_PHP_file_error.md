---
title: "[SOLVED] PHP file error"
date: 2008-02-20
forum: Server Platforms
---

### Post by youaredoome0 on 2008-02-20
```
Fatal error: Unknown: Failed opening required '/var/www/index.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0
```
I get this error when i try to access the PHP test page. Neither file, /usr/share/php or /usr/share/pear, exists.

---

### Post by Bliepo32 on 2008-02-20
Could you please post the PHP file? And did you install PHP and Apache from source, or did you use the package manager?

---

### Post by youaredoome0 on 2008-02-20
Oh, wait, Apache didn't have permission to access the php file. Thanks anyway.

---


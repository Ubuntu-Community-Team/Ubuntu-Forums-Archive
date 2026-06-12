---
title: "Problems with PHP..."
date: 2008-02-02
forum: Server Platforms
---

### Post by Nexus5.01 on 2008-02-02
Well I set up PHP and apche but when i access "test.php" using local host instead of showng it it wants me to download it and the same with windows.

What am I doing wrong?

---

### Post by Dr Small on 2008-02-02
Are you sure that Php is running ?

---

### Post by kool_kat_os on 2008-02-02
Ya, you dont have php installed probably

---

### Post by Nexus5.01 on 2008-02-03
How do I know if PHP is turned on?

---

### Post by Dr Small on 2008-02-03
This may return results:
```
ps aux | grep php
```

And to start php, it may be:
```
sudo /etc/init.d/php start
```

---

### Post by rockrocket on 2008-02-03
Maybe if you try to remove php and then install it again it will fix the problem.

---


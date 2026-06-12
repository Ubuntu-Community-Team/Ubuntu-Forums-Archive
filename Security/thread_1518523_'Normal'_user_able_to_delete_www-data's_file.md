---
title: "'Normal' user able to delete www-data's file"
date: 2010-06-26
forum: Security
---

### Post by den_ on 2010-06-26
Hi,

I am not sure if this is a nomal behaviour and that is the reason I am posting it here and not as bug in launchpad.

```

htdocs$ ls -l testFile.txt 
-rw-r--r-- 1 www-data www-data 78 2010-06-24 01:48 testFile.txt
htdocs$ rm testFile.txt 
rm: remove write-protected regular file `testFile.txt'? y
htdocs$ ls
css  favicon.ico  images  index.php  js  sign.png
```

---

### Post by sisco311 on 2010-06-26
Without the sticky bit set, any user with write and execute permissions for the directory can rename or delete contained files, regardless of owner.

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

---

### Post by den_ on 2010-06-26
Thank you sisco311.

---

### Post by Bachstelze on 2010-06-28
> **sisco311 said:**
> Without the sticky bit set, any user with write and execute permissions for the directory can rename or delete contained files, regardless of owner.

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

"Any user with write access", the execute bit is irrelevant here.

---

### Post by sisco311 on 2010-06-28
> **Bachstelze said:**
> "Any user with write access", the execute bit is irrelevant here.

Nope.  To create new files or delete files, you need write access to the directory. You also need execute access to all parent directories back to the root.

```
mkdir -p dir/foo/bar
> dir/foo/bar/file
chmod 0220 dir/
rm dir/foo/bar/file
rm: cannot remove `dir/foo/bar/file': Permission denied

```

---


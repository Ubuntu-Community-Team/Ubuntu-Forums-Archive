---
title: "chown multiple files multiple directories"
date: 2010-02-19
forum: Server Platforms
---

### Post by Tekman_1 on 2010-02-19
Hello All,

I have a vary unique problem with file and directory ownership. I need to change the ownership of multiple files and directories under a specific subdirectory.

Under this directory structure there are files and directories owned my different users and groups. I need to change all files and directories owned by "user1" to "user2". but if any are owned by "user3" I need those left alone.

Is there a simple way to do this or will I need to traverse the structure and change things one at a time.

Thanks in advance.

---

### Post by yota on 2010-02-19
you can do something like this:
```

find /path/to/dir -user user1 -exec chown user2 {} \;

```

where "{}" means "the found file" and "\;" is the terminator for exec statement.

"man find" for details.

Hope this helps!

---

### Post by Tekman_1 on 2010-02-19
yota,

Thanks for the quick reply. Worked perfectlly.

Thank you.

---

### Post by leonbravo on 2011-07-21
awesome :popcorn:

---


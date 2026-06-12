---
title: "Compare many files between Ubuntu servers"
date: 2019-08-24
forum: Server Platforms
---

### Post by sed_faster on 2019-08-24
Hello,

I intend compare a large of numbers of the files between servers (Ubuntu Servers). The all files it is almost 3TB. After googled about this issue I finished with this command:
```

diff -ryq /home/folder/ <(ssh gd@192.168.1.1 'cat /home/folder/)

```

But I'm not sure if it works.
How can I compare the 3TB of files between the two linux servers?

Thanks

---

### Post by TheFu on 2019-08-25
I'd get a list of different files first using **rsync** in dry-run mode.
Depending on the types of files (binary, text, something else), I'd use a different tool.  Might use a VCS if the files are text.

---


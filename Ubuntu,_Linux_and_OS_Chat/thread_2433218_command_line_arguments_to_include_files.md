---
title: "command line arguments to include files"
date: 2019-12-15
forum: Ubuntu, Linux and OS Chat
---

### Post by Skaperen on 2019-12-15
a command i am creating (for cloud automation) needs to be given quite many arguments.  it can make sense to store many of them (that the user rarely changes between commands) in one or more files.  bash already has a means to read a file and include it in the command line:
```

dothis foo $(cat filename) bar

```
i am thinking about a way to make this easier for the user in the code of this big command:
```

dothis foo @filename bar

```
what i am wondering is, would @ be a decent prefix character for this feature or should i consider using some other character?  obviously, the choice has to be something the shell does not treat as special.

---

### Post by TheFu on 2019-12-15
-c  or --config= would be common, right?   Getopts will make handling long and short options easy.

---

### Post by Skaperen on 2019-12-16
but will getopts automatically read more options as inserted inline, from the designated file?

---


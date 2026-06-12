---
title: "How can I scramble access times and"
date: 2009-12-18
forum: Security
---

### Post by shaggy999 on 2009-12-18
Does anybody have an idea of how I could scramble access time and modification time data on an entire directory of files?

---

### Post by blackmail on 2009-12-18
If you want you could take a look [here]("http://linux.die.net/man/1/touch"), I think it would help you further.

---

### Post by Agent ME on 2009-12-18
This command will update the modification and access times of all contents of a folder to the present time. You can use a single period "." to represent the current folder.
```
find somefolder -execdir touch -c '{}' +
```

---


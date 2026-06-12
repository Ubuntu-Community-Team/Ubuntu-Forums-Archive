---
title: "Not recognizing dvd drive"
date: 2013-02-15
forum: Ubuntu Studio
---

### Post by swansonkts on 2013-02-15
I am wondering if it is normal for ubuntu to not recognize files that are on a dvd that was made in windows. How do I read the dvd?:confused::confused:  Just to let you know, I'm a total newb to linux

---

### Post by jejeman on 2013-02-15
There should be no difference where DVD was made. All systems should read it.

---

### Post by swansonkts on 2013-02-15
> **jejeman said:**
> There should be no difference where DVD was made. All systems should read it.
  I appreciate the response. I have 2 dvd's that have videos I downloaded from youtube and I cannot view either dvd in ubuntu. not sure what to do. Is there a command line I can use to view the files?

---

### Post by jejeman on 2013-02-16
You can look in kernel ring buffer what is going on.
```
dmesg
```
Insert DVD, close the door, wait 1 minute, run the command.

---


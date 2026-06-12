---
title: "start cmd File not found"
date: 2010-03-21
forum: Wine
---

### Post by leniviy on 2010-03-21
Hi! Can someone who already has wine 1.1.41 run a test?
in terminal do: wine cmd
then: start cmd
A new command prompt should open, but I get "File not found" error. In 1.1.40 it works, but not in 41. And no one believes me >_<

fail:
```

# wine cmd
CMD Version 1.1.41


C:\>start cmd
File not found


C:\>

```OK:
```

# wine cmd
CMD Version 1.1.40


C:\>start cmd
fixme:exec:SHELL_execute flags ignored: 0x00000100

C:\>

```

---


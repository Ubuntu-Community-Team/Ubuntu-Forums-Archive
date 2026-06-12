---
title: "clarifying the winedebug command"
date: 2009-04-30
forum: Wine
---

### Post by loganp82 on 2009-04-30
So after searching the internet about the command WINEDEBUG that you put in your shortcuts for better performance I've noticed many inconsistincies with the command. Here's a list of variants I've found that people say to use:
WINEDEBUG=-fixme-all
WINEDEBUG="-fixme-all"
WINEDEBUG=-all
WINEDEBUG="-all"

So.....what I'm wondering is which command WORKS. Are the quotes needed? is the fixme part needed? Any clarification would be greatly appreciated.

---

### Post by cogadh on 2009-04-30
You don't need the quotes around the debug parameter. By specifying the removal of a certain debug channel like "-fixme", you are only supressing messages with that prefix, but all other messages are allowed, which is really only useful if you are troubleshooting a specific problem. To get the potential performance improvement, you should use the "-all" option, which basically turns off debugging:
```
WINEDEBUG=-all wine foo.exe
```

---

### Post by loganp82 on 2009-04-30
Thank you sir :)

---


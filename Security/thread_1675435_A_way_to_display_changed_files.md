---
title: "A way to display changed files?"
date: 2011-01-25
forum: Security
---

### Post by zanzes on 2011-01-25
is there a way to display a list of all the files changed during current session?

---

### Post by ajgreeny on 2011-01-25
I am not sure how you can do it for the current session, but files created and therefore, I assume, those modified as well will be listed in a file called newfiles.txt by ```
find -type f -mtime 0 > newfiles.txt
```  I am sure there must be a similar command that can do it either for a current session or by a time variable.

---

### Post by FuturePilot on 2011-01-25
> **ajgreeny said:**
>  I am sure there must be a similar command that can do it either for a current session or by a time variable.

```
find . -type f -mmin -time_in_minutes
```
-60 will show everything modified within the last 60 minutes, -120 in 2 hours etc.

---

### Post by ajgreeny on 2011-01-25
Thanks FP, I hadn't got round to looking for that yet, but had assumed it was something like your command.

What about per session, if you have had a long uptime and can't remember how long it is since you last did a full boot?

---

### Post by FuturePilot on 2011-01-25
> **ajgreeny said:**
> Thanks FP, I hadn't got round to looking for that yet, but had assumed it was something like your command.

What about per session, if you have had a long uptime and can't remember how long it is since you last did a full boot?

No idea. I guess you could possibly find out when you last logged in (with 'ps' perhaps) and do some math. I don't know of any way to do it by session time though.

---


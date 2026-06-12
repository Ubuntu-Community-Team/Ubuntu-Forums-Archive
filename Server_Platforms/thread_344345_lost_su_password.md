---
title: "lost su password"
date: 2007-01-22
forum: Server Platforms
---

### Post by Sniper99 on 2007-01-22
hi, i have had my linux for a while now, and i have just started really getting into it, and i unfortunately forgot one of the most important passwords on the machine, i can do admin tasks and stuff, but its just that if i type in su in the terminal, i cannot remember my password, i have tried every single password that i have ever used in the past(like 8), and it still wont give, anybody know any kind of su password cracker......

---

### Post by jtc on 2007-01-22
...but you can do administrative tasks you say? Then you still have a useraccount with full sudo rights? In that case the solution should be fairly simple.

```
sudo passwd root
```

---


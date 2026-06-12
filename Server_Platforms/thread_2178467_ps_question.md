---
title: "ps question"
date: 2013-10-03
forum: Server Platforms
---

### Post by remo2 on 2013-10-03
When you give the command ps aux, so what does that tell you?
How does the command ps-el differs from the previous one?
When you connect to server, and type the command ps aux, what happens?

---

### Post by Kirboosy on 2013-10-03
Welcome to the forums!

aux -- To see every process on the system using BSD syntax:

```
ps aux
**USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND**
```

ef --  To see every process on the system using standard syntax:

```
ps -ef
**F S   UID   PID  PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD**
```

Hope that helps!
~Caboose
PS if you would like more information try using the man pages.
```
man ps
```
Pressing 'Q' will close the man pages for you when you are done.

---

### Post by Lars Noodén on 2013-10-03
Two others that are useful would be **pgrep** and **top**.   

```

pgrep -lf firefox 

```

---


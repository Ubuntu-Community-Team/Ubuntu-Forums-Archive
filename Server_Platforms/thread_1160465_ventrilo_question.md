---
title: "ventrilo question"
date: 2009-05-15
forum: Server Platforms
---

### Post by Willn21 on 2009-05-15
hi guys i am new to ubuntu server.

I installed ventrilo on my ubuntu server

What i do is ./myventrilodirectory/ventrilo_srv

that runs the server and it works great my question is
[COLOR=Red]
1. once the server is running how can i get out of it and still have it run in the background
2. how can i get it to run on start up[/COLOR]

---

### Post by Willn21 on 2009-05-15
bump

---

### Post by Kareeser on 2009-05-15
Ctrl-Z to pause it, and then type "bg" to push the "job" into the backgroud.

You can read up on it by typing "man jobs" into the terminal.

To run it in the background from the beginning, append an amperstand (&) to the end.

---

### Post by Willn21 on 2009-05-16
ok after i get it in the background how can i bring it back up again.

---

### Post by llamaX on 2009-05-16
To answer your question, see [this]("http://web.mit.edu/gnu/doc/html/features_5.html").  However, the nicer solution would be to use something like screen or dtach.

With screen, you could start a detached session as:
```
screen -d -m -S vent /path/to/ventrilo_srv
```And reattach it as:
```
screen -r vent
```See [man screen(1)]("http://linux.die.net/man/1/screen") for more.

---


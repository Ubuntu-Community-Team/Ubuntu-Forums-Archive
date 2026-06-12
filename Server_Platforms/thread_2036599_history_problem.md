---
title: "history problem"
date: 2012-08-02
forum: Server Platforms
---

### Post by nikibg on 2012-08-02
When i type ```
history
``` its show me from 900 to 1500 command.I wanna see one earlier command .
How can see all command history

---

### Post by Cheesemill on 2012-08-02
The history command only stores a certain number of entries.
What is the output of:
```
grep HIST ~/.bashrc
```

---

### Post by nikibg on 2012-08-02
Histsize=1000
histfilesize=2000

---

### Post by Cheesemill on 2012-08-02
You should still have the commands stored then.

How are you accessing the terminal on the server? Are you using the server directly, are you accessing it through SSH or do you have a GUI installed?

---

### Post by LHammonds on 2012-08-02
I am running Ubuntu Server 12.04 LTS (64-bit) and I also have the default values as noted above.

When I run the following commands:
```

history > /tmp/history.txt
vi /tmp/history.txt

```It contains exactly 1000 lines which are numbered beginning with 93 and ending with 1092

LHammonds

---

### Post by Cheesemill on 2012-08-02
> **LHammonds said:**
> I am running Ubuntu Server 12.04 LTS (64-bit) and I also have the default values as noted above.

When I run the following commands:
```

history > /tmp/history.txt
vi /tmp/history.txt

```It contains exactly 1000 lines which are numbered beginning with 93 and ending with 1092

LHammonds

I'm thinking the problem might not be with the history, the OP might just be reaching the scrollback buffer limit of the terminal emulator (the default is 512 lines using gnome-terminal).

---

### Post by LHammonds on 2012-08-02
> **Cheesemill said:**
> I'm thinking the problem might not be with the history, the OP might just be reaching the scrollback buffer limit of the terminal emulator (the default is 512 lines using gnome-terminal).Which is why I mentioned the pipe redirection method.  Without knowing his terminal app, there is no way (for us) to know for sure...but running those two commands will let him see everything...for sure. ;)

LHammonds

---


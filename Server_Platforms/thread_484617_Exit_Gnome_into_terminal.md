---
title: "Exit Gnome into terminal"
date: 2007-06-26
forum: Server Platforms
---

### Post by PopcornEaterMan on 2007-06-26
Is there a way to exit gnome and enter the terminal?  I've downloaded Ubuntu Desktop, but I've turned on apache and I would like to run it as a server (without the GUI)

---

### Post by avik on 2007-06-26
Press Control-Alt-F1 to get to a terminal, log in, then type:

```
sudo /etc/init.d/gdm stop
```

---


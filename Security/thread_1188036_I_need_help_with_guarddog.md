---
title: "I need help with guarddog"
date: 2009-06-15
forum: Security
---

### Post by NIHrebel on 2009-06-15
When I open guard dog firewall I get a message that says something to the effect that no changes will take effect because guard dog needs administrative privileges. Any ideas? thanks

---

### Post by Ginsly on 2009-06-15
in your terminal
```
sudo guarddog
```

---

### Post by The Cog on 2009-06-15
I think it should be either **gksu guarddog** or **kdesu guarddog** depending on whether you are using gnome or KDE. Just using sudo runs the risk of leaving unwanted files owned by root in your home directory.

---

### Post by Agent ME on 2009-06-16
> **The Cog said:**
> I think it should be either **gksu guarddog** or **kdesu guarddog** depending on whether you are using gnome or KDE. Just using sudo runs the risk of leaving unwanted files owned by root in your home directory.
sudo and gksudo are identical, except the first one can only be launched from a terminal and the second one is graphical. You can use either one in this case.

---

### Post by Rubicon_82 on 2009-06-16
> **Agent ME said:**
> sudo and gksudo are identical, except the first one can only be launched from a terminal and the second one is graphical. You can use either one in this case.


You should only use *sudo* to grant root privileges to applications without GUIs.  Runing GUI applications with *sudo*, instead of *gksu*/ *kdesudo* can result in that application's configuration files getting mucked up.  With sudo, the config files e.g. '/home/user/.apprc' will often end up *chown*ed to root.  When that application is then rerun as a regular user, those same configuration files can no longer be changed.  Using *gksu*/* kdesudo* will prevent this.

It *is* possible to launch a GUI application from the terminal, so
```

gksu guarddog

```will work.

---


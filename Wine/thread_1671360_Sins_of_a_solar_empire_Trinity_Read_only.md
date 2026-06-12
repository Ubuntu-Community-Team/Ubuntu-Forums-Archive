---
title: "Sins of a solar empire Trinity Read only"
date: 2011-01-19
forum: Wine
---

### Post by su-37 on 2011-01-19
Hey, ive seen this game running on Linux mint via wine 1.2 i think and when i try to change the permissions on the executable and install it says its a read only. I tried to find it in Play on linux but no luck. Any ideas on how to change it?

---

### Post by prshah on 2011-01-20
> **su-37 said:**
> when i try to change the permissions on the executable and install it says its a read only.

When you launch programs using the GUI, the default program (called cautious-launcher) checks if the file has the executable bit set. If the exec-bit is not set, it will not allow to "run" the file. In this case, since the executable is on an CD/DVD, you will not be able to give it execute permissions, so open a terminal and launch the program directly. Open a terminal (Applications-Accessories-Terminal) and give the commands
```

cd /media/cdrom0 # replace as suitable
wine setup.exe # watch out for cAsE !

```

---

### Post by Perfect Storm on 2011-01-20
Linux Mint forum: [http://forums.linuxmint.com/](http://forums.linuxmint.com/)

Thread closed.

---


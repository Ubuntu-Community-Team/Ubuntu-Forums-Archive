---
title: "AntiX: Xorg runs under root"
date: 2024-08-15
forum: Ubuntu/Debian BASED
---

### Post by maketopsite on 2024-08-15
Clean install from [FONT=Courier New]antiX-23.1_386-full.iso[/FONT].
Default configuration, default Display manager. I've tries almost all Desktop Environments (installed by installer).

Is it please possible to run Xorg under user account ? (I've tried gdm3 but it's buggy)

---

### Post by Rubi1200 on 2024-08-18
What does the output show for this?
```
cat /etc/X11/Xwrapper.config
```

---

### Post by maketopsite on 2024-08-29
> **Rubi1200 said:**
> What does the output show for this?
```
cat /etc/X11/Xwrapper.config
```

```
$ cat /etc/X11/Xwrapper.config
cat: /etc/X11/Xwrapper.config: No such file or directory
maketopsite@maketopsite:~
$
```

---


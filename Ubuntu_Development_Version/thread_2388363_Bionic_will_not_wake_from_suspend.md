---
title: "Bionic will not wake from suspend"
date: 2018-04-01
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2018-04-01
I installed the beta ISO a few days ago. When the system suspends and wakes up there is just a black screen and a blinking underline at the top left.

No amount of waiting will do anything. The only thing I can do is press and hold the power button until it shuts down, wait a few minutes and then back on.

Is there a fix for this, or has anyone else had this problem?

---

### Post by Cavsfan on 2018-04-01
Found only the latest kernel will not wake.
```
cavsfan@cavsfan-le-beast:~$ uname -r
4.15.0-13-generic

```

Booted into the 4.15.0-12-generic kernel and it woke after suspend. [It had no internet access]("https://ubuntuforums.org/showthread.php?t=2386503") but, it woke like it should have.

---


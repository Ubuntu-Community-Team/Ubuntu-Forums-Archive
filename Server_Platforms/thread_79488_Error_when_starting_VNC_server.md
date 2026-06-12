---
title: "Error when starting VNC server"
date: 2005-10-20
forum: Server Platforms
---

### Post by zhorty on 2005-10-20
Hi.
I have downloaded the latest vnc server from real vnc, and when I'm doing:
./vncserver :1 -name zhorty -depth 16 -geometry 800x600
I get this error:
```
vncserver: error while loading shared libraries: libstdc++-.libc6.2-2.so.3: cannot open shared object file: No such file or directory
```

So where can I get this file? I tryed google and apt-get install libstdc++-.libc6.2-2.so.3, but apt-get is not finding the file.

And, yes, I am kind of new to linux.

Thanks :)

---

### Post by nverhaar on 2005-10-20
Try this...

apt-get install libstdc++6

---

### Post by zhorty on 2005-10-21
[QUOTE=nverhaar]Try this...

apt-get install libstdc++6[/QUOTE]
The package worked, but I still get the same error.

---

### Post by zhorty on 2005-10-23
Bump. :???:

---


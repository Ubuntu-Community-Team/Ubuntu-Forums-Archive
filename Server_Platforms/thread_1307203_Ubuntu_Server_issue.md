---
title: "Ubuntu Server issue"
date: 2009-10-30
forum: Server Platforms
---

### Post by sleepy-time-demon on 2009-10-30
I'm trying to set up my server to work many roles at the same time. I've currently got LXDE as my window manager, elinks for my web browser, webmin as my remote tool, and Sockso for my MP3 server interface. 

However, I seem to have a problem when I launch elinks from LXDE. It comes up with the error of:

```
xterm: Can't execvp -e: no such file or directory
```

yet when I open LXTerminal, and type 'elinks', it works fine.

Another question is, how can I set up a sh script to start up when my server turns on. Sockso is setup as a SH script, so I was hoping for some help there too please. Thanks.

---

### Post by sleepy-time-demon on 2009-10-31
Bump, any ideas?

---

### Post by knedlyk on 2011-03-15
> **sleepy-time-demon said:**
> Bump, any ideas?

The problem is in desktop files *.desktop, open them in editor and change Terminal=true into Terminal=false.

---


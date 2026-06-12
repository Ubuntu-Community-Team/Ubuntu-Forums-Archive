---
title: "unreadable terminal screen ubuntu server"
date: 2013-02-18
forum: Server Platforms
---

### Post by dantz on 2013-02-18
fresh install of ubuntu server only have access to the machine via ssh

check attachments to see what it looks like

my guess is that its something to do with the video modes or the non existant gfx chipset in there.

dell optiplex g150 128mb ram

---

### Post by tgalati4 on 2013-02-18
If you have an Intel graphics chip, it's possible that it is sharing RAM to run video.  If it's true that you are only running 128 MB, then there may not be enough RAM to run the video display.  Do you have a swap partition?

Post the output of:

```
free
```

Go into BIOS and set video RAM to a different value.

---

### Post by codemaniac on 2013-02-19
Moved to "Server Platforms".

---


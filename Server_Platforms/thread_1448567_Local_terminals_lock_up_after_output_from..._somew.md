---
title: "Local terminals lock up after output from... somewhere?"
date: 2010-04-06
forum: Server Platforms
---

### Post by mdittmer on 2010-04-06
I've noticed a curious behaviour on a new Ubuntu Server 9.10 installation. I get one of a few output messages at the current terminal, and after the output, the terminal is rendered useless. It won't respond to any keyboard input. The most common message is:

```
/dev/sda7: [some number] files, [some other number]/[yet another number] clusters
```

It seems like some process is writing urgent output (on stderr or similar perhaps?) but is somehow "staying in the foreground" after outputting its message. This can even happen if I'm running another program in the current terminal, like a text editor.

Any idea what might cause this?

---


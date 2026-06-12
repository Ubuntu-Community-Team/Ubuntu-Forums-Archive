---
title: "ntop - blank pages"
date: 2009-10-26
forum: Server Platforms
---

### Post by aba3k on 2009-10-26
Hi
Ntop is serving just blank pages. I tried reinstalling without success.

ntop[2220]: **WARNING** gzflush error -2(stream error)

---

### Post by druhboruch on 2009-10-27
Have you compiled it or installed binary?

---

### Post by aba3k on 2009-10-27
binary
the problem was the permissions of /tmp, i changed and it's all ok.
tnks

---


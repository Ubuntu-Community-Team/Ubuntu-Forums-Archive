---
title: "Add memory to server"
date: 2012-11-25
forum: Server Platforms
---

### Post by Jackjack770 on 2012-11-25
I've recently installed the latest ubuntu server onto an old computer and set it up as afield server and when I checked on another computer it said the space was like 369 megabytes which isn't very much so I tried to add more memory by plugging in a external memory drive had no luck. Any one know to add a external hard to the memory of the computer or at least assign all the files from other computers into the drive?

---

### Post by snowpine on 2012-11-25
Welcome to the forums!

Let's clarify some terminology before we answer your question: when you say "memory" do you mean RAM or hard drive space? Please copy & paste the output of the following terminal commands so we can understand the situation:

```
free -m
df -h
```

---


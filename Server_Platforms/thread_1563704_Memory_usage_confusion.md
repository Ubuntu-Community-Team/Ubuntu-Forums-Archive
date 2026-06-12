---
title: "Memory usage confusion"
date: 2010-08-29
forum: Server Platforms
---

### Post by onehitxzibit on 2010-08-29
I am kind of confused about my server's memory usage. Free -m shows 159MB used, but htop shows 45MB used. Which one should I trust (which is the correct)?

---

### Post by arrange on 2010-08-29
Can you please post the outputs of both commands in full (I mean the memory part)?

---

### Post by onehitxzibit on 2010-08-29
> **arrange said:**
> Can you please post the outputs of both commands in full (I mean the memory part)?
Here you go.

---

### Post by arrange on 2010-08-29
If you look at the second line of *free -m*, you will see, that there is no discrepancy: in the first line cache and buffers (which can be easily discarded) are added to the used memory total.

---

### Post by onehitxzibit on 2010-08-29
> **arrange said:**
> If you look at the second line of *free -m*, you will see, that there is no discrepancy: in the first line cache and buffers (which can be easily discarded) are added to the used memory total.

So 43MB is the actual current memory usage?

---

### Post by arrange on 2010-08-29
Well, as far as I know, calculating physical memory usage is never precise, but it will be roughly 43MB.

If you want more details about your memory usage, look at```
cat /proc/meminfo
```:D

---


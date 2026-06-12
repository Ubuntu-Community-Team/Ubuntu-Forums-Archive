---
title: "Memory Hog"
date: 2023-07-22
forum: Ubuntu Development Version
---

### Post by TenPlus1 on 2023-07-22
I installed Xubuntu 23.10 on a fresh system and was shocked to find it used 1.7gb of memory on a clean boot ?!

After tweaking startup applications I managed to get that down to 780mb which was still over twice what it was on 23.04.

Why is the newer release using so much memory ?  I use to recommend Xubuntu as a lightweight distro for new users.

---

### Post by VMC on 2023-07-22
Find the culprit:
```
top -o %MEM
```

---

### Post by TenPlus1 on 2023-07-24
[ATTACH=CONFIG]292505[/ATTACH]

---


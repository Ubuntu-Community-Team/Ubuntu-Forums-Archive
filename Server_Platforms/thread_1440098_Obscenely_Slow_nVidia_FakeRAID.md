---
title: "Obscenely Slow nVidia FakeRAID"
date: 2010-03-27
forum: Server Platforms
---

### Post by mewrei on 2010-03-27
I have two drives configured in RAID-1 over nVidia SATA FakeRAID for my home partition, and its obscenely slow.

I postmarked it and the results were not pretty.

Parameters:
set number 5000
set transactions 5000

FakeRAID1: 164 seconds of transactions (30 per second)
Single drive: 4 seconds of transactions (1250 per second)

I'm using JFS across the board (except for /boot).

Is there any way to improve performance/proc-load here or am I just SoL and need to figure out a different option?

---


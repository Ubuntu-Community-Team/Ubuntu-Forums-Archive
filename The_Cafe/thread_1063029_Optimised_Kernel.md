---
title: "Optimised Kernel"
date: 2009-02-07
forum: The Cafe
---

### Post by davbren on 2009-02-07
Hey all, I was wondering... what are the DISadvantages to having a low latency kernel like in Studio?

It occurred to me that if this exists then surely it would be in someway beneficial to everyone and thus should be included by default in the regular kernel. That is of course if the optimised kernel doesn't cause some sort of adverse effects.

---

### Post by davbren on 2009-03-01
any ideas?

---

### Post by mister_pink on 2009-03-01
I don't think optimised is the right word. I believe it just schedules tasks differently to the normal kernel, and I don't think that in everyday use it would necessarily be an advantage.

---

### Post by ssam on 2009-03-01
i think there is a compromise between overall throughput and low latency.

---

### Post by Bölvaður on 2009-03-01
servers have kernel that have longer times each process/thread has, because switching takes time, so it means they can do more calculations instead of constantly switching between processes/threads.

Then you have low latency kernels (I think this is how they are) when there is very frequent switching to make it look more respondent and looks like everything is done imminently. What you get for this constant switching is very long time occupied in just the act of switching between processes instead of doing any calculations.

Desktop users have more of a balanced setup.

---

### Post by davbren on 2009-03-02
I c, Thanx peeps!:guitar:

---

### Post by thisllub on 2009-03-02
VirtualBox doesn't work with the lowest latency setting.

---

